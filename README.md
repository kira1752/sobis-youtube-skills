# Sobis YouTube Skills

Skill kustom untuk agen AI (Muse) — satu pipa produksi video yang utuh: menulis naskah, menghasilkan klip generatif, dan mengemas video, dengan gerbang mutu anti-slop di setiap tahap. Dibagikan apa adanya dari sistem produksi internal kami, dan sudah dibersihkan supaya bisa langsung dipakai Muse lain: dokumen pipanya disertakan, keputusan khas channel kami diubah menjadi parameter yang kamu isi sendiri, dan tidak ada durasi atau format yang dikunci — durasi adalah parameter proyekmu.

**Baca `PIPELINE.md` lebih dulu.** Dokumen itu tulang punggung rantainya: tahap-tahap, gerbang (Gerbang 1, Gerbang 2, Gerbang 2B), syarat serah antar-tahap, dan tabel parameter proyek yang wajib kamu isi sebelum produksi pertama. Ketiga skill di bawah merujuk tahap dan gerbang yang didefinisikan di sana.

## Isi

### `PIPELINE.md` — dokumen pipa (tulang punggung)

Rantai lengkap: Naskah → Gerbang 1 → Cek Pra-Produksi → Produksi → Kemasan → Gerbang 2 + 2B → Tayang. Memuat prinsip yang mengikat (janji adalah utang tercatat; penilai bukan produsen; teks terbaca lahir di lapis deterministik, tidak pernah digambar model) dan butir-butir gerbang yang terukur.

### `skills/penjelasan-dan-cerita` — naskah video per segmen, anti-slop

Menulis naskah dalam dua mode yang berbagi satu gerbang mutu. Durasi bukan sifat skill ini: jumlah kata, proporsi busur, dan ambang pemeriksa dinyatakan sebagai fungsi durasi target proyekmu.

- **Mode PENJELAS** — nonfiksi informatif: lembar fakta, lembar janji (promise ledger), aturan penjelasan P1–P9, daftar failure modes.
- **Mode CERITA** — fiksi terkompresi: premis, kausalitas therefore/but, try-fail, scene-sequel, registri setup.

Syarat lolos gerbang: reader-sim oleh agen yang **berbeda** dari penulis + lembar janji bersih + skor stop-slop 5 dimensi (Directness, Rhythm, Trust, Authenticity, Density) — total <35/50 = revisi. Termasuk `references/daftar-pola-anti-slop.md`, daftar periksa pola tulisan mesin yang harus dihindari, dan pemeriksa mekanis (resep `python3` inline, tanpa dependensi).

### `skills/kemasan-video` — kemasan visual video

Mengemas judul, caption, dan diagram hasil render kode dengan satu tema Hallmark yang terkunci, lint QC Impeccable di gerbang, spek gerak MOTION.md, dan loop look-match terukur terhadap acuan. Seluruh pustaka tema Hallmark (50 tema, MIT) tersalin di `references/themes/`; tema teruji yang kami pakai: Blueprint.

### `skills/video-suara-bawaan` — mesin generate utama pipa

Mengemas kemampuan generatif bawaan Muse sendiri: video generatif dengan dialog native (terbukti natural berbahasa Indonesia) sebagai inti, dan TTS bawaan sebagai jalur narasi pendukung. Memuat peta rantai pipa + syarat serah antar-tahap, pola produksi multi-klip (satu klip ±10 detik adalah batas alat, bukan batas durasi video — video utuh dirakit dari banyak klip), aturan pencegahan AI slop sebelum generate (larang teks di dalam frame, satu penutur), dan audit ketat frame-per-frame yang wajib lolos sebelum hasil generate ditunjukkan ke pemilik channel. Orientasi adalah parameter format proyekmu: skill ini membawa frasa prompt vertikal yang teruji, dan auditnya menilai kesesuaian orientasi dengan format yang kamu pilih. Lahir dari pelajaran mahal: cek kemampuan bawaan agenmu dulu sebelum berminggu-minggu menguji engine eksternal.

## Cara pasang

1. Salin ketiga folder di `skills/` ke direktori skill kustom Muse tujuan (di Muse: `~/workspace/custom-skills/`):
   - `skills/penjelasan-dan-cerita/`
   - `skills/kemasan-video/`
   - `skills/video-suara-bawaan/`
2. Salin juga `PIPELINE.md` ke tempat yang bisa dibaca agenmu (mis. folder proyek videomu) — dokumen itulah tulang punggung rantainya; ketiga skill merujuk tahap dan gerbang yang didefinisikan di sana.
3. Jangan pisahkan berkas di `references/` dari skill induknya; itu bahan wajib, bukan lampiran opsional.

## Prasyarat alat

**Bawaan produk Muse (ada di setiap Muse; tidak perlu dipasang):**
- Generate video & gambar generatif (`media.generate_video` / `media.generate_image`) — dipakai skill `video-suara-bawaan`. Mekaniknya: ±10 detik per klip, maksimal 6 klip per putaran pesan.
- CLI `tts` Muse (`tts speak`, `tts synthesize-script`) — jalur narasi pendukung di skill yang sama.

**Alat sistem (pasang di mesinmu; skill mengasumsikan perintah ini ada di PATH):**
- `ffmpeg` + `ffprobe` — ekstrak frame, cek orientasi/resolusi, QA berkas (frame hitam/beku, loudness), ukur durasi beat.
- `node` + `npm`/`npx` — menjalankan lint kemasan Impeccable (`npx --yes impeccable detect <berkas.html> --json`) dan proyek render.
- `python3` — resep pemeriksa mekanis anti-slop di `penjelasan-dan-cerita/references/pemeriksa-mekanis.md` (skrip inline, tanpa dependensi tambahan).

**Alat proyekmu sendiri (disebut pipa, tidak disediakan repo ini):**
- Proyek render kemasan (kami memakai Remotion; atur `TEMP`/`TMPDIR` ke disk besar sebelum render — bundle render menyalin folder aset ke temp dan bisa menghabiskan puluhan GB).
- Alat forced alignment tingkat kata untuk hakim sinkron Gerbang 2 (kami memakai WhisperX), dan alat lip-sync bila memakai karakter berbicara di layar (kami memakai Rhubarb).
- Font lokal untuk tema kemasanmu bila font yang dinamai tema tidak terpasang di mesinmu — catat penggantiannya di catatan desain.

## Cara Muse baru menjalankan rantai ujung-ke-ujung hanya dari repo ini

1. Baca `PIPELINE.md` lebih dulu. Isi **tabel parameter proyek** di kepalanya (durasi target, format/platform, standar berkas, bahasa, suara terkunci, tema, mesin render, wewenang tayang) dan simpan sebagai berkas parameter proyekmu.
2. **Naskah:** minta agen menjalankan skill `penjelasan-dan-cerita` atas topikmu. Keluaran wajib: naskah + lembar fakta + lembar janji + anotasi beatmap. Lalu jalankan **reader-sim oleh agen/sesi yang berbeda** dari penulisnya.
3. **Gerbang 1:** agen penilai (bukan penulis) menilai naskah dengan kriteria Gerbang 1 di `PIPELINE.md`. Tanpa vonis LOLOS tertulis, jangan produksi.
4. **Pra-produksi (bila mengacu karya lain / rute baru):** bedah acuan + uji bukti satu beat termurah, dinilai Gerbang 2B. Produksi penuh hanya sesudah lulus tertulis.
5. **Produksi:** voice-first — hasilkan audio final per beat + beat-map (durasi terukur ffprobe). Lalu hasilkan klip per beat dengan skill `video-suara-bawaan` (pencegahan slop SEBELUM generate; teruskan konteks antar klip lewat `snapshot_id`; jumlah klip = durasi targetmu dibagi ±10 detik, digenerate ≤6 klip per putaran). Audit setiap klip mengikuti langkah audit di skill itu sebelum lanjut.
6. **Kemasan:** rakit dengan skill `kemasan-video` — stitching klip, lapis teks/diagram deterministik, satu tema terkunci, lint Impeccable, naikkan keluaran ke standar berkas parametermu, QA berkas (frame hitam/beku/loudness).
7. **Gerbang 2 + 2B:** agen penilai (bukan pembuat video) menjalankan seluruh cek Gerbang 2 dan butir K/W/P Gerbang 2B atas bukti bernama. Satu butir material gagal = REVISI, putar sampai LOLOS.
8. **Tayang:** hanya peran wewenang tayang yang mengunggah, hanya sesudah Gerbang 1 + 2 LOLOS.

## Yang wajib disesuaikan pemakai (jangan pakai bawaan kami mentah-mentah)

- **Suara terkunci** — ID suara + resep + engine + lisensi di lembar kunci suaramu. Suara maskot channel kami yang tertulis sebagai contoh di skill adalah milik channel kami; pilih dan kunci suaramu sendiri lewat audisi, dan pastikan engine-nya aman untuk pemakaian komersial.
- **Bahasa channel** — bahasa utama video + kebijakan trek bahasa. Contoh dialog/narasi di skill banyak berbahasa Indonesia dan Inggris karena channel kami dwibahasa; sesuaikan.
- **Durasi & format** — tidak ada durasi bawaan. Skill naskah lahir dari praktik video pendek kami, tetapi metodenya bekerja per segmen/beat untuk durasi berapa pun; tetapkan durasi target + platform + orientasi + standar berkas (resolusi/fps/loudness) sebagai parameter proyekmu.
- **Tema kemasan** — 50 tema Hallmark tersalin di `kemasan-video/references/themes/`; yang teruji oleh kami hanya Blueprint. Kunci temamu sendiri per video/seri.
- **Peran & wewenang** — dokumen kami menyebut peran generik (penulis, penilai, pemilik channel, peran wewenang tayang). Petakan ke strukturmu: siapa menulis, siapa menilai (wajib orang/sesi berbeda), siapa berhak memutuskan tayang.
- **Contoh di `references/`** — memakai nama episode dan konteks channel kami (mis. contoh Episode 002 dan cerita maskot kami). Metodenya berlaku umum; ganti contohnya dengan materimu bila membingungkan agenmu.

## Catatan

- Skill ini lahir dari kegagalan nyata (naskah yang lolos penilai analitis tetapi divonis penonton pertama membingungkan) — gerbangnya sengaja mengukur apa yang dulu tidak diukur: janji hook terbayar + pendengar pertama bisa mengikuti.
- Beberapa contoh di `references/` memakai nama episode dan konteks channel kami; metodenya berlaku umum, contohnya tinggal diganti.
- Lisensi tema pihak ketiga yang dirujuk (Hallmark) adalah MIT, sesuai sumbernya; berkas temanya tersalin di repo ini dengan atribusi di `skills/kemasan-video/references/themes/INDEX.md`.
