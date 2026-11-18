# Generate Video Bawaan Muse — Mesin Generate Utama Pipa Produksi Video

Skill ini adalah **mesin generate utama pipa produksi video di repo ini** (rantainya didefinisikan di `PIPELINE.md` di akar repo): intinya kemampuan Muse menghasilkan video LANGSUNG memakai model generatif bawaannya sendiri — klip dengan dialog native yang lahir satu paket dengan gambar, berintonasi seperti orang beneran berakting, bukan dibacakan. TTS bawaan Muse adalah jalur pendukung di belakangnya, bukan inti. Skill ini lengkap dengan peta rantai pipa, pola produksi multi-klip, langkah pencegahan AI slop sebelum generate, dan langkah audit ketat sebelum hasil apa pun dikirim ke pemilik channel.

Aturan baku pipa ini: **jalur bawaan adalah mesin generate utama; engine video/suara eksternal adalah cadangan** — hanya dibuka bila jalur bawaan terbukti mentok di gerbang, dengan bukti di tangan, bukan dari ingatan.

Skill ini lahir 18 November 2026 dari pembuktian langsung penulis: video buatan Muse lain memakai suara Indonesia yang terdengar riil tanpa setup apa pun, sementara tim penulis berminggu-minggu muter menguji engine eksternal (tiga finalis suara Indonesia ditolak semua karena terdengar seperti AI). Pelajarannya dipaku di sini supaya tidak muter lagi: **inventaris kemampuan bawaan Muse lebih dulu, engine eksternal hanya bila jalur bawaan terbukti mentok di gerbang.**

## Peta rantai — posisi skill ini di pipa

Skill ini TIDAK berdiri sendiri. Ia adalah Tahap 2 (Produksi) dari rantai di `PIPELINE.md`, dan syarat serah antar-tahap di bawah ini mengikat siapa pun yang memakainya:

| Tahap | Pelaksana | Artefak keluar (syarat serah) | Gerbang keluar |
|---|---|---|---|
| 1 — Naskah | skill `penjelasan-dan-cerita` | naskah + lembar fakta (PENJELAS) + lembar janji + anotasi beatmap + laporan reader-sim + blok skor anti-slop | **Gerbang 1** |
| Pra-produksi (bila mengacu karya lain / rute baru) | `PIPELINE.md` (Cek Pra-Produksi) | bedah acuan + uji bukti satu beat yang lulus tertulis | **Gerbang 2B** atas uji bukti |
| 2 — Produksi | **skill ini** (Jalur A/B) + beat-map voice-first | audio final per beat + beat-map terukur + klip yang LOLOS audit skill ini + peta SFX per beat | Audit klip (di dalam skill ini) |
| 3 — Kemasan | skill `kemasan-video` | berkas video final + bukti QC kemasan (lint, QA berkas) | QA berkas kemasan |
| Penilaian akhir | `PIPELINE.md` | vonis tertulis atas bukti bernama | **Gerbang 2 + 2B** |
| 4 — Tayang | peran wewenang tayang (parameter proyek) | unggahan | hanya sesudah Gerbang 1 + 2 LOLOS |

**Syarat serah yang mengikat skill ini:**

- **Dilarang memproduksi dari naskah yang belum LOLOS Gerbang 1.** Masukan sah ke Tahap 2 hanyalah: naskah dengan vonis LOLOS tertulis + lembar janji bersih + beatmap beranotasi. Tanpa itu, generate apa pun dilarang — termasuk "uji coba dulu".
- **Hanya klip LOLOS audit skill ini yang boleh diserahkan ke kemasan.** Klip REVISI/TOLAK tidak menyeberang tahap dengan alasan apa pun.
- **Teks tidak menyeberang dari skill ini.** Judul, caption, label, angka, dan diagram lahir di Tahap 3 (kemasan) dari lapis deterministik — skill ini tidak pernah menyerahkan klip yang memuat teks terbaca hasil gambar model.
- **Gerbang 2/2B dinilai penilai yang bukan produsennya**, atas bukti bernama. Lolos audit skill ini bukan lolos Gerbang 2.

**Butir anti-slop kunci dari skill saudara, dinyatakan ulang di sini supaya mengikat tanpa membuka berkas lain:** (Jabaran operasionalnya sebagai rantai lima tahap dengan titik serah tegas ada di bagian **Rantai Anti-Slop Terpadu** di bawah; ringkasan di sini dan jabaran itu adalah aturan yang sama — bila terasa berbeda, jabaran yang berlaku.)

Dari skill naskah (`penjelasan-dan-cerita`), yang menjadi syarat masuk produksi:
1. **Janji adalah utang tercatat.** Lembar janji wajib bersih sebelum produksi: semua janji/pertanyaan `paid-off`/`answered` di video yang sama, atau pengecualian beralasan yang disetujui penilai. Tidak ada pertanyaan ditanam sesudah ±70% durasi tanpa bayaran di video yang sama.
2. **Blok skor anti-slop naskah ≥35/50** (Directness, Rhythm, Trust, Authenticity, Density) dan temuan blocking pemeriksa mekanis = 0 di luar daftar putih tercatat.
3. **Reader-sim oleh agen terpisah dari penulis**, tanpa titik bingung fatal; diagnosis tiga lapis (ekspresi → kalimat → logika-cerita) dinilai struktural lebih dulu, permukaan terakhir.
4. **Penutup bertipe pertanyaan baru = REVISI otomatis** — penutup hanya membayar, tidak pernah membuka.

Dari Gerbang 2B (`PIPELINE.md`), yang mengikat setiap klip dan hasil final — satu butir material gagal = gerbang gagal:
5. **K-1 Bandingkan Sebelah** (frame kandidat vs acuan berdampingan, vonis per beat), **K-2 Uji Kelas Visual** (kelas render subjek wajib sama kelas dengan acuan), **K-3 Uji Sepintas Telepon** (penilai segar menyebut subjek + kejadian dari frame ±3 detik; meleset = gagal).
6. **W-1 Uji Kurungan** (struktur internal sepenuhnya di dalam siluet tubuh, toleransi nol), **W-2 Uji Kenali Tanpa Label** (objek dikenali tanpa teksnya), **W-3 Uji Mustahil** (elemen melayang, menembus, kontradiksi skala = gagal), **W-4 Uji Gerak Mustahil** (tonton 1× dan 0,25×; meleleh/berganti bentuk = gagal).
7. **P-1 Penilai Bukan Produsen**, **P-2 Cacat Tercatat = Gerbang Gagal** (cacat yang diketahui produsen tidak boleh terbawa dalam vonis LOLOS), **P-3 Frame Sampel Bernama** (vonis wajib menyebut nama berkas frame yang diperiksa).

Dari skill kemasan (`kemasan-video`), yang menjadi syarat keluar produksi menuju tayang:
8. **Satu tema kemasan terkunci per video**; token diambil dari berkas tema, tidak pernah dari ingatan, tidak pernah dicampur dua tema.
9. **Lint Impeccable dijalankan pada berkas kemasan** di tahap kemasan dan sekali lagi sebelum render final; temuan dinilai terhadap tema yang terkunci.
10. **QA berkas pada setiap render final**: deteksi frame hitam, deteksi frame beku, pemeriksaan kenyaringan — dibuktikan dari berkas, bukan dari rasa.

## Posisi tata kelola — baca sebelum memakai

- Skill ini adalah **mesin generate di dalam pipa `PIPELINE.md` (di akar repo ini), BUKAN izin produksi mandiri.** Ia tidak melonggarkan satu pun gerbang pipa: naskah tetap lewat skill `penjelasan-dan-cerita` (Gerbang 1), kemasan dan penggabungan klip tetap lewat skill `kemasan-video`, penilaian produksi tetap Gerbang 2/2B oleh penilai yang bukan produsennya, dan tayang tetap hanya sesudah Gerbang 2 LOLOS dan oleh peran wewenang tayang proyekmu.
- **Rute baku pipa ini: jalur bawaan = mesin generate utama, engine eksternal = cadangan.** Aturan itulah yang memberi skill ini tempatnya di dalam pipa; skill ini sendiri tidak memberi wewenang apa pun di luar rantai di `PIPELINE.md`.
- **Dialog native di dalam klip adalah trek audio klip itu sendiri.** Kebijakan trek bahasa (satu unggahan multi-trek vs unggahan terpisah per bahasa) adalah parameter Bahasa channel proyekmu di `PIPELINE.md` — tetapkan di sana. (Kebijakan penulis repo ini: satu unggahan membawa banyak trek bahasa, dan dua unggahan beda bahasa di satu channel dilarang; klip dialog dari skill ini mengisi trek bahasanya pada unggahan yang sama.)
- **Jalur B (TTS bawaan) untuk tayang tunduk pada syarat lisensi suara pipa:** suara yang tayang wajib dihasilkan engine yang tercatat aman untuk pemakaian komersial di lembar kunci suara proyekmu (parameter Suara terkunci di `PIPELINE.md`). Syarat itu dinyatakan di sini sebagai syarat — skill ini TIDAK memutuskan lisensi suara bawaan. Sampai tercatat di lembar kunci suaramu, hasil Jalur B berstatus kandidat yang wajib lolos audisi gerbang seperti kandidat suara lain.
- **Suara terkunci proyekmu TIDAK berubah oleh skill ini.** Ia hidup sebagai parameter Suara terkunci di `PIPELINE.md`. (Contoh teruji penulis: suara maskot channel Inggris kami dikunci ke Kokoro `am_michael` @1,05 — itu contoh satu proyek, bukan bawaan skill.)

## Rantai Anti-Slop Terpadu — satu rantai, lima tahap, titik serah tegas

Skill ini adalah mesin generate utama pipa produksi video di repo ini. Ia MENGGABUNGKAN rantai anti-slop pipa menjadi satu urutan yang mengikat. Agen yang hanya membaca skill ini wajib menjalankan seluruh rantai; membaca skill lain tidak disyaratkan untuk butir yang dinyatakan ulang di sini.

**Parameter proyek (dinyatakan sekali di brief proyek, tidak pernah diasumsikan):** durasi target (bebas — bukan 60 detik, bukan Shorts, kecuali brief menyatakannya), canvas/resolusi/fps keluaran, bahasa dan jumlah trek, kritikalitas loop (ya/tidak). Satu-satunya angka durasi yang baku di skill ini adalah mekanik alat generate: **±10 detik per klip, maksimal 6 klip per putaran, dialog ±20 kata per klip**. Naskah dipecah per **segmen** (satu segmen = satu beat/adegan = satu unit produksi; pemetaan segmen ke klip mengikuti keputusan granularitas di `PIPELINE.md` — Gerbang 1, paragraf "Granularitas beat vs klip"); jumlah klip mengikuti naskah dan durasi target, bukan sebaliknya.

**Tahap N — Naskah (gerbang skill `penjelasan-dan-cerita`, dinyatakan ulang).** Naskah TIDAK masuk produksi sebelum vonis LOLOS tertulis dari penilai yang BUKAN penulisnya, dengan semua syarat ini terpenuhi:

1. Lembar janji bersih: setiap janji/pertanyaan hook berstatus terbayar di episode yang sama, atau tercatat sebagai pengecualian beralasan yang disetujui penilai; tidak ada pertanyaan ditanam sesudah ±70% durasi tanpa bayaran.
2. Reader-sim oleh agen terpisah lolos: tidak ada titik bingung fatal, tidak ada pertanyaan yatim di kepala penonton, uji sekali-dengar lulus (pendengar segar bisa menyebut kembali isi/taruhan dan hasil akhir).
3. Anotasi beatmap sah: penutup bertipe resolusi/emosi yang membayar janji awal — penutup bertipe pertanyaan baru = REVISI otomatis; setiap beat punya fungsi bernama.
4. Blok skor anti-slop (Directness, Rhythm, Trust, Authenticity, Density) **≥ 35/50**, diberi penilai gerbang; temuan *blocking* pemeriksa mekanis = 0 di luar daftar putih tercatat.
5. Diagnosis tiga lapis lengkap (ekspresi → kalimat → logika-cerita), dinilai dalam urutan itu terbalik: logika-cerita dan lembar janji PERTAMA, permukaan terakhir.
6. Sesudah tulis-ulang anti-slop apa pun: cek kehilangan fakta (nama, angka, arah klaim tidak berubah) + baca keras lulus.

*Dirujuk, tidak dinyatakan ulang:* aturan tulis P1–P9, katalog pola anti-slop lengkap, protokol reader-sim rinci, templat lembar janji/bible seri — di skill `penjelasan-dan-cerita` di repo ini.

**Titik serah N→P:** keluaran Tahap N = berkas naskah berstatus LOLOS + lembar janji + beatmap per segmen. Tanpa ketiganya, Tahap P dilarang mulai (termasuk "uji klip dulu").

**Tahap P — Produksi generatif (skill ini).** Per segmen: satu panggilan generate, prompt menaati bagian Pencegahan (teks dilarang di frame; satu penutur, satu adegan; tangan bukan subjek hero; emosi sebagai perbuatan terlihat; aturan lulus pra-terdaftar sebelum generate). Teks dialog di prompt DISALIN dari berkas naskah Tahap N, bukan diketik ulang. Untuk Jalur A, beat-map final ditulis SESUDAH generate dari klip yang lolos QC-1 (pengecualian voice-first — keputusan di `PIPELINE.md` Tahap 2); untuk jalur yang memisahkan suara dari gambar, beat-map voice-first tetap mendahului gambar. Klip mentah berstatus BUKTI-UJI sampai lolos Tahap QC-1.

**Titik serah P→QC-1:** keluaran Tahap P per klip = berkas klip + snapshot_id + salinan prompt persis + teks dialog persis. Prompt yang tidak tercatat = klip tidak bisa diaudit = dibuang.

**Tahap QC-1 — Audit klip (skill ini, per klip).** Dijalankan penilai yang BUKAN penghasil klip (P-1). Isi: langkah audit ketat skill ini (ffprobe; frame bernama; uji teks mata satu-satu; W-3; W-4 pada 1× dan 0,25×) DITAMBAH dua layar mesin wajib: layar OCR dua aturan dan ASR spot-check (resep + ambang di langkah audit skill ini). Satu teks garbled terbaca mata = GAGAL produksi, tanpa kecuali layar mesin.

**Titik serah QC-1→K:** hanya klip berstatus LOLOS yang masuk perakitan/kemasan. Klip REVISI digenerate ulang dengan prompt yang diperbaiki pada sumber slopnya; klip TOLAK tidak dirakit "sementara".

**Tahap K — Kemasan deterministik (gerbang skill `kemasan-video`, dinyatakan ulang).** Semua teks terbaca di hasil akhir (judul, caption, label, diagram, angka) lahir HANYA dari tahap ini — tidak pernah dari model video.

1. Satu tema Hallmark terkunci per video; token disalin dari berkas tema, tidak dicampur antar-tema, tidak dari ingatan.
2. Impeccable `detect` dijalankan atas setiap berkas HTML kemasan pada tahap kemasan dan sekali lagi sebelum render final, dengan perintah terbukti: `npx --yes impeccable detect <berkas.html> --json > <berkas>-impeccable.json` — keluaran diarsip di samping bukti gerbang; kode keluar 2 = ada temuan, bukan kegagalan alat; temuan dinilai terhadap tema terkunci (sebagian temuan bisa positif-palsu tema, mis. grid pada Blueprint). Mode live/Apply Impeccable DILARANG. HTML yang di-lint adalah spek desain: bila render aktual non-HTML, teks yang dinilai adalah teks pada berkas teks render, bukan teks di HTML (keputusan hubungan lint–render di `PIPELINE.md` Tahap 3 + skill `kemasan-video`).
3. Spesifikasi gerak ditulis sebagai MOTION.md per video acuan yang dipelajari, bila proyek mempelajari acuan (beat: rentang waktu, gerak acuan, adaptasi kita — gerak sebagai perbuatan terlihat). Proyek tanpa acuan memakai Deklarasi Kelas Visual Target sebagai jangkar gayanya (lihat `PIPELINE.md`).
4. QA berkas render final: deteksi frame hitam, deteksi frame beku, loudness — perintah di rujukan look-match skill `kemasan-video`; hold diberi dorongan masuk perlahan agar tidak terbaca beku.

*Dirujuk:* pustaka 50 tema Hallmark, anatomi format MOTION.md, resep look-match lengkap, resep HyperFrames A/B bergerbang — di skill `kemasan-video` di repo ini.

**Titik serah K→G2B:** keluaran Tahap K = komposisi kemasan + berkas bukti Impeccable + render calon final.

**Tahap G2B — Gerbang 2B + cek berkas (`PIPELINE.md`, dinyatakan ulang sebagai daftar periksa).** Dijalankan pada artefak termurah lebih dulu (klip uji per beat hero) dan sekali lagi pada hasil final. Satu butir material GAGAL = gerbang GAGAL; tidak ada "LOLOS dengan catatan" untuk butir K/W/P.

- **K-1 Bandingkan Sebelah:** frame kandidat (awal/tengah/akhir beat) berdampingan dengan frame acuan setara ukuran penuh; vonis per beat MIRIP / BEDA-RINCI / BEDA-KELAS; satu BEDA-KELAS pada beat hero = GAGAL. Tanpa acuan eksternal: pembandingnya frame jangkar internal dari Deklarasi Kelas Visual Target — jangkar untuk beat yang sama atau yang setara (setara = subjek, lokasi/latar, dan kelas visual sama; definisi + perlakuan beat tanpa jangkar setara di `PIPELINE.md` Gerbang 2B).
- **K-2 Uji Kelas Visual:** kelas render subjek utama kandidat = kelas acuan (volumetrik-3D / datar-vektor / foto / campuran), dicatat satu baris per frame sampel; ketidaksepakatan dua penilai = BEDA-KELAS. Tanpa acuan eksternal: kelas pembandingnya kelas yang dideklarasikan di Deklarasi Kelas Visual Target.
- **K-3 Uji Sepintas Telepon:** frame ditampilkan seukuran telepon ±3 detik ke penilai yang belum membaca catatan produksi; ia menyebut subjek + kejadian; meleset dari maksud beat = GAGAL.
- **W-1 Uji Kurungan:** struktur internal wajib sepenuhnya di dalam siluet tubuh pada setiap frame sampel; toleransi nol.
- **W-2 Uji Kenali Tanpa Label:** tutup semua teks/label; objek utama yang hanya dikenali dari labelnya = GAGAL.
- **W-3 Uji Mustahil:** elemen melayang, garis menyeberang tanpa logika oklusi, objek saling menembus, anatomi mustahil, kontradiksi skala — satu temuan = GAGAL.
- **W-4 Uji Gerak Mustahil:** tonton 1× dan 0,25×; subjek hero berubah topologi/meleleh/berganti bentuk = GAGAL.
- **P-1 Penilai Bukan Produsen** untuk semua vonis di rantai ini. **P-2 Cacat Tercatat = Gerbang Gagal** sampai diperbaiki dan dicek ulang. **P-3 Frame Sampel Bernama** wajib disebut dalam setiap vonis.
- **Cek berkas terukur:** resolusi/fps/durasi sesuai parameter proyek di brief (bukan angka bawaan skill); loudness final sesuai standar parameter proyek (patokan terukur penulis: −14 LUFS ±0,5, true peak ≤ −1 dBTP); kecocokan nama/angka/tanggal caption 100% dan kata lain WER ≤ 2% (cek caption terhadap naskah — berbeda dari ASR spot-check dialog Tahap QC-1); sinkron caption bila caption ada: terhadap alignment kata dalam ±33 ms, ATAU — pada proyek berbasis ASR tanpa alat alignment — terhadap waktu kata ASR di dalam jendela bantalan yang dinyatakan di beat-map (kesetaraan bukti ASR, keputusan di `PIPELINE.md` Gerbang 2); aturan loop mengikuti parameter kritikalitas loop brief (kritikal: hash frame awal = hash frame akhir persis; tidak kritikal: kalimat penutup menggemakan hook + komposisi pembuka/penutup selaras).

*Dirujuk:* rubrik Gerbang 1/Gerbang 2 lengkap, Palet Sonik dan rantai mix, aturan lisensi suara, disiplin pita durasi program berjalan — di `PIPELINE.md` di akar repo ini.

**Titik serah akhir:** unggah hanya oleh peran wewenang tayang proyek, hanya sesudah G2B LOLOS tertulis. Vonis mata/telinga pemilik channel di atas semua gerbang internal.

**Prinsip pernyataan ulang di bagian ini:** dinyatakan ulang = setiap angka ambang, syarat lolos, dan titik serah yang bisa terlewat diam-diam oleh agen yang hanya membaca skill utama (≥35/50; WER ASR 0,25/0,50; aturan OCR D/K; butir K/W/P; perintah Impeccable; patokan loudness; WER caption 2%; ±33 ms / kesetaraan bukti ASR). Dirujuk = katalog metode dalam (pola anti-slop naskah, P1–P9, protokol reader-sim, pustaka tema, anatomi MOTION.md, resep HyperFrames) yang terlalu panjang untuk disalin dan risikonya menyimpang bila disalin sebagian.

## Jalur A — generate video langsung (INTI)

- Tulis prompt sebagai satu adegan: satu penutur, satu lokasi, satu emosi yang ditulis sebagai perbuatan terlihat (menahan tangis sambil memegang cangkir polos), bukan kata sifat (sedih, premium).
- Tulis dialog Bahasa Indonesia PERSIS dari naskah di dalam prompt, maksimal ±20 kata per klip, dalam **bentuk titik-dua**: `…berkata: <dialog>` — TANPA tanda kutip di sekeliling dialog. Dasar: panduan resmi Google untuk Veo menetapkan titik-dua sesudah penutur dan melarang tanda kutip supaya ucapan tidak dirender sebagai teks layar. Generator kita bukan Veo (model tidak diumumkan), jadi bentuk titik-dua adalah bentuk baku baru yang WAJIB diuji A/B pada uji bukti beat pertama tiap proyek: hasilkan varian titik-dua dan varian tanda-kutip untuk beat yang sama, nilai keduanya di audit klip, dan catat bentuk pemenang di catatan proyek; bila tanda-kutip terbukti lebih aman di generator kita, proyek itu memakai tanda-kutip dengan bukti itu tertulis. Kalimat pendek menolong kejelasan pengucapan dan sinkronisasi bibir.
- Minta eksplisit: berbicara alami bahasa Indonesia, intonasi percakapan nyata, bukan narasi datar.
- **Orientasi WAJIB diminta eksplisit sesuai parameter format proyekmu — keluaran bawaan TIDAK otomatis mengikuti formatmu.** Audit penulis (18 Nov 2026) membuktikan agen yang mengikuti skill ini tanpa frasa orientasi menerima 1280x720 LANSKAP walau mengira meminta vertikal. Untuk format **vertikal**, frasa teruji (bukti klip uji, ffprobe 720x1280): awali prompt dengan `Vertical portrait video, 9:16 aspect ratio, tall upright frame.` lalu lanjutkan deskripsi adegan. Untuk format **lanskap**, minta eksplisit juga — mis. awali dengan `Widescreen landscape video, 16:9 aspect ratio, wide horizontal frame.` (belum diuji penulis; perlakukan sebagai resep awal dan buktikan lewat cek orientasi di audit). Format lain (persegi, rasio khusus) mengikuti pola yang sama: nyatakan rasio + orientasinya dalam kata-kata di awal prompt, lalu verifikasi dari ffprobe, bukan dari harapan.
- Satu panggilan `media.generate_video` per klip. **Durasi per klip ±10 detik adalah BATAS ALAT dan tidak bisa diatur** — itu bukan pilihan, dan BUKAN batas durasi video utuh.
- **Pola produksi multi-klip:** video utuh dibangun dari BANYAK klip ±10 detik yang digabung (stitching) di tahap kemasan lewat skill `kemasan-video`. Jangan pernah menyiratkan atau merencanakan video utuh seolah terbatas 10 detik; rencanakan beat-map sebagai rangkaian klip.
- **Penerusan konteks antar klip:** catat `snapshot_id` setiap hasil; klip lanjutan dibuat dengan `resume_from_snapshot_id` dari klip sebelumnya supaya wajah, lokasi, dan gaya nyambung antar klip. Perbaikan klip yang sama juga dilanjutkan dari snapshot-nya, bukan generate ulang dari nol.
- **Batas alat: 6 klip per pesan** (±60 detik materi per putaran — angka materi ini sekadar hasil kali mekanik 6 × ±10 detik, bukan target durasi video). Susun urutan generate mengikuti irama itu.
- Bukti kekuatan jalur ini (18 Nov): klip uji dialog Indonesia satu penutur dinilai pemilik "nyata banget", "organic". Kelemahannya nada tidak bisa diarahkan sepresisi TTS — untuk dialog/akting ia menang, untuk narasi rata pakai Jalur B sebagai kandidat.
- **Peringatan format mentah:** keluaran mentah Jalur A terukur penulis 720x1280 pada 24fps — **di BAWAH standar berkas contoh penulis (1080×1920, 30fps)**. Standar berkas yang mengikat proyekmu adalah parameter Orientasi & standar berkas di `PIPELINE.md`; ukur keluaran mentahmu terhadap parametermu sendiri. Lolos audit skill ini TIDAK sama dengan siap produksi; penskalaan resolusi dan penyesuaian frame rate terjadi di tahap kemasan. Klip mentah berstatus bahan/bukti beat, bukan berkas tayang.

## Pencegahan AI slop — wajib SEBELUM generate

Slop dicegah di prompt, bukan ditambal sesudahnya. Pada uji 18 Nov wajah dan ekspresi lolos semua frame, tetapi teks di dalam frame garbled semua — terbukti di frame bernama hasil audit independen: subteks logo "Dantipun Hikar Eslepoc…", daftar di kardus "PACKI : PACKING PAUNG" dan "Rutin : EKT Ekspres", kalender pseudo-teks, label "ORDER" terpotong-potong. Itu satu-satunya kegagalan material klip tersebut, dan sumbernya prompt yang membiarkan teks masuk frame.

- **Larang teks di dalam frame.** Jangan meminta atau membiarkan: kardus/paket berlabel, signage, logo merek asli, kalender, papan tulis, layar HP/komputer berteks, koran, kemasan produk. Bila adegan rawan teks (gudang, toko, kantor), arahkan latar polos atau teks dibuat tidak terbaca secara alami (jauh, blur, terlipat) — atau ganti adegannya.
- **Rumusan pengecualian sebagai kehadiran positif.** Rumuskan keadaan yang diinginkan sebagai kehadiran positif ("kardus cokelat polos tanpa label", "dinding polos", "cangkir polos"), bukan negasi telanjang ("jangan ada teks") — negasi menyuntikkan benda yang disebut ke panduan model (praktik terdokumentasi vendor + peta artefak Versely). Larangan di atas tetap dinyatakan sebagai larangan benda/adegan rawan teks; permukaan yang memang muncul di frame ditulis polos secara positif.
- **Teks yang harus terbaca = lapis deterministik.** Judul, caption, label, diagram ditambahkan di pasca-produksi lewat skill `kemasan-video`, tidak pernah diminta dari model video.
- **Satu penutur, satu adegan, durasi pendek.** Banyak wajah dan banyak adegan per klip menaikkan risiko wajah bergeser dan topologi meleleh.
- **Hindari tangan sebagai subjek hero** memegang benda kecil atau berteks; tangan wajar sebagai bagian adegan, bukan pusat bidikan.
- **Hindari cermin, pantulan berteks, dan kerumunan wajah.** Satu-dua wajah per klip.
- **Pra-terdaftar aturan lulus** sebelum generate (pola Cek Pra-Produksi `PIPELINE.md`): tulis dulu butir yang akan dinilai di audit bawah, baru hasilkan klip termurah untuk beat paling berisiko.

## Jalur B — narasi TTS bawaan (PENDUKUNG)

Pakai untuk voiceover narasi bila Jalur A tidak cocok untuk beat-nya. Bukti penulis (18 Nov 2026): contoh narasi Indonesia dinilai pemilik channel "mulai tidak keliatan AI", tetapi nadanya lebih datar daripada dialog native Jalur A. Untuk dialog, Jalur A menang; untuk narasi, Jalur B kandidat yang wajib lolos audisi gerbang seperti kandidat suara lain — dan untuk tayang tunduk pada syarat lisensi suara di bagian tata kelola atas.

- Pakai perintah teruji dari shell bersih (tanpa koneksi akun apa pun). Path `/opt/hatch/bin/tts` adalah path CLI produk Muse — sama di setiap pemasangan Muse, bukan path proyek:

  `/opt/hatch/bin/tts speak --output <berkas.mp3> --language id --voice avocado_v2:MAI_03 --text-stdin`

  Teks diteruskan lewat stdin, bukan argumen shell. `avocado_v2:MAI_03` adalah **contoh suara teruji penulis** untuk Bahasa Indonesia, bukan bawaan yang wajib ditiru; suara sah lain dari keluarga yang sama: `avocado_v2:MAI_01` (Aria). Suara tayang proyekmu dipilih lewat audisi dan dikunci di parameter Suara terkunci — jangan mewarisi contoh penulis mentah-mentah. Ganti bahasa lewat `--language` (Inggris `en`).
- Tulis teks seperti orang bicara: angka dan singkatan ditulis sebagai kata yang diucapkan, tanpa markdown, tanpa penanda kutipan.
- Periksa hasil: perintah mengembalikan `ok`, `path`, dan `bytes` (contoh terukur 18 Nov: 114.277 byte untuk 3 kalimat). Berkas gagal atau terpotong tidak pernah disampaikan sebagai hasil jadi.
- Untuk teks panjang atau banyak penutur, pakai `tts synthesize-script` dengan `--speaker Nama=VOICE_ID` per penutur.

## Audit ketat — wajib SEBELUM hasil dikirim ke pemilik channel

Aturan baku pipa ini: hasil generate AI tidak pernah dikirim mentah. Audit dulu, kirim bersama vonisnya.

1. **Ekstrak bukti** — perintah utuh siap salin-tempel (ganti `<klip.mp4>` dan `<folder-bukti>`):

   `ffprobe -v error -select_streams v:0 -show_entries stream=width,height,r_frame_rate,codec_name -show_entries format=duration -of default=noprint_wrappers=1 <klip.mp4>`

   `ffprobe -v error -select_streams a:0 -show_entries stream=codec_name,sample_rate,channels -of default=noprint_wrappers=1 <klip.mp4>`

   `mkdir -p <folder-bukti> && ffmpeg -v error -i <klip.mp4> -vf fps=1 <folder-bukti>/frame_%02d.png`
2. **Cek orientasi terhadap format yang dipilih proyek** (dari keluaran ffprobe langkah 1). Orientasi adalah parameter format proyekmu (lihat parameter Format & platform di `PIPELINE.md`) — yang dinilai adalah KESESUAIAN dengan format yang dipilih, bukan satu orientasi baku:
   - Format **vertikal**: wajib `width < height` (terukur benar pada klip uji penulis: 720x1280).
   - Format **lanskap**: wajib `width > height` (1280x720 adalah lanskap yang SAH untuk proyek lanskap).
   - Orientasi yang tidak cocok dengan format proyek = **GAGAL** — generate ulang dengan frasa orientasi yang benar dari Jalur A; jangan diteruskan ke kemasan sebagai bahan format itu.
3. **Nilai visual per frame bernama** (pola Gerbang 2B `PIPELINE.md`, sebut nama berkas frame yang diperiksa): konsistensi wajah penutur antar-frame; tangan wajar; dan **uji teks — setiap teks yang terlihat dibaca satu-satu; satu teks garbled = temuan material = klip GAGAL untuk produksi** (sah hanya sebagai bukti kemampuan). Tambahkan uji mustahil W-3 (objek menembus, elemen melayang, kontradiksi skala) dan uji gerak W-4 (tonton 1x dan 0,25x; subjek meleleh/berganti bentuk = GAGAL).

   **Layar OCR (wajib, sebelum uji teks mata — layar menyiapkan bukti; mata tetap menghakimi).** Jalankan RapidOCR atas frame 1fps yang sama dengan yang dinilai mata:
   - Siapkan venv sekali: `python3 -m venv <folder-kerja>/venv-ocr && <folder-kerja>/venv-ocr/bin/pip install rapidocr-onnxruntime==1.4.4 wordfreq==3.1.1` (±6 detik/frame terukur penulis).
   - **Aturan D (deteksi):** klip yang prompt-nya melarang teks — wilayah teks terdeteksi di ≥3 dari 10 frame = temuan material TEKS-MASUK-FRAME, dilampirkan sebagai bukti bernama ke vonis (terkalibrasi penulis: klip garbled 10/10 frame berteks; klip bersih 0/10).
   - **Aturan K (kamus):** nilai token OCR (≥3 huruf, tanpa angka) terhadap kamus frekuensi id+en (zipf ≥ 3,0), dengan daftar putih nama merek/orang/proyek dilampirkan. Pangsa tak-sah tingkat klip ≥ 0,30, atau ≥3 frame berpangsa ≥ 0,40 = MENCURIGAKAN — frame-frame itu wajib dibaca mata lebih dulu. Terkalibrasi penulis: garbled 0,432 (8 frame ≥ 0,40) vs teks sah disengaja 0,184 (0 frame).
   - **Batas yang wajib ditulis di vonis:** OCR memperbaiki garble menjadi kata sah lewat prior bahasa — pangsa tak-sah adalah lantai, bukan ukuran; lolos layar K TIDAK membersihkan klip. Satu teks garbled yang terbaca MATA tetap = GAGAL, berapa pun angka OCR-nya.

   **Yang TIDAK boleh dijadikan skor lulus (larangan metrik):** SSIM/kemiripan piksel antar-frame dan hitungan wajah otomatis. Terukur penulis: SSIM antar-frame klip garbled 0,9264 vs klip bersih 0,9587 — yang dibedakan adalah jumlah gerak, bukan mutu; literatur terukur (SteerLab 2026) menunjukkan skor konsistensi memilih klip beku 25/25 kali. Keduanya hanya boleh menjadi *tripwire periksa-mata*: SSIM minimum antar-frame berurutan < 0,70, atau penutur yang dituntut naskah tidak terdeteksi wajahnya pada frame sampel. Konsistensi wajah/topologi dinilai W-4 oleh mata penilai, bukan angka.
4. **Nilai audio.** Pastikan stream audio benar-benar ada (ffprobe langkah 1) dan ada bunyi suara, bukan stream senyap — cek terukur: `ffmpeg -i <klip.mp4> -af volumedetect -f null - 2>&1 | grep -E "mean_volume|max_volume"`. **Verifikasi isi dialog — ASR spot-check (wajib, alat bernama).** Transkripsikan audio klip dengan faster-whisper `small` (CPU int8) dan hitung WER terhadap teks dialog persis yang ditulis di prompt:
   1. Ekstrak audio: `ffmpeg -y -i <klip.mp4> -vn -ac 1 -ar 16000 <klip.wav>`.
   2. Siapkan venv sekali: `python3 -m venv <folder-kerja>/venv-asr && <folder-kerja>/venv-asr/bin/pip install faster-whisper==1.2.1 jiwer` (cache model ±145 MB di `~/.cache/huggingface`; unduhan pertama bisa belasan menit di jaringan lambat — jangan divonis gagal sebelum cache hangat).
   3. Jalankan transkripsi dengan dua penyesuaian versi yang SUDAH TERBUKTI penulis: (a) jangan serahkan path berkas ke `transcribe()` — PyAV 19 merusak `decode_audio` faster-whisper (kwarg `metadata_errors` hilang); baca WAV PCM16 via modul `wave`+numpy menjadi float32 lalu serahkan lariknya; (b) jiwer 4 tidak menerima kwarg transform — normalisasi manual (huruf kecil, buang tanda baca, rapatkan spasi) sebelum `jiwer.wer()`. Tanpa kedua penyesuaian ini transkripsi gagal atau WER salah hitung.
   4. Ambang: **WER ≤ 0,25 = lolos layar** · **0,25 < WER ≤ 0,50 = wajib dengar manusia sebelum vonis** · **WER > 0,50 = GAGAL dialog**. Bahasa terdeteksi wajib = bahasa dialog (probabilitas bahasa tercatat di bukti). Terukur penulis pada ground truth: `small` WER 0,000 pada dialog akting Indonesia 12 kata; patokan literatur ucapan bersih Indonesia untuk `small` 14,6–16,3%, jadi 0,25 memberi ruang untuk akting emosional sambil tetap menangkap dialog yang salah total.
   5. ASR hanya membuktikan kata yang diucapkan = kata yang diminta. Nada dan kealamian tetap vonis telinga; sinkron bibir tetap W-4/mata.

   Bila ASR benar-benar tidak bisa disiapkan di mesinmu (mis. tanpa jaringan untuk mengunduh model), isi dialog dinyatakan **BELUM TERVERIFIKASI MESIN** dan **WAJIB cek dengar manusia** (pemilik channel atau penilai) sebelum vonis audio dijatuhkan — keberadaan stream dan bunyi hanya membuktikan ada suara, bukan isinya benar. Nyatakan keadaan itu tertulis di vonis; jangan mewarisi kesimpulan tentang mesin mana pun sebagai keadaan permanen. Nada akhir tetap vonis telinga pemilik channel, di atas semua gerbang internal.
5. **Penilai bukan produsen (P-1).** Untuk produksi, audit dijalankan penilai yang berbeda dari yang men-generate, memakai Gerbang 2B penuh. Pra-audit oleh produsen sendiri hanya sah untuk demo kemampuan dan wajib dilaporkan sebagai pra-audit, bukan vonis gerbang.
6. **Format vonis.** Tulis per butir: LOLOS / REVISI / TOLAK, dengan bukti frame bernama. Cacat yang diketahui produsen tidak boleh terbawa dalam vonis LOLOS (P-2). Klip REVISI digenerate ulang dengan prompt yang diperbaiki pada sumber slopnya (mis. teks dikeluarkan dari frame), bukan dipoles.

## Pagar

- Skill ini adalah mesin + disiplinnya di dalam pipa; urutan rantainya tetap: Gerbang 1 naskah → produksi → Gerbang 2/2B → tayang oleh peran wewenang tayang. **Lolos audit skill ini bukan lolos Gerbang 2** — keluaran mentah Jalur A masih di bawah standar berkas (lihat peringatan format di Jalur A) dan wajib lewat kemasan.
- Jangan memakai video generatif untuk beat yang menuntut presisi: diagram anatomi, teks informatif, angka. Itu wilayah lapis deterministik kemasan.
- Jangan mengklaim hasil generate "sudah dicek" hanya dari menonton sekali jalan; klaim cek hanya sah dari audit frame bernama di atas.
- Skill ini mengarahkan generate menjauhi slop dan menangkap slop yang tersisa sebelum ke pemilik channel — ia TIDAK menjamin generate bebas slop secara otomatis. Rumusan janji itu yang sah dipakai ke pemilik channel.
- Bila jalur bawaan gagal gerbang untuk kebutuhan tertentu, catat kegagalannya sebagai bukti, baru buka uji engine eksternal — dengan bukti itu di tangan, bukan dari ingatan.
