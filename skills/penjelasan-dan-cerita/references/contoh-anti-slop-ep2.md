# Contoh Terkerjakan — Lapisan Anti-Slop atas naskah asli Episode 002

Uji bukti dari penilaian internal penulis atas repo tulis (2026-11-18), direproduksi ringkas sebagai preseden terhitung skill ini. Sumber: NASKAH.md Episode 002 asli (152 kata, 9 beat; fakta F1–F7 tidak diubah suntingan mana pun). Kesimpulan besarnya: **rasa AI pada naskah kita bersifat ritmis-struktural, bukan leksikal** — kosakatanya bersih; yang mekanis adalah denyutnya.

## Temuan atas naskah asli (dengan contoh kalimat)

1. **Em dash sebagai konektor serbaguna — 8 dash dalam 152 kata, di 6 dari 9 beat** (humanizer §8; stop-slop; oh-story: blocking). Contoh: Beat 2 "Ten tons of force — from plain air — is holding it shut." · Beat 7 "Half a pound — a breath — is fifteen hundred pounds."
2. **Pembuka "So" — 2 beat** (Beat 6, Beat 9; Beat 9 adalah echo loop yang disengaja → ditandai, masuk pertimbangan daftar putih).
3. **False agency** — Beat 7: "Physics locks the door long before cruise." ("Physics" adalah nama bidang, bukan pelaku.)
4. **Pasif tanpa pelaku** — Beat 4: "Up here, the cabin is pumped full of air."
5. **Kontras panggung separuh-negatif** — Beat 5: "Eight pounds sounds like nothing. But the door has three thousand square inches."
6. **Kepadatan fragmen dramatis** — hampir setiap beat berisi fragmen tumbuk ("Go ahead. Try." / "You can't." / "It doesn't even take eight."). Alatnya sah; keteraturan denyutnya yang menjadi tell.
7. **Menghindari "is"** — Beat 3: "That door works like a plug…"
8. **Peredam bertumpuk (lemah-sendiri)** — Beat 8: "The locks help, sure — but they're backup."

**Yang TIDAK ditemukan (dicatat agar preseden ini jujur):** daftar kata AI humanizer §12 = nol; tidak ada inflated significance; tidak ada sisa chatbot; tidak ada triad leksikal paksa (rangkaian beat 4–5–6 adalah isi persamaan, bukan triad gaya).

## Skor stop-slop naskah asli

Directness 7 · Rhythm 4 (denyut tumbuk hampir seragam antar-beat) · Trust 6 · Authenticity 4 (dash + false agency + rekayasa quotable) · Density 8 = **29/50 < 35 → revisi** menurut ambang stop-slop — konvergen dengan vonis pemilik channel dari arah yang sepenuhnya berbeda. (Catatan laporan: penilai lain bisa bergeser ±3 titik; kesimpulan ambangnya kokoh karena dua dimensi terendah berpijak pada temuan terhitung.)

## Contoh suntingan (fakta & maksud dipertahankan)

| Beat | Sebelum | Sesudah | Pola yang diperbaiki |
|---|---|---|---|
| 2 | "You can't. Ten tons of force — from plain air — is holding it shut." | "You can't. Plain air holds it shut with ten tons of force." | dash ganda dibuang, pernyataan langsung |
| 3 | "That door works like a plug, wedged into its frame from the inside — with the whole sky leaning on it." | "The door is a plug, wedged into its frame from the inside, and the whole sky leans on it." | "works like"→"is"; dash→koma |
| 4 | "Up here, the cabin is pumped full of air. Outside, there's barely any. The gap: eight pounds on every square inch." | "Up here, the airplane pumps its cabin full of air. Outside, almost none is left. The gap: eight pounds on every square inch." | pelaku dinamai, pasif hilang |
| 5 | "Eight pounds sounds like nothing. But the door has three thousand square inches." | "Eight pounds on one square inch. The door has three thousand of them." | kontras panggung → tangga angka |
| 6 | "So the air pushes with over ten tons — and you'd have to pull all of it toward you first." | "The push totals over ten tons, and you must pull all of it toward you first." | pembuka "So" + dash dibuang |
| 7 | "It doesn't even take eight. Half a pound — a breath — is fifteen hundred pounds. Physics locks the door long before cruise." | "Even half a pound is enough: across the door, that is fifteen hundred pounds. Pressure locks the door long before cruise." | false agency dibuang; dash dibuang |
| 8 | "The locks help, sure — but they're backup. Down low, the pressure fades to nothing. In 2023, a passenger pulled an emergency exit open at seven hundred feet." | "The mechanical locks are only the backup. Down low, the pressure gap shrinks to nothing. In 2023, a passenger pulled an emergency exit open at seven hundred feet." | peredam + dash dibuang; klaim kejujuran utuh |

Beat 1 dan 9 sengaja TIDAK ditulis ulang di uji ini: keduanya perangkat genre yang disengaja (tantangan hook + echo loop) — preseden langsung untuk daftar putih: pola yang dipilih sadar boleh dipertahankan; yang diperbaiki adalah kepadatan pola di beat-beat isi.

## Bukti mekanis

Pemeriksa deterministik repo sumber (oh-story), dijalankan penulis atas teks narasi apa adanya saat penilaian awal (2026-11-18), mencatat:

```
8 temuan [blocking] em-dash (baris 1, 2×2, 3, 6, 7×2, 8), exit code 1
```

Skrip pemeriksa repo sumber itu TIDAK disertakan di repo ini. Pemeriksaan yang sama di repo ini dijalankan dengan resep `python3` inline di [pemeriksa-mekanis.md](pemeriksa-mekanis.md): simpan teks narasi ke `narasi.txt`, jalankan resepnya, dan nilai hitungan em-dash per beat + total terhadap ambang di berkas itu — hasil hitungnya setara untuk cek em-dash dan kepadatan fragmen.

Dua arah buktinya: temuan dash bukan selera penilai (terkonfirmasi mekanis oleh perkakas repo ketiga), dan yang diimpor dari oh-story adalah mekanisme pemeriksanya — bukan daftar katanya (lihat pemeriksa-mekanis.md).

## Batas contoh ini

Suntingan di atas memperbaiki rasa mekanis, bukan seluruh vonis pemilik channel atas Episode 002: kebingungannya juga soal urutan informasi (lapis logika-cerita) dan visual — di luar jangkauan daftar periksa permukaan. Lapisan anti-slop adalah syarat perlu, bukan syarat cukup; gerbang tetap diputuskan lembar janji + reader-sim.
