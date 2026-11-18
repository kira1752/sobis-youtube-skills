# Protokol Reader-Sim + Templat Laporan

Reader-sim = membaca/mendengar naskah SEBAGAI pendengar pertama kali dan melaporkan pengalaman yang DIRASAKAN momen demi momen — bukan kritik kerajinan. Diadaptasi dari `reader-sim` di creative-writing-skills (haowjy, Apache-2.0), dipindahkan dari membaca ke mendengar/menonton. Struktur diagnosis tiga lapisnya diadaptasi dari story-deslop di oh-story-claudecode (worldwonderer, MIT): 表达 (ekspresi) → 用笔 (pemakaian pena) → 故事 (logika cerita), diterjemahkan menjadi ekspresi / kalimat / logika-cerita.

## Pagar peran (tidak bisa ditawar)

- Simulator adalah agen **terpisah dari penulis naskah**. Penulis yang mensimulasikan naskahnya sendiri menghasilkan laporan yang tahu semua jawaban — persis kegagalan yang membuat Episode 002 lolos.
- Simulator menerima: naskah, persona, dan batas pengetahuan. Ia TIDAK menerima lembar fakta, lembar janji, catatan penulis, atau vonis gerbang sebelumnya. Ia menilai dari dalam pengalaman pertama, bukan dari berkas produksi.
- Klaim laporan wajib berjangkar ke teks: nomor beat + kutipan pendek kalimat yang menimbulkan pengalaman itu.

## Persona baku (sesuaikan per episode, nyatakan selalu di laporan)

- **Mode PENJELAS:** penonton awam sesuai platform proyekmu (persona adalah parameter proyek: platform, perangkat, dan konteks menonton dinyatakan eksplisit di laporan); tidak punya latar domain topik (fisika, mekanik, biologi — sesuai topik); menonton sekali jalan, tidak bisa memutar ulang; perhatian penuh hanya dijamin pada detik-detik pembuka (kalibrasi penulis pada format pendek: ±5 detik pertama — untuk format lain, nyatakan jendela perhatian personamu sendiri).
- **Mode CERITA:** penonton yang baru pertama kali melihat tokoh ini; tidak tahu episode sebelumnya; tahu konvensi genre seperlunya (komedi, horor, dst. sesuai episode).

## Prosedur

1. Nyatakan persona + batas pengetahuan di kepala laporan sebelum membaca.
2. Baca/dengar naskah dari awal sampai akhir TANPA berhenti, sambil mencatat pengalaman momen-ke-momen pada tiga kanal:
   - **Pertanyaan yang dipegang:** pertanyaan apa yang sedang hidup di kepala saat ini; kapan ia muncul, berubah, terjawab, atau berhenti dipedulikan.
   - **Beban paham:** istilah/angka/klaim yang harus ditahan sebelum terbayar; di mana tumpukannya terasa berat.
   - **Perhatian:** di mana menanjak, di mana melayang, di mana ingin berhenti.
   (Mode CERITA tambah: momen tertawa/tersentuh yang benar-benar tiba vs yang hanya dimaksudkan.)
3. Di akhir, jawab uji sekali-dengar dari ingatan saja (tanpa membaca ulang): Mode PENJELAS — "video ini bilang apa dan kenapa" dalam 1–2 kalimat; Mode CERITA — taruhan tokoh + apa hasil akhirnya, dalam 1–2 kalimat.
4. Sebutkan **pertanyaan terakhir yang hidup di kepala** saat naskah berakhir, persis seperti dirasakan. Ini butir paling menentukan di seluruh laporan.
5. Susun diagnosis tiga lapis (templat di bawah) dan blok skor. Simulator melaporkan pengalaman; penilai gerbang yang memutuskan vonis dari laporan ini + lembar janji.

## Yang TIDAK dilakukan simulator

- Tidak memberi saran perbaikan kerajinan ("sebaiknya beat 4 diganti…"). Itu pekerjaan penilai/penulis sesudahnya.
- Tidak menilai kebenaran fakta. Itu wilayah lembar fakta.
- Tidak berpura-pura menjadi "penonton umum". Selalu persona yang dinyatakan.

## Templat laporan

```markdown
# LAPORAN READER-SIM — <judul episode>

- Simulator: <agen/sesi, terpisah dari penulis: ya>
- Persona: <siapa, pengetahuan awal, toleransi ambiguitas>
- Batas pengetahuan: <apa yang persona ini TIDAK tahu>
- Media sim: teks dibaca sekali jalan / VO didengar sekali (pilih satu, sebutkan)

## Pengalaman keseluruhan (2–3 kalimat, dirasakan — bukan dinilai)

## Momen-ke-momen

| Beat | Pertanyaan yang dipegang | Beban paham | Perhatian | Kutipan jangkar |
|---|---|---|---|---|
| 1 |  |  |  |  |
| … |  |  |  |  |

## Uji sekali-dengar (dari ingatan, tanpa membaca ulang)

- Ulangi isi video dalam 1–2 kalimat: "…"
- Pertanyaan terakhir yang hidup di kepala saat berakhir: "…"
- Pertanyaan itu terbayar / yatim: <terbayar oleh beat … / YATIM>

## Diagnosis tiga lapis

### Lapis 1 — Ekspresi (permukaan)
<dash & fragmen yang terasa, pola anti-slop yang terdengar, ritme kalimat yang mekanis — sebagai pengalaman, bukan daftar temuan>

### Lapis 2 — Kalimat (pemakaian)
<fokus per beat, tebal-tipis uraian: bagian yang terasa dikuliahkan vs yang terasa hidup; beat yang tidak mengubah apa pun>

### Lapis 3 — Logika-cerita (kausalitas + urutan pengungkapan)
<apakah tiap beat disebabkan/dikomplikasi beat sebelumnya; apakah urutan siapa-tahu-apa membuat penonton memegang pertanyaan yang benar; di mana janji dibayar terlalu dini atau ditanam terlalu akhir>

## Blok skor anti-slop (stop-slop; diisi penilai gerbang dari laporan ini + naskah)

| Dimensi | Skor /10 | Bukti satu baris |
|---|---|---|
| Directness |  |  |
| Rhythm |  |  |
| Trust |  |  |
| Authenticity |  |  |
| Density |  |  |
| **Total** | **/50** | <35 = REVISI |

## Titik bingung fatal (kosongkan bila tidak ada)

- <beat + kutipan + kenapa fatal: pertanyaan yatim / beban tak terbayar / isi tak bisa diulang>
```

## Membaca laporan sebagai penilai gerbang

- **Titik bingung fatal** = salah satu dari: (a) pertanyaan terakhir di kepala penonton yatim; (b) beban paham menumpuk ≥2 besaran/istilah abstrak yang belum terbayar dalam satu rentang beat; (c) uji sekali-dengar gagal mengulang isi. Satu saja cukup untuk REVISI.
- Lapis 3 yang buruk tidak bisa ditebus lapis 1 yang bersih. Naskah asli Episode 002 adalah preseden: kosakata bersih, urutan informasi yang membingungkan.
- Skor Rhythm dan Authenticity yang rendah biasanya berjangkar ke temuan terhitung (kepadatan dash/fragmen) — cocokkan dengan keluaran pemeriksa mekanis sebelum memperdebatkannya.
