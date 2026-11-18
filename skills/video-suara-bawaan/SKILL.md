# Generate Video Bawaan Muse — Skill Utama Divisi YouTube

Skill ini adalah **SKILL UTAMA divisi YouTube untuk generate video**: intinya kemampuan Muse menghasilkan video LANGSUNG memakai model generatif bawaannya sendiri — klip dengan dialog native yang lahir satu paket dengan gambar, berintonasi seperti orang beneran berakting, bukan dibacakan. TTS bawaan Muse adalah jalur pendukung di belakangnya, bukan inti. Skill ini lengkap dengan pola produksi multi-klip, langkah pencegahan AI slop sebelum generate, dan langkah audit ketat sebelum hasil apa pun dikirim ke Indra.

Keputusan pemilik (Indra, 18 November 2026): skill ini jadi skill utama divisi untuk generate video; **engine video/suara eksternal turun menjadi cadangan** — hanya dibuka bila jalur bawaan terbukti mentok di gerbang, dengan bukti di tangan, bukan dari ingatan.

Skill ini lahir 18 November 2026 dari pembuktian langsung: video buatan Muse adik pemilik channel memakai suara Indonesia yang terdengar riil tanpa setup apa pun, sementara divisi kami berminggu-minggu muter menguji engine eksternal (tiga finalis suara Indonesia ditolak semua karena terdengar seperti AI). Pelajarannya dipaku di sini supaya tidak muter lagi: **inventaris kemampuan bawaan Muse lebih dulu, engine eksternal hanya bila jalur bawaan terbukti mentok di gerbang.**

## Posisi tata kelola — baca sebelum memakai

- Skill ini adalah **mesin generate di dalam PIPA-PRODUKSI divisi, BUKAN izin produksi mandiri.** Ia tidak melonggarkan satu pun gerbang pipa: naskah tetap lewat skill `penjelasan-dan-cerita` (Gerbang 1), kemasan dan penggabungan klip tetap lewat skill `kemasan-video`, penilaian produksi tetap Gerbang 2/2B oleh penilai yang bukan produsennya, dan upload tetap hanya sesudah Gerbang 2 LOLOS dan oleh Manager.
- **Keputusan tertulis Manager 2026-11-18 (atas perintah Indra): jalur bawaan = mesin utama Rute 1, engine eksternal = cadangan.** Keputusan itulah yang memberi skill ini tempatnya di dalam pipa; skill ini sendiri tidak memberi wewenang apa pun di luar keputusan itu.
- **Dialog Bahasa Indonesia native adalah trek audio klip itu sendiri** dalam model divisi satu-unggahan-multi-trek: satu unggahan membawa banyak trek bahasa, dan dua unggahan beda bahasa di satu channel dilarang permanen. Klip dialog ID dari skill ini mengisi trek ID pada unggahan yang sama — bukan video terpisah.
- **Jalur B (TTS bawaan) untuk tayang tunduk pada syarat lisensi suara pipa (Usulan 1):** suara yang tayang wajib dihasilkan engine yang tercatat komersial-aman di lembar kunci suara. Syarat itu dinyatakan di sini sebagai syarat — skill ini TIDAK memutuskan lisensi suara bawaan. Sampai tercatat di lembar kunci suara, hasil Jalur B berstatus kandidat yang wajib lolos audisi gerbang seperti kandidat suara lain.
- Kunci suara maskot channel Inggris (Kokoro `am_michael` @1,05) TIDAK berubah oleh skill ini.

## Jalur A — generate video langsung (INTI)

- Tulis prompt sebagai satu adegan: satu penutur, satu lokasi, satu emosi yang ditulis sebagai perbuatan terlihat (menahan tangis sambil memegang cangkir polos), bukan kata sifat (sedih, premium).
- Tulis dialog Bahasa Indonesia PERSIS di dalam prompt, dalam tanda kutip, maksimal ±20 kata per klip. Kalimat pendek menolong kejelasan pengucapan dan sinkronisasi bibir.
- Minta eksplisit: berbicara alami bahasa Indonesia, intonasi percakapan nyata, bukan narasi datar.
- **Orientasi vertikal WAJIB diminta eksplisit — keluaran bawaan TIDAK otomatis vertikal.** Audit 18 Nov 2026 membuktikan agen yang mengikuti skill ini tanpa frasa orientasi menerima 1280x720 LANSKAP. Frasa teruji (bukti klip uji 18 Nov 2026, ffprobe 720x1280): awali prompt dengan `Vertical portrait video, 9:16 aspect ratio, tall upright frame.` lalu lanjutkan deskripsi adegan.
- Satu panggilan `media.generate_video` per klip. **Durasi per klip ±10 detik adalah BATAS ALAT dan tidak bisa diatur** — itu bukan pilihan, dan BUKAN batas durasi video utuh.
- **Pola produksi multi-klip:** video utuh dibangun dari BANYAK klip ±10 detik yang digabung (stitching) di tahap kemasan lewat skill `kemasan-video`. Jangan pernah menyiratkan atau merencanakan video utuh seolah terbatas 10 detik; rencanakan beat-map sebagai rangkaian klip.
- **Penerusan konteks antar klip:** catat `snapshot_id` setiap hasil; klip lanjutan dibuat dengan `resume_from_snapshot_id` dari klip sebelumnya supaya wajah, lokasi, dan gaya nyambung antar klip. Perbaikan klip yang sama juga dilanjutkan dari snapshot-nya, bukan generate ulang dari nol.
- **Batas alat: 6 klip per pesan** (±60 detik materi per putaran). Susun urutan generate mengikuti irama itu.
- Bukti kekuatan jalur ini (18 Nov): klip uji dialog Indonesia satu penutur dinilai pemilik "nyata banget", "organic". Kelemahannya nada tidak bisa diarahkan sepresisi TTS — untuk dialog/akting ia menang, untuk narasi rata pakai Jalur B sebagai kandidat.
- **Peringatan format mentah:** keluaran mentah Jalur A terukur 720x1280 pada 24fps — **di BAWAH cek berkas Gerbang 2 PIPA-PRODUKSI (1080×1920, 30fps)**. Lolos audit skill ini TIDAK sama dengan siap produksi; penskalaan resolusi dan penyesuaian frame rate terjadi di tahap kemasan. Klip mentah berstatus bahan/bukti beat, bukan berkas tayang.

## Pencegahan AI slop — wajib SEBELUM generate

Slop dicegah di prompt, bukan ditambal sesudahnya. Pada uji 18 Nov wajah dan ekspresi lolos semua frame, tetapi teks di dalam frame garbled semua — terbukti di frame bernama hasil audit independen: subteks logo "Dantipun Hikar Eslepoc…", daftar di kardus "PACKI : PACKING PAUNG" dan "Rutin : EKT Ekspres", kalender pseudo-teks, label "ORDER" terpotong-potong. Itu satu-satunya kegagalan material klip tersebut, dan sumbernya prompt yang membiarkan teks masuk frame.

- **Larang teks di dalam frame.** Jangan meminta atau membiarkan: kardus/paket berlabel, signage, logo merek asli, kalender, papan tulis, layar HP/komputer berteks, koran, kemasan produk. Bila adegan rawan teks (gudang, toko, kantor), arahkan latar polos atau teks dibuat tidak terbaca secara alami (jauh, blur, terlipat) — atau ganti adegannya.
- **Teks yang harus terbaca = lapis deterministik.** Judul, caption, label, diagram ditambahkan di pasca-produksi lewat skill `kemasan-video`, tidak pernah diminta dari model video.
- **Satu penutur, satu adegan, durasi pendek.** Banyak wajah dan banyak adegan per klip menaikkan risiko wajah bergeser dan topologi meleleh.
- **Hindari tangan sebagai subjek hero** memegang benda kecil atau berteks; tangan wajar sebagai bagian adegan, bukan pusat bidikan.
- **Hindari cermin, pantulan berteks, dan kerumunan wajah.** Satu-dua wajah per klip.
- **Pra-terdaftar aturan lulus** sebelum generate (pola Mandat Pengecekan Ketat PIPA-PRODUKSI): tulis dulu butir yang akan dinilai di audit bawah, baru hasilkan klip termurah untuk beat paling berisiko.

## Jalur B — narasi TTS bawaan (PENDUKUNG)

Pakai untuk voiceover narasi bila Jalur A tidak cocok untuk beat-nya. Bukti 18 Nov: contoh narasi Indonesia dinilai pemilik "mulai tidak keliatan AI", tetapi nadanya lebih datar daripada dialog native Jalur A. Untuk dialog, Jalur A menang; untuk narasi, Jalur B kandidat yang wajib lolos audisi gerbang seperti kandidat suara lain — dan untuk tayang tunduk pada syarat lisensi Usulan 1 di bagian tata kelola atas.

- Pakai perintah teruji dari shell bersih (tanpa koneksi akun apa pun):

  `/opt/hatch/bin/tts speak --output <berkas.mp3> --language id --voice avocado_v2:MAI_03 --text-stdin`

  Teks diteruskan lewat stdin, bukan argumen shell. Suara bawaan lain yang sah: `avocado_v2:MAI_01` (Aria). Ganti bahasa lewat `--language` (Inggris `en`).
- Tulis teks seperti orang bicara: angka dan singkatan ditulis sebagai kata yang diucapkan, tanpa markdown, tanpa penanda kutipan.
- Periksa hasil: perintah mengembalikan `ok`, `path`, dan `bytes` (contoh terukur 18 Nov: 114.277 byte untuk 3 kalimat). Berkas gagal atau terpotong tidak pernah disampaikan sebagai hasil jadi.
- Untuk teks panjang atau banyak penutur, pakai `tts synthesize-script` dengan `--speaker Nama=VOICE_ID` per penutur.

## Audit ketat — wajib SEBELUM hasil dikirim ke Indra

Aturan pemilik (18 Nov 2026, 20:43): hasil generate AI tidak pernah dikirim mentah. Audit dulu, kirim bersama vonisnya.

1. **Ekstrak bukti** — perintah utuh siap salin-tempel (ganti `<klip.mp4>` dan `<folder-bukti>`):

   `ffprobe -v error -select_streams v:0 -show_entries stream=width,height,r_frame_rate,codec_name -show_entries format=duration -of default=noprint_wrappers=1 <klip.mp4>`

   `ffprobe -v error -select_streams a:0 -show_entries stream=codec_name,sample_rate,channels -of default=noprint_wrappers=1 <klip.mp4>`

   `mkdir -p <folder-bukti> && ffmpeg -v error -i <klip.mp4> -vf fps=1 <folder-bukti>/frame_%02d.png`
2. **Cek orientasi (dari keluaran ffprobe langkah 1).** Untuk Shorts wajib potret: `width < height` (terukur benar 720x1280). Bila `width > height` (1280x720 lanskap) = **GAGAL** — generate ulang dengan frasa orientasi vertikal di Jalur A; jangan diteruskan ke kemasan sebagai bahan Shorts.
3. **Nilai visual per frame bernama** (pola Gerbang 2B PIPA-PRODUKSI, sebut nama berkas frame yang diperiksa): konsistensi wajah penutur antar-frame; tangan wajar; dan **uji teks — setiap teks yang terlihat dibaca satu-satu; satu teks garbled = temuan material = klip GAGAL untuk produksi** (sah hanya sebagai bukti kemampuan). Tambahkan uji mustahil W-3 (objek menembus, elemen melayang, kontradiksi skala) dan uji gerak W-4 (tonton 1x dan 0,25x; subjek meleleh/berganti bentuk = GAGAL).
4. **Nilai audio.** Pastikan stream audio benar-benar ada (ffprobe langkah 1) dan ada bunyi suara, bukan stream senyap — cek terukur: `ffmpeg -i <klip.mp4> -af volumedetect -f null - 2>&1 | grep -E "mean_volume|max_volume"`. **Verifikasi isi dialog: per 18 Nov 2026 TIDAK ada alat transkripsi/ASR yang terpasang di VM ini** (diperiksa: tidak ada modul whisper/whisperx/faster-whisper; CLI `tts` hanya sintesis, bukan transkripsi). Karena itu isi dialog dinyatakan **BELUM TERVERIFIKASI MESIN** dan **WAJIB cek dengar manusia/Manager** sebelum vonis audio dijatuhkan — keberadaan stream dan bunyi hanya membuktikan ada suara, bukan isinya benar. Nada akhir tetap vonis telinga pemilik, di atas semua gerbang internal.
5. **Penilai bukan produsen (P-1).** Untuk produksi divisi, audit dijalankan worker penilai yang berbeda dari yang men-generate, memakai Gerbang 2B penuh. Pra-audit oleh produsen sendiri hanya sah untuk demo kemampuan dan wajib dilaporkan sebagai pra-audit, bukan vonis gerbang.
6. **Format vonis.** Tulis per butir: LOLOS / REVISI / TOLAK, dengan bukti frame bernama. Cacat yang diketahui produsen tidak boleh terbawa dalam vonis LOLOS (P-2). Klip REVISI digenerate ulang dengan prompt yang diperbaiki pada sumber slopnya (mis. teks dikeluarkan dari frame), bukan dipoles.

## Pagar

- Skill ini adalah mesin + disiplinnya di dalam pipa; urutan divisi tetap: Gerbang 1 naskah → produksi → Gerbang 2/2B → upload oleh Manager. **Lolos audit skill ini bukan lolos Gerbang 2** — keluaran mentah Jalur A masih di bawah cek berkas Gerbang 2 (lihat peringatan format di Jalur A) dan wajib lewat kemasan.
- Jangan memakai video generatif untuk beat yang menuntut presisi: diagram anatomi, teks informatif, angka. Itu wilayah lapis deterministik kita.
- Jangan mengklaim hasil generate "sudah dicek" hanya dari menonton sekali jalan; klaim cek hanya sah dari audit frame bernama di atas.
- Skill ini mengarahkan generate menjauhi slop dan menangkap slop yang tersisa sebelum ke pemilik — ia TIDAK menjamin generate bebas slop secara otomatis. Rumusan janji itu yang sah dipakai ke pemilik.
- Bila jalur bawaan gagal gerbang untuk kebutuhan tertentu, catat kegagalannya sebagai bukti, baru buka uji engine eksternal — dengan bukti itu di tangan, bukan dari ingatan.
