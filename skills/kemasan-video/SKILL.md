# Kemasan Video

## Titik serah intake — klip apa yang boleh masuk kemasan

- Kemasan hanya menerima klip berstatus LOLOS audit klip skill utama (QC-1 pada rantai skill `video-suara-bawaan`) untuk produksi generatif, atau LOLOS Gerbang 2B atas artefak-uji untuk rute lain. Klip mentah generatif tidak pernah masuk komposisi "untuk dilihat dulu".
- Teks apa pun yang terbaca di komposisi akhir wajib dapat ditelusur ke berkas kemasan deterministik (HTML/komposisi), bukan ke frame klip — bila ada teks terbaca yang sumbernya frame klip, itu temuan QC-1 yang terlewat dan dikembalikan ke tahap itu, bukan ditambal di kemasan.

## Periksa kemasan dengan Impeccable

- Jalankan detect Impeccable pada setiap berkas HTML kemasan (kartu judul, caption, diagram, overlay) di Gerbang 1 dan sekali lagi di Gerbang 2 sebelum render final. (Gerbang 1 dan Gerbang 2 didefinisikan di `PIPELINE.md` di akar repo ini.)

- **Hubungan lint dengan artefak render (keputusan, mengikat):** berkas HTML yang di-lint adalah spek desain (token tema, tata letak, kontras) — belum tentu artefak render aktual. Bila render aktual dibangun lewat jalur komposit deterministik non-HTML (mis. teks digambar dari berkas teks oleh mesin komposit), judul/subjudul/caption yang dinilai adalah yang ada di berkas teks render itu dan terbaca di frame hasil — BUKAN yang tertulis di HTML. Teks HTML yang berbeda dari teks render adalah cacat kemasan tercatat sampai diselaraskan; jangan menilai kebenaran teks dari HTML yang tidak ter-render, dan jangan menganggap lint bersih atas HTML sebagai bukti teks render benar.

- Pakai perintah npx sebagai jalur utama dan simpan keluarannya sebagai bukti:

  `npx --yes impeccable detect <berkas.html> --json > <berkas>-impeccable.json`

- Catat versi Impeccable yang benar-benar berjalan di bukti gerbang — versi dari npx bisa bergerak antar-run. Kalibrasi penulis repo ini memakai versi terpaku 4.9.2; bila konsistensi antar-run penting bagi proyekmu, paku versi yang sama di perintahmu (mis. `npx --yes impeccable@4.9.2 detect ...`) dan jangan ganti di tengah seri tanpa mencatatnya.

- Baca keluaran sebagai larik JSON. Setiap temuan membawa bidang antipattern, severity, category, file, dan snippet. Hitung jumlah temuan dan kelompokkan menurut antipattern sebelum menilai.

- Perlakukan kode keluar 2 sebagai tanda ada temuan, bukan kegagalan alat. Kode itu teramati pada uji kami setiap kali temuan dilaporkan dan JSON tetap lengkap.

- Bandingkan dengan tolok ukur teruji kami. Kartu judul bawaan agen tanpa arahan menghasilkan 9 temuan, yaitu low-contrast 3, gradient-text 2, icon-tile-stack, oversized-h1, overused-font, dan ai-color-palette. Kartu yang sama dengan token tema Blueprint terkunci menghasilkan 2 temuan.

- Nilai temuan terhadap tema yang terkunci sebelum memperbaikinya. Temuan codex-grid-background pada tema Blueprint adalah positif palsu sebagian, karena tema itu mengizinkan grid di bawah gambar.

- Arsipkan berkas JSON hasil detect di samping bukti gerbang video itu.

- Larang mode live dan perintah Apply dari Impeccable dalam keadaan apa pun. README proyeknya sendiri menyatakan mode Apply dapat menjalankan CLI agen dengan persetujuan dan sandbox dimatikan. Skill ini hanya memakai detect dan CLI.

## Kunci satu tema Hallmark per video

- Minta penentu tema proyekmu (peran yang kamu tetapkan di parameter proyek — pemilik channel atau yang mewakilinya) memilih satu tema Hallmark sebelum pekerjaan kemasan dimulai dan tulis nama tema itu di catatan desain episode.

- Ambil token dari berkas tema, bukan dari ingatan. Seluruh pustaka tema Hallmark (50 tema, lisensi MIT) tersalin di skill ini pada [references/themes/](references/themes/) — lihat [references/themes/INDEX.md](references/themes/INDEX.md). Tema yang sudah teruji penulis, Blueprint, ada di [references/themes/blueprint.md](references/themes/blueprint.md).

- Salin blok token `:root` dari berkas tema ke komposisi kemasan dan pakai hanya token itu untuk kertas, tinta, font, radius, dan garis. Jangan mencampur token dari dua tema dalam satu video.

- Ganti font yang dinamai tema dengan font dari folder font lokal proyekmu bila font tema tidak terpasang di mesinmu dan catat penggantiannya di catatan desain. (Contoh kalibrasi penulis: Blueprint menamai Chakra Petch dan IBM Plex Mono yang tidak terpasang di mesin penulis; uji penulis memakai Alumni Sans, Albert Sans, dan JetBrains Mono dari folder font lokal proyek penulis.)

- Jangan mengimpor seluruh skill Hallmark dan jangan memakai sloplint sebagai QC kita. Separuh gerbang sloplint menilai halaman web dan tidak punya padanan di frame video. QC kemasan tetap Impeccable dari bagian sebelumnya.

- Ingat batas token tema. Token tidak menyelesaikan komposisi, dan kartu uji kami masih menyisakan descender terpotong serta pita kosong besar sesudah token diterapkan. Pemeriksaan mata dan Impeccable tetap wajib.

## Tulis spesifikasi gerak dengan format MOTION.md

- Tulis satu berkas MOTION.md untuk setiap video referensi yang dipelajari, pada tahap beatmap atau storyboard, sebelum mesin render dipilih.

- Ikuti format di [references/motion-md.md](references/motion-md.md). Berkas rujukan itu berisi anatomi format, templat kosong, dan satu contoh terisi penuh.

- Isi tabel beat dengan tiga kolom wajib, yaitu rentang waktu di potongan, gerak referensi yang dipertahankan, dan adaptasi kita atas beat itu.

- Tulis gerak sebagai perbuatan yang terlihat, bukan kata sifat. Perintah seperti menekan pil di tengah bisa dibangun ulang, sedangkan kata seperti premium tidak.

- Akhiri berkas dengan tautan ke komposisi yang bisa diedit, film hasil, dan video perbandingan berdampingan begitu film pertama ada.

- Cantumkan sumber formatnya di laporan pekerjaan. Format ini diadaptasi dari OpenMotion yang berlisensi Apache-2.0. Aplikasi OpenMotion tidak diadopsi dan tidak perlu dipasang.

## Samakan look dengan loop look-match

- Jalankan loop look-match setiap kali pekerjaan diminta menyerupai referensi tertentu. Langkah lengkap, perintah QA, dan gotcha ada di [references/look-match.md](references/look-match.md).

- Ukur referensi menjadi angka lebih dulu, satu analis per topik, lalu kunci angka itu sebagai bible proyek sebelum membangun.

- Nilai hasil dengan penilai segar yang tidak ikut membangun, memakai lembar berdampingan dan skor per area dari 10, lalu petakan setiap perbaikan ke pemilik berkasnya.

- Jalankan QA frame pada setiap render final, yaitu deteksi frame hitam, deteksi frame beku, dan pemeriksaan kenyaringan, dengan perintah ffmpeg di berkas rujukan.

- Beri setiap hold dorongan masuk perlahan. Hold datar terbaca sebagai frame beku oleh QA dan oleh penonton.

- Atur TEMP dan TMPDIR ke disk besar sebelum render Remotion apa pun. Bundle Remotion menyalin folder public ke temp dan tidak menghapusnya, dan kelalaian ini pernah menghabiskan 60 sampai 110 GB.

- Buang dua aturan tampilan proyek sumber metode ini. Caption mengikuti aturan caption proyekmu dan ekspor mengikuti standar berkas proyekmu — keduanya parameter proyek (lihat `PIPELINE.md` di akar repo ini), bukan angka warisan dari proyek sumber maupun dari penulis repo ini.

## Render kemasan dengan HyperFrames hanya untuk A/B bergerbang

- Perlakukan HyperFrames sebagai calon mesin kemasan, bukan jalur produksi. Pakai hanya untuk A/B bergerbang melawan mesin render baku proyekmu, pada adegan judul, caption, diagram, dan 2.5D. Jangan mengubah dokumen pipa produksi berdasarkan skill ini.

- Atur lingkungan sebelum perintah apa pun, dengan direktori proyekmu sendiri:

  `export HYPERFRAMES_CACHE_DIR=<direktori-cache-privat-di-disk-besar>`
  `export TMPDIR=<direktori-temp-di-disk-besar>`

- Hormati alasan di balik resep itu. CLI menolak cache di bawah direktori home yang mode grupnya longgar (di mesin penulis home ber-mode grup 2770), jadi cache harus di direktori privat berinduk privat. TMPDIR harus di disk yang besar karena `/tmp` bisa berupa tmpfs kecil (di mesin penulis 512 MB). Di mesin penulis, cache teruji terisi unduhan Chrome Headless Shell sekitar 263 MB — sediakan ruang untuk itu.

- Vendor GSAP ke dalam proyek sebelum render. Scaffold memuat GSAP dari CDN dan render harus deterministik tanpa jaringan. Unduh `gsap.min.js` sekali ke folder proyek, dengan versi teruji 3.15.0, dan rujuk berkas lokal itu dari komposisi.

- Jaga keluaran render di disk besar. Pemeriksaan ruang kosong renderer membaca lokasi keluaran, dan proyek yang tinggal di `/tmp` gagal dengan pesan ruang disk rendah walau TMPDIR sudah benar. Arahkan keluaran dengan opsi `-o` ke disk besarmu bila proyek harus tinggal di tempat lain.

- Jalankan `npm run check` sesudah setiap perubahan komposisi dan perbaiki semua error sebelum render. Skrip proyek memaku `hyperframes@0.9.63`. Render dengan `npm run render` atau `npx --yes hyperframes@0.9.63 render -o <path-keluaran>`.

- Baca hasil check sebagai bukti Gerbang 2. Check mengambil sampel timeline dan menandai pelanggaran zona aman platform (TikTok, Reels, Shorts) serta teks di bawah lantai 28 px — nilai temuannya terhadap format dan standar berkas parameter proyekmu, bukan sebagai hukum universal.

- Patuhi kontrak komposisi yang teruji. Setiap elemen berwaktu membawa `data-start`, durasi, dan class `clip`. Satu timeline root yang berhenti terdaftar di `window.__timelines` untuk setiap id komposisi. Logika harus deterministik, tanpa `Date.now()`, tanpa `Math.random()`, dan tanpa fetch jaringan.

- Baca satu frame hasil render sebelum menyerahkan, memakai perintah ambil frame ffmpeg di [references/look-match.md](references/look-match.md). Check yang lulus tidak menunjukkan tampang frame.

- Kalibrasikan harapan waktu. Angka berikut adalah kalibrasi mesin penulis, bukan patokan mesinmu: render klip 5 detik memakan sekitar 2 sampai 3 menit, dengan compile sekitar 69 sampai 74 detik dan capture GPU software yang berayun antara sekitar 1,8 dan 4,2 fps antar run. Lapisan kemasan film 57 detik terekstrapolasi kasar menjadi 15 sampai 20 menit di mesin itu.

- Jangan memasang skill HyperFrames dan jangan memakai fitur Pro berbayarnya. Skill ini hanya memakai CLI dan resep di atas.
