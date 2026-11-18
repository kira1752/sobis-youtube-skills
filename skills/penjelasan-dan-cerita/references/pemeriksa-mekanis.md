# Pemeriksa Mekanis Anti-Slop — arsitektur dua tingkat

Arsitektur diadaptasi sebagai KONSEP dari pemeriksa deterministik story-deslop di oh-story-claudecode (worldwonderer, MIT): temuan dua tingkat (**blocking** vs **advisory**) + daftar putih untuk pilihan penulis yang disengaja + pindai-ulang maksimal 3 putaran + aturan bahwa nol temuan skrip tidak menggantikan pembacaan manusia. Bukti konsepnya: pemeriksa repo itu, dijalankan atas narasi Episode 002, menembak tepat 8 em-dash sebagai blocking (exit code 1) — aturan titikunya lintas-bahasa walau katalog leksikonnya Mandarin dan tidak dipakai di sini. Daftar pola pemeriksa divisi diisi dari [daftar-pola-anti-slop.md](daftar-pola-anti-slop.md), bukan dari katalog repo mana pun.

## Dua tingkat temuan

- **BLOCKING** — naskah tidak boleh naik ke reader-sim sebelum nol, atau tercatat di daftar putih:
  1. Kepadatan em-dash melewati ambang (cek 1 di bawah).
  2. Penutup bertipe pertanyaan baru — dideteksi dari anotasi beatmap (kolom Hook keluar beat terakhir = `question` yang ID-nya tidak ada di lembar janji sebagai terbayar), bukan dari teks mentah.
- **ADVISORY** — dibaca penilai, diputuskan satu per satu, tidak otomatis menggagalkan:
  1. Kepadatan fragmen per beat (cek 2).
  2. Pembuka kalimat yang sama ≥3 kali; pembuka "So"/Wh- berulang di luar daftar putih.
  3. Em-dash di bawah ambang blocking (tetap dicatat jumlahnya untuk skor Authenticity).

## Cek 1 — Em-dash (per beat + total)

- Hitung em-dash (—, termasuk en-dash – yang dipakai sebagai konektor) per beat dan total naskah.
- **Ambang dinyatakan sebagai fungsi panjang naskah** (kalibrasi dari preseden Ep 002 penulis: 8 dash / 152 kata = blocking):
  - Panjang acuan kalibrasi: **150 kata**. Pada panjang acuan: blocking bila total >3, advisory bila total 1–3.
  - Untuk panjang lain, skala linear: ambang blocking total = **ceil(3 × jumlah kata ÷ 150)**, minimum 3. (Contoh: naskah 300 kata → blocking bila total >6; naskah 450 kata → >9.) Ambang advisory = 1 sampai ambang blocking.
  - Per beat tidak diskalakan: **>1 dash dalam satu beat = blocking** pada panjang berapa pun, di luar daftar putih.
- Dash yang tercatat di daftar putih (jeda delivery yang disengaja, dinamai beat-nya) dikecualikan dari hitungan.

## Cek 2 — Kepadatan fragmen per beat

- Fragmen = kalimat ≤4 kata yang bukan perintah hook yang disengaja (daftar putih).
- Untuk hitungan ini, "kalimat" mencakup klausa yang digabung titik koma: resep di bawah memecah teks juga pada `;`, jadi klausa ≤4 kata hasil belahan titik koma dihitung fragmen sama seperti kalimat bertanda titik. Fragmen yang disembunyikan di balik titik koma tidak lolos dari hitungan (lihat catatan titik koma di Aturan main).
- Hitung rasio fragmen per beat (fragmen ÷ kalimat beat itu).
- **Ambang (rasio — berlaku pada panjang berapa pun, tidak perlu diskalakan):**
  - Advisory bila satu beat mana pun rasionya >50%.
  - Blocking bila ≥75% beat memuat fragmen penutup satu-baris DAN rasio fragmen rata-rata >40% — pola ritme-berbasis-aturan ala Ep 002 asli (hampir setiap beat berisi fragmen tumbuk dengan denyut sama).

## Resep perintah (jalan dari shell bersih; teks narasi polos satu beat per blok, blok dipisah baris kosong)

Prasyarat: `python3` tersedia di PATH (resep ini tanpa dependensi tambahan — prasyarat paling ringan di pipa ini).

Simpan teks narasi saja (tanpa arahan gambar) ke `narasi.txt`, lalu:

```bash
python3 - <<'EOF'
import re, sys
teks = open('narasi.txt', encoding='utf-8').read()
beats = [b.strip() for b in re.split(r'\n\s*\n', teks) if b.strip()]
total_dash = 0
for i, b in enumerate(beats, 1):
    dash = b.count('—') + b.count('–')
    total_dash += dash
    kalimat = [k for k in re.split(r'[.!?;]+', b) if k.strip()]
    frag = sum(1 for k in kalimat if len(k.split()) <= 4)
    rasio = (frag / len(kalimat)) if kalimat else 0
    print(f"beat {i}: dash={dash} kalimat={len(kalimat)} fragmen={frag} rasio={rasio:.0%}")
print(f"TOTAL dash={total_dash} dari {sum(len(b.split()) for b in beats)} kata")
EOF
```

Nilai keluarannya terhadap ambang di atas dan terhadap daftar putih episode. Perintah ini sengaja resep, bukan perkakas terpasang: ia tidak membaca daftar putih dan tidak memberi vonis — penilai yang memberi vonis.

## Aturan main

- **Pindai-ulang maksimal 3 putaran** sesudah perbaikan. Sengketa yang tersisa diputuskan penilai gerbang dari teks, bukan dari putaran keempat.
- **Nol temuan ≠ naskah bersih.** Pemeriksa hanya menghitung yang bisa dihitung (dash, fragmen, pembuka). Rasa AI pada naskah Ep 002 bersifat ritmis-struktural; lapis kalimat dan logika-cerita tetap dinilai manusia/agen lewat reader-sim dan diagnosis tiga lapis.
- **Titik koma (perbaikan 2026-11-18, dari uji clean-room):** pemecah kalimat pada resep kini memuat `;`. Sebelumnya klausa yang digabung titik koma tidak pernah terpecah, sehingga deteksi fragmen buta terhadapnya. Uji sebelum/sesudah atas dua kasus: (i) beat sah "Cahayanya sampai seketika; bunyinya merangkak tiga detik tiap kilometer." — sebelum: 1 kalimat, 0 fragmen; sesudah: 2 klausa, 1 fragmen, rasio 50% (tidak melewati ambang advisory >50% — tidak ada temuan baru pada naskah sah itu); (ii) fragmen bertumpuk yang disembunyikan titik koma, "Dia menatap langit; tidak ada jawaban; hanya diam; selamanya membisu." — sebelum: 1 kalimat, rasio 0% (buta total); sesudah: 4 klausa, 4 fragmen, rasio 100% (tertangkap). Konsekuensi yang disadari: klausa titik koma yang pendek kini bisa menaikkan rasio fragmen sebuah beat — itu memang maksud perbaikannya, dan temuan advisory tetap diputuskan penilai satu per satu.
- Keluaran pemeriksa (jumlah per beat + total) disimpan sebagai bukti di folder episode, sejajar bukti gerbang lain, dan menjadi jangkar skor Rhythm/Authenticity di blok skor stop-slop.
