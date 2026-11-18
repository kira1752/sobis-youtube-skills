# Penjelasan & Cerita

Skill menulis naskah video **per segmen/beat** dalam dua mode yang berbagi satu gerbang: **Mode PENJELAS** (nonfiksi informatif) dan **Mode CERITA** (fiksi terkompresi). **Durasi bukan identitas skill ini** — durasi adalah parameter proyek (lihat `PIPELINE.md` di akar repo ini): metode di sini bekerja per segmen dan diskalakan ke durasi target berapa pun, dari video pendek belasan detik sampai format panjang. Contoh terkerjakan di skill ini kebetulan berdurasi ±60 detik karena itulah format proyek penulis; kalibrasinya dinyatakan sebagai fungsi durasi, bukan angka mati. Skill ini lahir dari kegagalan terukur Episode 002 "Pintu Pesawat": naskahnya lolos penilai analitis internal (hook 8/8) tetapi divonis pemilik channel membingungkan, tidak menarik, dan berakhir awkward — karena tidak ada tahap yang mengukur apakah janji hook terbayar dan apakah pendengar pertama bisa mengikuti. Skill ini memasang dua pengukuran itu sebagai syarat lolos, ditambah lapisan anti-slop supaya naskah tidak terasa ditulis mesin.

Metodenya diadaptasi dari penilaian atas repo-repo penulisan (creative-writing-skills, story-skills, humanizer, stop-slop, oh-story) — atribusi dan lisensi lengkap ada di bagian Atribusi & lisensi di bawah. Teks metodenya teringkas utuh di skill ini dan berkas `references/`-nya; tidak ada berkas di luar repo ini yang perlu dibaca, dan tidak ada perangkat lunak atau CLI dari repo mana pun yang dipasang atau disalin.

## Pilih mode lebih dulu

- Topiknya fakta yang harus dijelaskan (mekanisme, sistem, angka, cara kerja benda) → Mode PENJELAS.
- Topiknya tokoh yang menginginkan sesuatu dan berusaha (maskot, karakter, situasi rekaan) → Mode CERITA.
- Campuran (fakta dibungkus tokoh): mode ditentukan oleh apa yang membawa durasi targetnya — bila penonton menunggu JAWABAN, itu PENJELAS; bila menunggu NASIB TOKOH, itu CERITA. Catat pilihan mode dan alasannya satu baris di kepala naskah.

## Prinsip yang mengikat kedua mode

- **Janji adalah utang tercatat, bukan kesan.** Setiap pertanyaan yang ditanam dan setiap janji yang diajarkan hook dicatat di lembar janji dan wajib terbayar di episode yang sama, atau tercatat sebagai pengecualian beralasan. Lihat [references/templat-lembar-janji.md](references/templat-lembar-janji.md).
- **Struktural dulu, permukaan terakhir.** Vonis soal janji, urutan informasi, dan fungsi beat diputuskan SEBELUM skor permukaan (detik hook, jumlah kata, loop). Jangan pernah memperbaiki masalah struktural dengan edit kalimat.
- **Penulis tidak menilai karyanya sendiri untuk vonis lolos.** Reader-sim wajib dijalankan agen yang terpisah dari penulis naskah. Penulis boleh menjalankan cek mekanis dan anti-slop atas tulisannya sendiri; vonis pengalaman pendengar tidak.
- **Suntingan gaya tidak boleh mengubah fakta.** Sesudah setiap putaran penulisan ulang (termasuk anti-slop), jalankan cek kehilangan fakta: nama, angka, dan klaim dibandingkan ke lembar fakta (PENJELAS) atau ke premis + registri (CERITA). Suntingan yang menghilangkan atau menambah klaim = cacat, bukan gaya. Jangan "membuat rasa manusia" dengan menambah mikro-aksi, umpatan, konflik, atau detail baru — itu mengarang, bukan menyunting (pagar dari story-deslop oh-story).
- **Satu-satunya penutup yang sah adalah bayaran.** Beat terakhir dilarang membuka pertanyaan baru. Penutup bertipe pertanyaan baru pada anotasi beatmap = REVISI otomatis, tanpa perlu perdebatan penilai.

## Mode PENJELAS — alur kerja

Kerjakan berurutan; jangan melompat ke penulisan sebelum langkah 2 selesai.

1. **Lembar fakta.** Setiap klaim naskah dipetakan ke baris fakta bersumber (praktik divisi yang sudah berlaku: FAKTA/TURUNAN dibedakan, sumber bernama). Naskah tidak boleh memuat klaim di luar lembar fakta.
2. **Lembar janji.** Isi templat di [references/templat-lembar-janji.md](references/templat-lembar-janji.md): pertanyaan hook dalam satu kalimat, tiap janji/pertanyaan dengan beat menanam dan beat membayar yang DIRENCANAKAN, dan daftar pengecualian beralasan (pola exemptions story-skills). Pola pengecualian untuk caveat: caveat atas klaim utama dicatat sebagai pengecualian dengan alasan tertulis, dan di naskah ia ditanam DAN dibayar di beat yang sama (lihat P8) — caveat tidak pernah menempati dua beat terakhir.
3. **Tulis dengan aturan P1–P9** (aturan penjelasan internal penulis, dirumuskan 2026-11-18 — teksnya mandiri dan utuh di sini):
   - **P1 — Sebut, tunjuk, baru jelaskan.** Objek disebut dengan nama bendanya dan ditunjukkan sebagai benda itu sebelum cara kerjanya dijelaskan. Penjelasan tidak mendahului penampakan.
   - **P2 — Satu kalimat, satu ide konkret.** Satu klausa utama per kalimat untuk beat penjelasan; kalimat >20 kata dilarang di paruh kedua video; subjek tidak diganti di tengah kalimat.
   - **P3 — Angka selalu berpasangan dengan terjemahan bendawi di kalimat yang sama.** Angka telanjang = cacat naskah.
   - **P4 — Eskalasi berantai jangkar.** Angka baru hanya dihitung dari benda langkah tepat sebelumnya yang sudah divisualkan. Dilarang melompat dua tangga; dilarang memperkenalkan benda baru dan angka baru di kalimat yang sama.
   - **P5 — Rumus utuh dalam satu beat, atau tidak sama sekali.** Tidak ada persamaan yang dirakit lintas beat; perhitungan tampil dan selesai dalam satu beat sebagai satu peristiwa.
   - **P6 — Checklist bayaran-janji di naskah.** Di kepala naskah tertulis: pertanyaan hook → bayaran per beat → bayaran final. Beat yang tidak bisa menamai bayarannya tidak lolos tulis.
   - **P7 — Penutup memanen, bukan membuka.** Kalimat terakhir hanya memakai bahan yang sudah ditanam; tanpa fakta baru, tanpa caveat, tanpa metafora yang belum ditanam di beat tengah.
   - **P8 — Caveat satu kalimat, di tengah, menempel klaimnya.** Batas klaim dinyatakan segera sesudah klaim yang dibatasinya, satu kalimat, dengan akibatnya sekalian. Rincian (nama, tanggal, sumber) turun ke deskripsi dan/atau label layar kecil. Dua beat terakhir bebas caveat secara mutlak.
   - **P9 — Uji sekali-dengar.** Sebelum gerbang, naskah dibacakan sekali tanpa gambar kepada pendengar segar; ia harus bisa mengulang "video ini bilang apa dan kenapa" dalam satu-dua kalimat. Di skill ini P9 dijalankan sebagai bagian dari reader-sim (langkah 6).
4. **Periksa failure modes penjelas** dengan [references/daftar-failure-modes.md](references/daftar-failure-modes.md): info-dumping, over-elaboration, emotional commentary, over-intensifying. Perbaiki yang ditemukan sebelum naik — keempatnya adalah penyakit penulis, bukan bahan perdebatan gerbang.
5. **Jalankan lapisan anti-slop** (bagian tersendiri di bawah) atas draf penuh.
6. **Anotasi beatmap.** Beri tiap beat tipe outcome dan fungsi bayarannya mengikuti [references/anotasi-beatmap.md](references/anotasi-beatmap.md). Reverse outline satu baris per beat (apa yang BENAR-BENAR dilakukan beat ini) wajib ditulis sebelum anotasi — ia yang menangkap beat yang membuktikan ulang kesimpulan yang sama.
7. **Reader-sim wajib** oleh agen terpisah, mengikuti [references/protokol-reader-sim.md](references/protokol-reader-sim.md): persona penonton awam sesuai parameter format proyekmu, batas pengetahuan dinyatakan, laporan momen-ke-momen. Syarat lolos ada di bagian Gerbang bersama.

## Mode CERITA — alur kerja

Ringkasan metode ada di [references/mode-cerita.md](references/mode-cerita.md); kerjakan berurutan.

1. **Premise workshop terkompresi** (adaptasi premise-workshop story-skills): tangkap spark apa adanya → hasilkan 8–12 what-if dari sudut berbeda (balik, naikkan biaya, pindah waktu/tempat, beri ke orang yang salah) → pilih 1–3 → susun logline (protagonis + want + obstacle + stakes) → uji logline (konflik tersirat? taruhan terbaca? bisa diceritakan dalam satu napas?) → namai taruhan. Skala taruhan mengikuti durasi target: untuk unit pendek cukup taruhan kecil yang konkret dan terasa (gengsi, kehilangan benda, janji ke tokoh lain); unit yang lebih panjang boleh menumpuk taruhan berlapis dan menaikkan skalanya — tetapi minimal satu level taruhan harus personal, bukan abstrak.
2. **Busur terkompresi (berskala terhadap durasi target):** hook → komplikasi → pergeseran tengah (midpoint shift: masalah berubah makna) → krisis/keputusan → resolusi yang membayar janji premis, dipecah per segmen (satu segmen = satu beat/adegan = satu unit produksi); jumlah segmen mengikuti durasi target, bukan sebaliknya. Proporsi tiap komponen terhadap durasi target ada di [references/mode-cerita.md](references/mode-cerita.md). Uji kausasi di setiap sambungan beat: sambungan harus bisa dibaca "therefore" atau "but"; sambungan yang hanya "and then" = beat diganti atau dibuang.
3. **Try-fail & scene-sequel terkompresi** (adaptasi scene-craft story-skills): isi tengah adalah siklus try-fail — usaha pertama berakhir `no`, usaha berikutnya `no-and` (gagal DAN keadaan memburuk) atau `yes-but` (berhasil TAPI berbiaya). Rangkaian `yes` bersih menguras tegangan; paling banyak satu `yes` bersih, dan tempatnya di awal sebagai kontras. Sebelum payoff, sisipkan satu beat sequel terkompresi: reaksi → dilema → keputusan, dalam satu beat.
4. **Registri setup→bayaran.** Pakai lembar janji yang sama dengan Mode PENJELAS ([references/templat-lembar-janji.md](references/templat-lembar-janji.md)) dengan jenis record "setup": setiap benda/kebiasaan/kalimat yang ditanam dan penonton berhak melihat bayarannya dicatat. Pengecualian seri (setup yang sengaja dibayar di episode berikutnya) DICATAT sebagai pengecualian beralasan — tidak pernah diselipkan diam-diam.
5. **Bible seri ringan.** Bila tokohnya berulang (maskot channel), perbarui berkas bible seri mengikuti [references/templat-bible-seri.md](references/templat-bible-seri.md): fakta karakter, keadaan terakhir, setup lintas episode yang masih terbuka. Bible dikelola manual sebagai satu berkas markdown per seri — bukan registri perangkat lunak.
6. **Lapisan anti-slop** sama seperti Mode PENJELAS (bagian di bawah), lalu **anotasi beatmap** ([references/anotasi-beatmap.md](references/anotasi-beatmap.md)) dan **reader-sim versi penonton cerita**: persona penonton yang baru pertama melihat tokoh ini; yang dilacak adalah pertanyaan yang dipegang, momen tertawa/tersentuh yang benar-benar tiba, dan momen perhatian melayang. Syarat lolos sama dengan Mode PENJELAS.

## Lapisan anti-slop — cek pra-reader-sim di kedua mode

Lapisan ini berjalan SESUDAH draf penuh dan SEBELUM reader-sim, di kedua mode. Daftar pola lengkap bergrada ada di [references/daftar-pola-anti-slop.md](references/daftar-pola-anti-slop.md); arsitektur pemeriksanya di [references/pemeriksa-mekanis.md](references/pemeriksa-mekanis.md). Prosedurnya (adaptasi humanizer):

1. **Pemeriksa mekanis lebih dulu.** Jalankan cek deterministik dua tingkat dari berkas rujukan pemeriksa: temuan **blocking** (kepadatan em-dash melewati ambang; penutup bertipe pertanyaan baru terdeteksi dari anotasi) wajib nol atau tercatat di daftar putih pengecualian; temuan **advisory** (kepadatan fragmen per beat, pembuka kalimat berulang, pembuka "So"/Wh-) dibaca dan diputuskan satu per satu. Pindai-ulang sesudah perbaikan maksimal 3 putaran. Nol temuan skrip TIDAK menggantikan pembacaan manusia — ia hanya membersihkan yang bisa dihitung.
2. **Tandai.** Penulis (atau pemeriksa permukaan) menandai tiap pola dari daftar bergrada di naskahnya sendiri. Bedakan derajatnya: **tell kuat** = bertindak pada satu temuan saja (false agency, kontras panggung yang menjawab keberatan yang tak pernah diajukan, sisa chatbot); **tell lemah-sendiri** = baru berarti bila berkelompok (fragmen dramatis, peredam bertumpuk, pembuka berulang) — kepadatan adalah sinyalnya, bukan keberadaannya. Perangkat genre yang DISENGAJA (fragmen tantangan hook, echo penutup, dash sebagai jeda delivery yang jarang dan disengaja) masuk daftar putih dengan alasan tertulis, mengikuti klausul humanizer bahwa pilihan sadar penulis mengalahkan pola.
3. **Tulis ulang** kalimat yang tertandai. Aturan unik stop-slop yang wajib dipakai di sini: **false agency** — benda/abstraksi mati tidak boleh diberi verba manusia ("Physics locks the door" → pelaku fisik yang sebenarnya: "Pressure locks the door"); **cut quotables** — kalimat yang terdengar seperti pull-quote ditulis ulang kecuali ia membawa fakta; dua benda lebih baik daripada triad paksa ("two items beat three").
4. **Cek kehilangan fakta.** Bandingkan naskah hasil tulis-ulang ke lembar fakta / premis baris demi baris. Nama, angka, arah klaim tidak boleh berubah.
5. **Baca keras.** Untuk pipa voice-first kita, baca-keras = dengarkan render VO drafnya (atau bacakan dengan suara normal bila VO belum ada). Kalimat yang hanya enak dibaca diam tetapi tersandung di mulut = revisi. Sesudah langkah ini naskah baru boleh naik ke reader-sim.

**Skor stop-slop wajib.** Laporan gerbang (kedua mode) wajib memuat blok skor 5 dimensi dari [references/protokol-reader-sim.md](references/protokol-reader-sim.md): Directness, Rhythm, Trust, Authenticity, Density — masing-masing 1–10. Total **<35/50 = REVISI**, berapa pun vonis lain. Skor diberikan penilai gerbang, bukan penulis. (Preseden: naskah asli Episode 002 dinilai 29/50 oleh penilaian repo tulis — Rhythm 4, Authenticity 4 — dan vonis itu konvergen dengan vonis pemilik channel dari arah yang sepenuhnya berbeda.)

## Gerbang bersama — syarat lolos

Naskah LOLOS hanya bila SEMUA terpenuhi; satu gagal = REVISI dengan alasan tertulis yang menunjuk syaratnya:

1. **Lembar janji bersih.** Semua janji berstatus `paid-off` dan semua pertanyaan `answered` di dalam episode yang sama, ATAU tercatat sebagai pengecualian beralasan yang disetujui penilai. Tidak ada pertanyaan ditanam sesudah ±70% durasi tanpa bayaran di episode itu.
2. **Reader-sim tanpa titik bingung fatal.** Laporan reader-sim (agen terpisah dari penulis) tidak memuat: titik bingung yang tak terjawab sampai akhir, pertanyaan terakhir di kepala penonton yang yatim (bukan janji hook yang terbayar), atau kegagalan uji sekali-dengar (P9, Mode PENJELAS) / kegagalan menyebut kembali taruhan dan hasil akhir tokoh (Mode CERITA).
3. **Anotasi beatmap sah.** Penutup bertipe `resolution`/`emotional` yang membayar janji awal — penutup bertipe `question` baru = REVISI otomatis. Tidak ada beat tanpa fungsi bernama (bayaran parsial, tanam, atau perubahan model penonton/keadaan tokoh).
4. **Blok skor anti-slop ≥35/50** dan temuan blocking pemeriksa mekanis = 0 di luar daftar putih tercatat.
5. **Diagnosis tiga lapis lengkap** di laporan gerbang, mengikuti struktur [references/protokol-reader-sim.md](references/protokol-reader-sim.md): lapis **ekspresi** (permukaan: pola anti-slop, dash, fragmen), lapis **kalimat** (pemakaian: fokus, tebal-tipis uraian, fungsi tiap beat), lapis **logika-cerita** (kausalitas + urutan siapa-tahu-apa / urutan pengungkapan). Naskah bisa bersih di lapis pertama dan tetap gugur di lapis ketiga — Episode 002 adalah presedennya.

Urutan penilaian gerbang: lapis logika-cerita dan lembar janji dinilai PERTAMA (struktural), baru lapis kalimat, terakhir lapis ekspresi dan skor permukaan. Jangan membalik urutan ini.

## Contoh terkerjakan

Dua uji bukti dari laporan penilaian repo cerita, dengan atribusi metode per bagian:

- [references/contoh-penjelas-ep2.md](references/contoh-penjelas-ep2.md) — tulis-ulang penuh penjelasan Episode 002 (registri janji, naskah 9 beat, catatan metode per perubahan) + ringkasan hasil lapisan anti-slop atas naskah yang sama dari penilaian repo tulis.
- [references/contoh-cerita-robi.md](references/contoh-cerita-robi.md) — mikro-fiksi "ROBI DAN KOTAK YANG TIDAK MAU PINDAH": premis hasil workshop, registri setup, 8 beat tertulis, penilaian jujur batas buktinya.

## Integrasi ke pipa (BAKU — bukan usulan)

Empat butir integrasi berikut **sudah diputuskan dan berlaku sebagai rantai baku** (keputusan penanggung jawab pipa, 2026-11-18). Substansinya hidup di `PIPELINE.md` di akar repo ini (Tahap 1 + Gerbang 1), dan skill ini adalah acuan metodenya:

- **G-1 (BAKU):** Gerbang 1 mensyaratkan untuk semua format: (a) lembar janji bersih sebagai lampiran wajib naskah, (b) laporan reader-sim oleh agen terpisah dari penulis sebagai lampiran wajib, dengan blok skor anti-slop ≥35/50 dan diagnosis tiga lapis.
- **G-2 (BAKU):** Rubrik Gerbang 1 memuat tiga baris cek struktural developmental (premise & promise; fungsi per beat; information design) yang diputuskan sebelum skor permukaan.
- **G-3 (BAKU):** Anotasi outcome/hook per beat adalah kolom wajib format beatmap naskah, dengan aturan penutup bertipe pertanyaan baru = REVISI otomatis.
- **G-4 (BAKU):** Pemeriksa mekanis anti-slop (em-dash + kepadatan fragmen) adalah cek berkas terukur di Gerbang 1, sejajar dengan cek durasi dan jumlah kata.

Naskah yang belum memenuhi keempatnya belum boleh naik ke produksi, berapa pun vonis parsial yang sudah ia kumpulkan.

## Atribusi & lisensi

Hanya teks metode yang diadaptasi; tidak ada perangkat lunak, CLI, atau berkas kata dari repo sumber yang disalin atau dipasang.

- **haowjy/creative-writing-skills** — Apache License 2.0. Diadaptasi: reader-sim (protokol simulasi pendengar pertama), writing-principles (kanal rasa penasaran + failure modes: info-dumping, over-elaboration, emotional commentary, over-intensifying), story-review/developmental-edit (premise & promise, scene function, information design), story-architecture (uji kausasi therefore/but, busur terkompresi, setup/payoff dilacak eksplisit).
- **danjdewhurst/story-skills** — MIT License. Diadaptasi: plot-structure (registri janji/pertanyaan + siklus hidupnya, pengetikan outcome & hook, peringatan pacing), premise-workshop (spark→what-if→logline→taruhan), scene-craft (try-fail, scene-sequel), revision-continuity (reverse outline, tangga revisi bernama — dipakai ringan), gagasan registri karakter/kontinuitas seri (diperkecil jadi bible markdown manual).
- **blader/humanizer** — MIT License. Diadaptasi: daftar pola AI-tells bergrada (kuat vs lemah-sendiri) berbasis Wikipedia "Signs of AI writing", prosedur tandai→tulis ulang→cek kehilangan fakta→baca keras, klausul perangkat disengaja, adaptasi em-dash untuk naskah suara.
- **hardikpandya/stop-slop** — MIT License. Diadaptasi: rubrik skor 5 dimensi (Directness/Rhythm/Trust/Authenticity/Density, ambang <35/50), aturan false agency, "cut quotables", "two items beat three".
- **worldwonderer/oh-story-claudecode** — MIT License. Diadaptasi sebagai KONSEP (bukan berkas): arsitektur pemeriksa deterministik dua tingkat (blocking/advisory + daftar putih + pindai-ulang maks 3) dari story-deslop, diagnosis tiga lapisnya （表达/用笔/故事 → ekspresi/kalimat/logika-cerita), dan pagar "jangan mengarang rasa manusia". Katalog pola dan leksikon Mandarinnya TIDAK diambil.
- **Aturan P1–P9** adalah aturan internal penulis sendiri (dirumuskan 2026-11-18), bukan dari repo luar.
