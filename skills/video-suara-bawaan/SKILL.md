# Video & Suara Bawaan Muse

Skill ini mengemas kemampuan generatif BAWAAN Muse sendiri — video generatif dengan dialog native dan TTS bawaan — untuk produksi Divisi YouTube, lengkap dengan langkah pencegahan AI slop sebelum generate dan langkah audit ketat sebelum hasil apa pun dikirim ke Indra.

Skill ini lahir 18 November 2026 dari pembuktian langsung: video buatan Muse adik pemilik channel memakai suara Indonesia yang terdengar riil tanpa setup apa pun, sementara divisi kami berminggu-minggu muter menguji engine eksternal (tiga finalis suara Indonesia ditolak semua karena terdengar seperti AI). Pelajarannya dipaku di sini supaya tidak muter lagi: **inventaris kemampuan bawaan Muse lebih dulu, engine eksternal hanya bila jalur bawaan terbukti mentok di gerbang.**

## Dua jalur bawaan dan kapan memakainya

- **Jalur A — video generatif dengan dialog native.** Kekuatannya nada: dialog lahir satu paket dengan gambar dari model video, berintonasi seperti orang beneran berakting, bukan dibacakan. Pakai untuk beat dialog/akting berbahasa Indonesia. Bukti 18 Nov: klip uji 10 detik 720x1280, dialog Indonesia satu penutur; vonis pemilik: "nyata banget", "organic".
- **Jalur B — TTS bawaan untuk narasi.** Pakai untuk voiceover narasi. Bukti 18 Nov: contoh narasi Indonesia dinilai pemilik "mulai tidak keliatan AI", tetapi nadanya lebih datar daripada dialog native Jalur A. Untuk dialog, Jalur A menang; untuk narasi, Jalur B kandidat yang wajib lolos audisi gerbang seperti kandidat suara lain.

Kedua jalur TIDAK mengubah kunci suara maskot channel Inggris (Kokoro `am_michael` @1,05) dan tidak menggantikan pipa divisi: naskah tetap lewat skill `penjelasan-dan-cerita` (Gerbang 1), kemasan tetap lewat skill `kemasan-video`, dan upload tetap hanya sesudah Gerbang 2 LOLOS.

## Jalur A — hasilkan video dialog

- Tulis prompt sebagai satu adegan: satu penutur, satu lokasi, satu emosi yang ditulis sebagai perbuatan terlihat (menahan tangis sambil memegang paket), bukan kata sifat (sedih, premium).
- Tulis dialog Bahasa Indonesia PERSIS di dalam prompt, dalam tanda kutip, maksimal ±20 kata per klip. Kalimat pendek menolong kejelasan pengucapan dan sinkronisasi bibir.
- Minta eksplisit: berbicara alami bahasa Indonesia, intonasi percakapan nyata, bukan narasi datar.
- Satu panggilan `media.generate_video` per klip; batas alat 6 video per pesan. Durasi bawaan teramati ±10 detik, vertikal 720x1280 24fps dengan audio AAC 24kHz mono.
- Catat `snapshot_id` hasil; perbaikan klip yang sama dilanjutkan dari snapshot itu, bukan generate ulang dari nol.

## Jalur B — hasilkan narasi TTS

- Pakai perintah teruji dari shell bersih (tanpa koneksi akun apa pun):

  `/opt/hatch/bin/tts speak --output <berkas.mp3> --language id --voice avocado_v2:MAI_03 --text-stdin`

  Teks diteruskan lewat stdin, bukan argumen shell. Suara bawaan lain yang sah: `avocado_v2:MAI_01` (Aria). Ganti bahasa lewat `--language` (Inggris `en`).
- Tulis teks seperti orang bicara: angka dan singkatan ditulis sebagai kata yang diucapkan, tanpa markdown, tanpa penanda kutipan.
- Periksa hasil: perintah mengembalikan `ok`, `path`, dan `bytes` (contoh terukur 18 Nov: 114.277 byte untuk 3 kalimat). Berkas gagal atau terpotong tidak pernah disampaikan sebagai hasil jadi.
- Untuk teks panjang atau banyak penutur, pakai `tts synthesize-script` dengan `--speaker Nama=VOICE_ID` per penutur.

## Pencegahan AI slop — wajib SEBELUM generate

Slop dicegah di prompt, bukan ditambal sesudahnya. Pada uji 18 Nov wajah dan ekspresi lolos semua frame, tetapi teks di kardus ekspedisi garbled semua ("FRAGIL", "J&T EXPRES", tulisan kecil label dan kalender ngawur) — satu-satunya kegagalan material klip itu, dan sumbernya prompt yang membiarkan teks masuk frame.

- **Larang teks di dalam frame.** Jangan meminta atau membiarkan: kardus/paket berlabel, signage, logo merek asli, kalender, papan tulis, layar HP/komputer berteks, koran, kemasan produk. Bila adegan rawan teks (gudang, toko, kantor), arahkan latar polos atau teks dibuat tidak terbaca secara alami (jauh, blur, terlipat) — atau ganti adegannya.
- **Teks yang harus terbaca = lapis deterministik.** Judul, caption, label, diagram ditambahkan di pasca-produksi lewat skill `kemasan-video`, tidak pernah diminta dari model video.
- **Satu penutur, satu adegan, durasi pendek.** Banyak wajah dan banyak adegan per klip menaikkan risiko wajah bergeser dan topologi meleleh.
- **Hindari tangan sebagai subjek hero** memegang benda kecil atau berteks; tangan wajar sebagai bagian adegan, bukan pusat bidikan.
- **Hindari cermin, pantulan berteks, dan kerumunan wajah.** Satu-dua wajah per klip.
- **Pra-terdaftar aturan lulus** sebelum generate (pola Mandat Pengecekan Ketat PIPA-PRODUKSI): tulis dulu butir yang akan dinilai di audit bawah, baru hasilkan klip termurah untuk beat paling berisiko.

## Audit ketat — wajib SEBELUM hasil dikirim ke Indra

Aturan pemilik (18 Nov 2026, 20:43): hasil generate AI tidak pernah dikirim mentah. Audit dulu, kirim bersama vonisnya.

1. **Ekstrak bukti.** `ffprobe` untuk durasi, resolusi, dan keberadaan stream audio; `ffmpeg -vf fps=1` untuk frame per detik ke folder bukti di samping klip.
2. **Nilai visual per frame bernama** (pola Gerbang 2B PIPA-PRODUKSI, sebut nama berkas frame yang diperiksa): konsistensi wajah penutur antar-frame; tangan wajar; dan **uji teks — setiap teks yang terlihat dibaca satu-satu; satu teks garbled = temuan material = klip GAGAL untuk produksi** (sah hanya sebagai bukti kemampuan). Tambahkan uji mustahil W-3 (objek menembus, elemen melayang, kontradiksi skala) dan uji gerak W-4 (tonton 1x dan 0,25x; subjek meleleh/berganti bentuk = GAGAL).
3. **Nilai audio.** Pastikan stream audio benar-benar ada dan dialognya sesuai teks yang diminta (transkrip bila alat transkripsi tersedia; bila tidak, nyatakan belum terverifikasi mesin). Nada akhir tetap vonis telinga pemilik, di atas semua gerbang internal.
4. **Penilai bukan produsen (P-1).** Untuk produksi divisi, audit dijalankan worker penilai yang berbeda dari yang men-generate, memakai Gerbang 2B penuh. Pra-audit oleh produsen sendiri hanya sah untuk demo kemampuan dan wajib dilaporkan sebagai pra-audit, bukan vonis gerbang.
5. **Format vonis.** Tulis per butir: LOLOS / REVISI / TOLAK, dengan bukti frame bernama. Cacat yang diketahui produsen tidak boleh terbawa dalam vonis LOLOS (P-2). Klip REVISI digenerate ulang dengan prompt yang diperbaiki pada sumber slopnya (mis. teks dikeluarkan dari frame), bukan dipoles.

## Pagar

- Skill ini adalah mesin + disiplinnya; ia tidak melonggarkan satu pun gerbang PIPA-PRODUKSI. Urutan divisi tetap: Gerbang 1 naskah → produksi → Gerbang 2/2B → upload oleh Manager.
- Jangan memakai video generatif untuk beat yang menuntut presisi: diagram anatomi, teks informatif, angka. Itu wilayah lapis deterministik kita.
- Jangan mengklaim hasil generate "sudah dicek" hanya dari menonton sekali jalan; klaim cek hanya sah dari audit frame bernama di atas.
- Bila jalur bawaan gagal gerbang untuk kebutuhan tertentu, catat kegagalannya sebagai bukti, baru buka uji engine eksternal — dengan bukti itu di tangan, bukan dari ingatan.
