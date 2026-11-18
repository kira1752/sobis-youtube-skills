# PIPELINE — Pipa Produksi Video

**Status: FINAL (2026-11-18).** Dokumen ini adalah tulang punggung rantai produksi yang dijalankan ketiga skill di repo ini. Ia berdiri sendiri: sebuah Muse yang baru mengambil repo ini bisa menjalankan rantai ujung-ke-ujung hanya dari dokumen ini + ketiga `SKILL.md`, tanpa konteks lain. Slot parameter bertanda `[ISI: ...]` memang disisakan kosong — itu parameter pemakai, diisi sebelum produksi pertama, bukan draf yang belum selesai.

Satu prinsip penataan: **struktur tahap dan gerbang bersifat tetap; durasi, format, bahasa, dan suara adalah parameter proyek.** Tidak ada tahap di pipa ini yang terkunci ke durasi atau format tertentu. Isi parameter proyekmu lebih dulu (bagian pertama), lalu jalankan rantainya.

## Parameter proyek — isi sebelum produksi pertama

| Parameter | Slot | Catatan |
|---|---|---|
| Durasi target | [ISI: durasi target video, mis. 60 detik / 3 menit / 12 menit] | Durasi adalah keputusan proyek per video atau per seri. Struktur tahap/gerbang di bawah tidak berubah oleh durasi; yang berubah hanya jumlah segmen dan jumlah klip. |
| Format & platform | [ISI: platform dan format, mis. YouTube Shorts vertikal / YouTube long-form lanskap / Reels] | Menentukan orientasi, resolusi, dan zona aman teks. |
| Orientasi & standar berkas | [ISI: resolusi, frame rate, loudness, mis. 1080×1920, 30 fps, −14 LUFS, true peak ≤ −1 dBTP] | Dipakai cek berkas di Gerbang 2. Angka contoh di sini adalah standar terukur yang kami pakai; kalibrasikan ke platformmu. |
| Bahasa channel | [ISI: bahasa utama video + kebijakan trek bahasa lain bila ada] | Naskah, dialog, dan caption mengikuti slot ini. |
| Suara terkunci | [ISI: ID suara / resep suara narator tetap + engine penghasilnya + status lisensinya] | Satu suara tetap untuk semua video. Suara yang tayang WAJIB dihasilkan engine yang tercatat aman untuk pemakaian komersial di lembar kunci suara proyekmu. Mengganti suara di tengah seri hanya lewat keputusan tertulis pemilik channel. |
| Tema visual kemasan | [ISI: nama tema kemasan yang terkunci per video/seri] | Satu tema per video; token diambil dari berkas tema, bukan dari ingatan. |
| Mesin render kemasan | [ISI: mesin render proyekmu, mis. proyek Remotion sendiri] | Pipa ini tidak menyediakan proyek render; kemasan dikerjakan pada mesin proyekmu. |
| Wewenang tayang | [ISI: siapa yang berhak mengunggah/memutuskan tayang] | Unggah hanya oleh peran ini, hanya sesudah semua gerbang LOLOS. |

## Prinsip yang mengikat semua tahap

1. **Janji adalah utang tercatat.** Setiap pertanyaan yang ditanam dan setiap janji hook dicatat di lembar janji dan wajib terbayar di video yang sama, atau tercatat sebagai pengecualian beralasan yang disetujui penilai.
2. **Penilai bukan produsen.** Di setiap gerbang, yang memberi vonis adalah agen/sesi yang berbeda dari yang memproduksi tahap itu. Catatan produsen adalah bukti masukan, bukan vonis. Cacat yang diketahui produsen tidak boleh terbawa dalam vonis LOLOS — cacat tercatat = gerbang gagal sampai diperbaiki dan dicek ulang.
3. **Teks terbaca lahir di lapis deterministik, tidak pernah digambar model generatif.** Judul, caption, label, angka, dan diagram ditambahkan di tahap kemasan dari data/teks yang pasti. Model video tidak pernah diminta menulis teks di dalam frame.
4. **Klaim "sudah dicek" hanya sah dari bukti bernama.** Vonis gerbang wajib menyebut nama berkas bukti yang diperiksa (frame sampel per beat, berkas audio, berkas hasil cek). Vonis dari sekali menonton/mendengar tanpa bukti bernama tidak sah.
5. **Putaran revisi berjalan sampai LOLOS.** Bila gerbang menemukan problem: adaptasi dan modifikasi persis sesuai kriteria penilai, lalu nilai ulang. Tidak ada batas putaran kaku; bila problem yang sama berulang tanpa kemajuan, pemilik channel memutuskan ganti pendekatan atau ganti topik.
6. **Suara dan gaya boleh khas, standar mutu tidak boleh turun.** Jangkar konsistensi antarvideo adalah suara terkunci + rumus mutu gerbang, bukan gaya gambar yang dipaku.

## Rantai tahap

### Tahap 1 — Naskah (skill `penjelasan-dan-cerita`)

Kerjakan dengan skill naskah. Naskah dibangun **per segmen/adegan (beat)**, bukan per durasi: jumlah beat mengikuti durasi target parameter proyek. Alur di dalam tahap ini:

1. Pilih mode: PENJELAS (fakta dijelaskan) atau CERITA (tokoh berusaha) — campuran ditentukan oleh apa yang ditunggu penonton: jawaban (PENJELAS) atau nasib tokoh (CERITA).
2. Lembar fakta (PENJELAS): setiap klaim dipetakan ke baris fakta bersumber; status FAKTA hanya untuk klaim yang tertelusur ke sumber primer atau pelaporan langsung media tingkat satu; sisanya berstatus laporan/dugaan dan dibingkai jujur sebagai dugaan di naskah. Penilai gerbang memeriksa acak ≥3 baris FAKTA ke sumber aslinya.
3. Lembar janji: pertanyaan hook satu kalimat; tiap janji/pertanyaan/setup dengan beat menanam dan beat membayar yang direncanakan; pengecualian beralasan dicatat tertulis. Tidak ada pertanyaan/setup baru ditanam sesudah ±70% durasi tanpa bayaran di video yang sama.
4. Tulis mengikuti aturan mode (P1–P9 untuk PENJELAS; busur terkompresi + uji kausasi therefore/but + try-fail untuk CERITA — keduanya di `SKILL.md` skill naskah). Aturan durasi di dalam aturan itu berskala terhadap durasi target proyekmu, bukan angka tetap.
5. Lapisan anti-slop atas draf penuh: pemeriksa mekanis dua tingkat (blocking wajib nol di luar daftar putih; advisory diputuskan satu per satu) → tandai pola bergrada → tulis ulang → cek kehilangan fakta → baca keras / dengarkan render suara draf.
6. Anotasi beatmap: tiap beat bertipe outcome dan fungsi bayaran bernama; penutup bertipe pertanyaan baru = REVISI otomatis.
7. Reader-sim oleh agen yang **terpisah dari penulis**: persona penonton awam platformmu [ISI: persona penonton sesuai parameter format], laporan momen-ke-momen, uji sekali-dengar.

**Artefak keluar tahap 1:** naskah + lembar fakta (PENJELAS) + lembar janji + anotasi beatmap + laporan reader-sim + blok skor anti-slop.

### GERBANG 1 — Penilaian naskah (penilai ≠ penulis)

Naskah TIDAK lanjut ke produksi sebelum lolos gerbang ini. Vonis: **LOLOS / REVISI / TOLAK**.

1. **Hook** — empat sub-skor 0–2: (a) pukulan ≤2 detik (kata pertama narasi ATAU teks layar frame 0), (b) janji yang bisa dibayar isi, (c) teks + suara + gambar serentak sejak frame 0, (d) beat kedua 3–7 detik. Lolos bila total ≥6/8 DAN tidak ada 0 pada (a) atau (b). Naskah memisahkan baris [HOOK — beat 1] dan [JANJI/LANGKAH PERTAMA — beat 2].

**Granularitas beat vs klip (keputusan, mengikat untuk sub-skor (d) dan semua penilaian waktu di gerbang ini):** beat adalah unit naskah; klip adalah unit produksi (±10 detik, mekanik alat). Keduanya tidak harus berimpit: satu klip boleh memuat beberapa beat, dan satu beat boleh terbagi ke lebih dari satu klip. Sub-skor (d) dinilai pada **peta waktu naskah**: penilai memetakan tiap beat ke rentang detik dari tempo baca terukur proyek (kata kumulatif ÷ tempo), dan (d) dinilai dari posisi MULAI beat kedua pada peta waktu itu — batas klip tidak dipakai sebagai batas beat. Bila beat kedua terbagi lintas klip, posisi mulainya tetap posisinya pada peta waktu naskah. Menilai (d) dari awal klip kedua adalah kesalahan penilaian.
2. **Kesederhanaan penjelasan** — orang awam yang tidak tahu topiknya bisa mengikuti awal sampai akhir tanpa tersesat: satu ide per langkah, istilah berat selalu dijelaskan, analogi membantu bukan mengaburkan.
3. **Kejujuran materi** — klaim sesuai lembar fakta; dugaan dibingkai sebagai dugaan dengan kata-kata biasa; candaan/analogi tidak mengubah fakta.
4. **Nada** — sesuai jiwa channel proyekmu [ISI: nada channel]; bukan kuliah kaku.
5. **Alur utuh** — mengalir logis dari hook sampai penutup tanpa lompatan yang membingungkan.
6. **Penutup membayar** — kalimat terakhir hanya memakai bahan yang sudah ditanam; menggemakan hook bila format proyekmu memakai loop [ISI: aturan loop proyekmu, bila ada].
7. **Durasi sesuai parameter** — panjang naskah cocok dengan durasi target proyek (hitung dari tempo baca terukur proyekmu), termasuk disiplin pita durasi platformmu bila ada [ISI: pita durasi yang dihindari/dianjurkan platformmu, bila ada].
8. **Kreativitas** — sudut, analogi, dan candaan terasa unik dan segar, bukan template yang bisa ditebak. Penilai memberi penilaian kreativitas eksplisit + alasannya (termasuk uji tebak: penilai menulis tebakannya atas bagian tengah sebelum membacanya, dan uji pembanding terhadap 2–3 video setopik). Naskah yang benar secara struktur tetapi generik = REVISI.
9. **Syarat dari skill naskah** — lembar janji bersih (semua `paid-off`/`answered` atau pengecualian beralasan disetujui); reader-sim tanpa titik bingung fatal; blok skor anti-slop 5 dimensi (Directness, Rhythm, Trust, Authenticity, Density) **≥35/50**; diagnosis tiga lapis lengkap (ekspresi → kalimat → logika-cerita), dinilai struktural lebih dulu, permukaan terakhir. (Butir 9 ini beserta syarat lampiran di Tahap 1 adalah integrasi baku **G-1..G-4** dari skill naskah — sudah diputuskan, bukan usulan: lembar janji + reader-sim sebagai lampiran wajib, cek struktural developmental sebelum skor permukaan, anotasi outcome/hook sebagai kolom wajib beatmap, dan pemeriksa mekanis anti-slop sebagai cek berkas terukur di gerbang ini.)

Aturan tambahan: tanpa vonis tertulis, tanpa produksi — termasuk naskah yang ditulis sebelum pipa ini dipakai. Karakter fiksi/IP pihak lain dilarang; tokoh publik nyata hanya sebagai karikatur generik untuk komentar/parodi berita publik, tanpa likeness fotorealistik dan tanpa klaim melampaui sumber.

### Cek Pra-Produksi — WAJIB sebelum Tahap 2, untuk video yang mengacu karya lain atau memakai metode/rute baru

Akar aturan ini: produksi penuh yang dibangun tanpa mengecek dulu cara acuan dibuat dan apakah mesin kita bisa menyamainya adalah kegagalan termahal yang pernah kami alami. Urutan ini tidak bisa dilompati:

1. **Bedah acuan:** cara produksi karya acuan disimpulkan per elemen visual (kelas mesin: volumetrik-3D / generatif / datar-vektor / foto / campuran); tiap simpulan berkelas bukti DATA atau DUGAAN. Tanpa bedah ini, metode produksi tidak boleh dipilih.
2. **Uji bukti satu beat:** beat paling berisiko gagal diproduksi lebih dulu dalam bentuk termurahnya (still / klip pendek / render uji), dengan aturan lulus **pra-terdaftar tertulis sebelum uji jalan**. Uji dinilai memakai Gerbang 2B.
3. **Produksi penuh hanya sesudah uji bukti LOLOS Gerbang 2B** dan dinyatakan lulus secara tertulis oleh [ISI: peran penentu lulus pra-produksi]. Uji gagal = ganti metode/rute, bukan memoles metode yang sama.

**Perlakuan proyek orisinal TANPA karya acuan (keputusan, mengikat):** bila proyek tidak mengacu karya lain, langkah 1 diganti **Deklarasi Kelas Visual Target**: dokumen singkat yang ditulis dan dikunci SEBELUM uji bukti, berisi (a) kelas render subjek utama yang ditargetkan (volumetrik-3D / datar-vektor / foto / campuran), (b) jangkar gaya yang dinyatakan sebagai kehadiran positif (palet, pencahayaan, framing, tekstur), dan (c) 3–5 frame jangkar yang dihasilkan sendiri pada uji bukti dan dinyatakan sebagai acuan internal proyek. Deklarasi ini mengambil alih seluruh peran "acuan" di pipa ini untuk proyek itu; uji bukti (langkah 2) tetap wajib dan dinilai terhadap deklarasi ini.

### Tahap 2 — Produksi (suara + klip)

Berjalan **voice-first**: suara final per beat + berkas beat-map (beat, teks, mulai, selesai, durasi terukur) diserahkan lebih dulu; gambar dirakit mengikuti beat-map — dilarang menebak durasi adegan dari perkiraan tempo baca.

**Pengecualian Jalur A (keputusan, mengikat):** untuk beat yang diproduksi lewat Jalur A skill `video-suara-bawaan` (dialog native yang lahir di dalam klip), voice-first TIDAK berlaku harfiah — tidak ada berkas suara final per beat yang bisa diserahkan sebelum gambar ada, karena durasi terukur beat baru lahir sesudah generate. Alur yang menggantikannya untuk Jalur A: (1) aturan lulus klip dipra-registrasi tertulis sebelum generate; (2) generate dari naskah yang LOLOS Gerbang 1; (3) beat-map final (beat, teks, mulai, selesai, durasi terukur) ditulis SESUDAH generate dari klip yang lolos audit, dan beat-map itulah yang mengikat Tahap 3 — untuk beat Jalur A, "audio final per beat" pada artefak keluar tahap ini adalah trek dialog di dalam klipnya. Kewajiban voice-first tetap berlaku penuh untuk semua jalur yang memisahkan suara dari gambar (narasi VO/TTS dan klip tanpa dialog native): di sana suara final + beat-map tetap diserahkan lebih dulu dan gambar mengikuti beat-map.

**Suara:**
- Narasi dihasilkan dari suara terkunci parameter proyek, dari naskah yang LOLOS Gerbang 1. Penyampaian wajib hidup (timing, penekanan, momen hidup) — suara datar yang membosankan = gugur walau natural.
- Konsistensi diperiksa di Gerbang 2 terhadap referensi kanonik paket kunci suara (uji dengar buta; patokan terukur kami: median F0 ±10%, tempo ±8% — kalibrasikan ke proyekmu).
- Bila adegan memakai dialog di dalam klip generatif (skill `video-suara-bawaan` Jalur A), dialog itu adalah trek audio klip itu sendiri dan tetap tunduk pada konsistensi + lisensi suara proyek.
- Musik + SFX hanya dari sumber bebas klaim (pustaka royalty-free platform / sintesis sendiri); sumber eksternal lain wajib verifikasi lisensi per berkas. Produksi menyerahkan **peta SFX per beat**: pilihan efek + timing per adegan + sumber/lisensi + level target relatif terhadap narasi. **Ambience bawaan klip (keputusan, mengikat):** bunyi latar yang lahir di dalam trek klip generatif (mis. hujan/badai pada klip Jalur A) bukan "pilihan efek" — ia tidak punya sumber/lisensi terpisah dan tidak punya level target terpisah. Di peta SFX ia dicatat sebagai baris tersendiri per klip (kelas: ambience bawaan klip; sumber: klip itu sendiri), dan levelnya dinilai sebagai bagian dari trek klipnya lewat loudness final + uji dengar, bukan terhadap pita level SFX; ia tidak dihitung dalam kepadatan SFX. Bila ambience itu dinaikkan, diturunkan, atau diganti secara terpisah di mix, barisnya berubah menjadi SFX biasa dan wajib memuat sumber/lisensi + level target seperti efek pilihan lain. Rantai mix loudness-first: narasi dinormalkan lebih dulu, gain SFX dihitung relatif terhadap narasi ternormalisasi, mix final dinormalkan ke standar loudness parameter proyek.

**Klip/gambar (skill `video-suara-bawaan` untuk bidikan generatif; skill `kemasan-video` untuk lapis kemasan):**
- Rute baku bidikan hero: **generatif per bidikan** (still generatif + image-to-video) dipadukan **lapis diagram/teks deterministik**. Gerak 2.5D di atas still hanya komponen, bukan rute hero mandiri.
- **Mekanik alat generatif (fakta alat, bukan target durasi):** satu panggilan generate menghasilkan satu klip **±10 detik**; maksimal **6 klip per putaran** pesan. Video utuh — berapa pun durasi target parameter proyek — dibangun sebagai rangkaian klip: petakan beat-map ke jumlah klip yang dibutuhkan (durasi target ÷ ±10 detik, dibulatkan mengikuti beat), teruskan konteks antar klip lewat `snapshot_id` hasil sebelumnya (`resume_from_snapshot_id`) supaya wajah, lokasi, dan gaya nyambung.
- Pencegahan slop sebelum generate (wajib, dari skill utama): teks dilarang di dalam frame; satu penutur, satu adegan per klip; tangan bukan subjek hero; hindari cermin/pantulan berteks dan kerumunan wajah; orientasi diminta eksplisit sesuai parameter format (untuk format vertikal, frasa teruji ada di skill utama).
- Setiap klip mentah melewati **audit klip** skill utama sebelum masuk kemasan: ekstrak frame bernama, cek orientasi terhadap parameter format, uji teks satu-satu (satu teks garbled = klip GAGAL untuk produksi), konsistensi wajah, uji mustahil, uji gerak, keberadaan + isi audio (isi dialog dinyatakan belum terverifikasi mesin bila tidak ada alat transkripsi — wajib cek dengar manusia).
- Karakter yang berbicara di layar: gerakan mulut digerakkan dari berkas isyarat lip-sync atas audio final (alat lip-sync adalah prasyarat proyekmu bila memakai karakter berbicara); animasi mulut berbasis timer/loop acak = REVISI otomatis di Gerbang 2.

**Artefak keluar tahap 2:** audio final per beat + beat-map + klip lolos audit + peta SFX per beat.

### Tahap 3 — Kemasan (skill `kemasan-video`)

- Gabung (stitch) klip menjadi video utuh mengikuti beat-map; tambahkan lapis deterministik: judul, caption, label, diagram — semua teks lahir di sini, dari teks pasti, mengikuti aturan caption proyekmu [ISI: aturan caption proyekmu].
- Satu tema kemasan terkunci per video: token dari berkas tema; lint QC desain (Impeccable `detect`) dijalankan pada berkas kemasan di tahap ini dan sekali lagi sebelum render final; temuan dinilai terhadap tema yang terkunci.
- **Lint vs artefak render (keputusan, mengikat):** lint menilai berkas HTML kemasan sebagai spek desain (token tema, tata letak, kontras). Bila artefak render aktual dibangun lewat jalur komposit deterministik non-HTML (mis. teks digambar dari berkas teks oleh mesin komposit proyek), teks yang dinilai di gerbang adalah teks pada berkas teks deterministik yang dipakai komposit itu sebagaimana terbaca di frame render — bukan teks yang tertulis di dalam HTML. Perbedaan teks apa pun antara berkas HTML dan berkas teks render adalah cacat kemasan tercatat (berlaku P-2 di Gerbang 2B) sampai diselaraskan; temuan lint atas token/desain HTML tetap berlaku penuh.
- Untuk pekerjaan yang menyerupai referensi tertentu: tulis spek gerak MOTION.md dari referensinya lebih dulu, ukur referensi menjadi angka (bible proyek), dan jalankan loop look-match dengan penilai segar yang tidak ikut membangun.
- Render pada mesin render parameter proyek, keluaran diarahkan ke disk besar; sebelum render final, naikkan keluaran mentah generatif (yang umumnya di bawah standar berkas) ke standar berkas parameter proyek (resolusi + frame rate).
- QA berkas pada setiap render final: deteksi frame hitam, deteksi frame beku, pemeriksaan kenyaringan — perintahnya ada di `references/look-match.md` skill kemasan.

**Artefak keluar tahap 3:** berkas video final + berkas bukti QC kemasan.

### GERBANG 2 — Penilaian akhir / QC (penilai ≠ pembuat video)

Video + suara TIDAK tayang sebelum lolos gerbang ini. Vonis: **LOLOS / REVISI / TOLAK**; aturan putaran revisi sama seperti Gerbang 1.

1. Hasil sesuai naskah yang lolos Gerbang 1 (tidak ada drift cerita/kata)?
2. Suara: sesuai paket suara terkunci, sinkron penuh dengan gambar dan caption (tidak ada delay), enak didengar untuk durasi penuh video, penyampaiannya kreatif, dan sama dengan suara tetap video-video sebelumnya?
3. Anti-AI-slop: karakter konsisten antar-frame, tidak ada artefak morphing/warping, gerakan bersih, ekspresi dan timing disengaja, bukan template generik, bukan slideshow.
4. Mutu gambar: line work/gaya konsisten **di dalam video itu sendiri** (antarvideo gaya boleh berbeda mengikuti topik/tren), resolusi dan frame rate sesuai standar berkas parameter proyek.
5. Penutup/loop sesuai aturan format proyekmu [ISI: aturan loop proyekmu, bila ada].
6. Judul, deskripsi, hashtag, dan disclosure konten AI terpasang benar?
7. Kreativitas: video terasa unik dan segar secara visual dan suara — terutama desain SFX (unik, on point terhadap gambar, timing presisi per adegan). Video yang rapi teknis tetapi generik = REVISI.

**Cek terukur (dibuktikan dari berkas, bukan rasa) — satu butir gagal = REVISI:**
- Sinkron: dinilai lewat salah satu dari dua rute bukti setara (keputusan di paragraf "Kesetaraan bukti ASR" sesudah daftar ini). Rute alignment: caption dan pemeriksaan sinkron memakai forced alignment tingkat kata; patokan lolos: onset beat/caption dalam ±33 ms (1 frame @30 fps) dari alignment. Rute ASR: untuk proyek tanpa alat forced alignment yang captionnya dibangun dari waktu kata ASR, patokan lolosnya adalah jendela bantalan caption yang dinyatakan di beat-map terhadap waktu kata ASR (bawaan kami: −0,15/+0,25 detik). Proyek menyatakan rutenya di catatan produksi sebelum gerbang ini; penilai tidak boleh menggagalkan butir sinkron hanya karena alat alignment tidak ada bila rute ASR dipenuhi dan dibuktikan.
- Berkas: resolusi + frame rate + durasi sesuai standar berkas parameter proyek dan beat-map (toleransi ±1 frame, INKLUSIF — selisih tepat 1 frame di kedua arah berada di dalam toleransi; butir ini gagal hanya pada selisih ≥ 2 frame); loudness sesuai standar parameter; kecocokan nama/angka/tanggal caption 100%, kata lain WER ≤ 2%.
- SFX: level tiap kelas SFX relatif terhadap puncak narasi ternormalisasi dalam pita parameter proyekmu [ISI: pita level SFX proyekmu; pita terukur kami: dampak ≤ −10 dB, halus −15..−20 dB, musik −18..−24 dB; kepadatan ≤1 SFX dampak per 4 detik]; peta SFX memuat sumber/lisensi + level target + fungsi; baris ambience bawaan klip dikecualikan dari kewajiban sumber/lisensi + level target dan dari hitungan kepadatan (keputusan di Tahap 2).
- Loop (bila format proyekmu memakai loop): untuk video <60 detik, hash frame awal = hash frame akhir wajib penuh; untuk durasi lebih panjang, cukup gema kalimat penutup + komposisi shot pembuka/penutup yang selaras.
- Uji dengar loop: penilai mendengarkan hasil final ≥5 putaran berturut-turut; suara/SFX yang menjadi annoying pada pendengaran berulang = REVISI, diperbaiki di sumbernya.

**Kesetaraan bukti ASR untuk butir sinkron (keputusan, mengikat):** patokan ±33 ms di atas mengandaikan forced alignment, tetapi pipa ini juga mengesahkan proyek yang captionnya dibangun dari waktu kata ASR. Untuk proyek seperti itu, bukti ASR dinyatakan SETARA dengan alignment untuk butir sinkron — proyek TIDAK wajib menambah alat alignment — dengan syarat kumulatif: (1) waktu kata berasal dari resep ASR skill utama (`faster-whisper`) dengan timestamp tingkat kata diaktifkan, dan waktu kata itu tersimpan sebagai data beat-timing proyek yang bisa diperiksa penilai; (2) dialog klip sudah lolos layar ASR di audit klip (WER ≤ 0,25); (3) beat-map menyatakan jendela bantalan caption yang dipakai proyek terhadap waktu kata ASR (bawaan: onset caption −0,15 s.d. +0,25 detik dari onset kata ASR pertama caption itu); (4) penilai mengukur onset SETIAP caption terhadap data beat-timing itu dan setiap onset jatuh di dalam jendela yang dinyatakan — satu caption di luar jendela = butir sinkron GAGAL. Bila ASR proyek tidak menghasilkan timestamp tingkat kata, rute ASR tidak tersedia: proyek memakai rute alignment, atau butir sinkron dinyatakan tidak bisa dibuktikan dan gerbang REVISI — butir ini tidak pernah LOLOS tanpa salah satu dari dua bukti itu. Rute yang dipakai wajib dicatat di vonis.

### GERBANG 2B — Kemiripan & kewajaran visual (bagian WAJIB Gerbang 2)

Menilai kemiripan terhadap acuan dan kewajaran visual — BUKAN kesesuaian terhadap daftar perbaikan. Dijalankan pada artefak termurah (still/klip uji/render uji) sebelum produksi penuh (lewat Cek Pra-Produksi), dan sekali lagi pada hasil final. **Satu butir material GAGAL = vonis gerbang GAGAL** (tidak ada "LOLOS dengan catatan" untuk butir K/W/P).

**Butir K — Kemiripan terhadap acuan:**
- **K-1 "Bandingkan Sebelah":** per beat hero, frame kandidat (awal/tengah/akhir beat) ditampilkan berdampingan dengan frame acuan setara pada ukuran penuh; vonis per beat MIRIP / BEDA-RINCI / BEDA-KELAS. Satu BEDA-KELAS pada beat hero = GAGAL.
- **K-2 "Uji Kelas Visual":** kelas render subjek utama kandidat wajib sama dengan acuan pada beat itu (volumetrik-3D / datar-vektor / foto / campuran); dicatat satu baris per frame sampel; ketidaksepakatan dua penilai = BEDA-KELAS.
- **K-3 "Uji Sepintas Telepon":** frame kandidat ditampilkan seukuran layar telepon ±3 detik ke penilai yang belum membaca catatan produksi; penilai menyebut subjek + kejadian; jawaban meleset dari maksud beat = GAGAL.

**Butir K pada proyek tanpa acuan eksternal (keputusan, mengikat):** bila proyek orisinal tanpa karya acuan, K-1 membandingkan frame kandidat terhadap **frame jangkar internal** dari Deklarasi Kelas Visual Target (per beat hero: frame jangkar untuk beat yang sama atau yang setara), dan K-2 menilai kelas render kandidat terhadap **kelas yang dideklarasikan** di deklarasi itu. **"Setara" (definisi, mengikat):** frame jangkar setara untuk sebuah beat bila memuat subjek yang sama, lokasi/latar yang sama, dan kelas visual yang sama dengan beat yang dinilai; frame jangkar dari beat lain hanya sah bila ketiga unsur itu terpenuhi. Bila beat hero memperkenalkan subjek atau lokasi yang belum punya frame jangkar setara, K-1 untuk beat itu dinilai terhadap frame jangkar subjek yang sama yang paling dekat (kontinuitas subjek + kelas terhadap Deklarasi) dan ketiadaan jangkar setara itu dicatat eksplisit di vonis — ketiadaan itu bukan BEDA-KELAS otomatis, dan bukan alasan melewatkan K-1. K-3 tidak berubah. Ketatnya setara, bukan longgar: satu BEDA-KELAS pada beat hero tetap = GAGAL, dan larangan "LOLOS dengan catatan" untuk butir K tetap berlaku penuh. Tanpa Deklarasi Kelas Visual Target yang terkunci, butir K tidak bisa dinilai dan gerbang GAGAL secara prosedural — "tidak ada acuan" tidak pernah menjadi alasan melewatkan atau melonggarkan butir K.

**Butir W — Kewajaran visual dasar:**
- **W-1 "Uji Kurungan":** setiap struktur internal (saraf/otak/organ) wajib sepenuhnya DI DALAM siluet tubuh pada SETIAP frame sampel. Toleransi nol: satu elemen menembus garis tubuh = beat GAGAL. Cek: perbesar 200% + telusur siluet; bila masker tersedia, uji piksel otomatis (piksel struktur di luar masker = 0).
- **W-2 "Uji Kenali Tanpa Label":** tutup semua teks/label pada frame sampel; penilai menamai tiap objek utama; objek yang hanya dikenali dari labelnya = GAGAL.
- **W-3 "Uji Mustahil":** daftar periksa per frame sampel — elemen berakhir di udara kosong; garis menyeberangi batas objek tanpa logika oklusi; objek saling menembus tanpa alasan fisik; anatomi di tempat mustahil; kontradiksi skala satu beat. Satu temuan = GAGAL.
- **W-4 "Uji Gerak Mustahil" (rute bergerak):** tonton beat pada 1× dan 0,25×; subjek hero berubah topologi/meleleh/berganti bentuk antar-frame = GAGAL.

**Butir P — Proses:**
- **P-1 "Penilai Bukan Produsen":** vonis ditandatangani sesi/pekerja yang berbeda dari produsen beat; catatan produksi produsen adalah bukti masukan, bukan vonis.
- **P-2 "Cacat Tercatat = Gerbang Gagal":** setiap cacat yang ditulis produsen sendiri di catatan produksi otomatis menggagalkan butir terkait sampai diperbaiki dan dicek ulang; cacat yang diketahui tidak boleh terbawa dalam vonis LOLOS.
- **P-3 "Frame Sampel Bernama":** vonis wajib menyebut nama berkas frame sampel yang diperiksa (per beat: awal/tengah/akhir + sekitar transisi); vonis dari menonton render sekali jalan tidak sah.

### Tahap 4 — Tayang

- Unggah **hanya bila Gerbang 1 + Gerbang 2 (termasuk 2B) LOLOS** dan semua kriteria terpenuhi. Tidak ada unggah "coba-coba".
- Dilakukan oleh peran wewenang tayang parameter proyek, yang mengatur judul/thumbnail/jadwal.
- Yang dikejar adalah kesegaran topik (tayang saat topiknya masih naik); jam posting adalah logistik, bukan sinyal peringkat.

## Peta rantai — skill mana di tahap mana

| Tahap | Skill / dokumen | Gerbang keluar |
|---|---|---|
| Naskah | `penjelasan-dan-cerita` | Gerbang 1 |
| Pra-produksi | dokumen ini (Cek Pra-Produksi) | Gerbang 2B atas uji bukti |
| Produksi klip & dialog | `video-suara-bawaan` | Audit klip (di dalam skill) |
| Kemasan & rakit | `kemasan-video` | QA berkas kemasan |
| Penilaian akhir | dokumen ini (Gerbang 2 + 2B) | Vonis LOLOS → tayang |
