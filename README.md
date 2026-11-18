# Sobis YouTube Skills

Skill kustom untuk agen AI (Muse) dari Divisi YouTube kami — dipakai untuk menulis naskah Shorts dan mengemas video dengan gerbang mutu anti-slop. Dibagikan apa adanya dari sistem produksi internal kami.

## Isi

### `skills/penjelasan-dan-cerita` — naskah Shorts ±60 detik, anti-slop

Menulis naskah dalam dua mode yang berbagi satu gerbang mutu:

- **Mode PENJELAS** — nonfiksi informatif: lembar fakta, lembar janji (promise ledger), aturan penjelasan P1–P9, daftar failure modes.
- **Mode CERITA** — fiksi mikro terkompresi: premis, kausalitas therefore/but, try-fail, scene-sequel, registri setup.

Syarat lolos gerbang: reader-sim oleh agen yang **berbeda** dari penulis + lembar janji bersih + skor stop-slop 5 dimensi (Directness, Rhythm, Trust, Authenticity, Density) — total <35/50 = revisi. Termasuk `references/daftar-pola-anti-slop.md`, daftar periksa pola tulisan mesin yang harus dihindari.

### `skills/kemasan-video` — kemasan visual video

Mengemas judul, caption, dan diagram hasil render kode dengan satu tema Hallmark yang terkunci, lint QC Impeccable di gerbang, spek gerak MOTION.md, dan loop look-match terukur terhadap acuan. Tema teruji yang disertakan: Blueprint (`references/themes/blueprint.md`).

### `skills/video-suara-bawaan` — video & suara generatif bawaan agen

Mengemas kemampuan generatif bawaan Muse sendiri: video generatif dengan dialog native (terbukti natural berbahasa Indonesia) dan TTS bawaan untuk narasi. Lengkap dengan aturan pencegahan AI slop sebelum generate (larang teks di dalam frame, satu penutur, klip pendek) dan audit ketat frame-per-frame yang wajib lolos sebelum hasil generate ditunjukkan ke pemilik channel. Lahir dari pelajaran mahal: cek kemampuan bawaan agenmu dulu sebelum berminggu-minggu menguji engine eksternal.

## Cara pakai

Salin folder skill yang diinginkan ke folder skill kustom agenmu (di Muse: `~/workspace/custom-skills/`), lalu minta agen membaca `SKILL.md`-nya saat mengerjakan tugas terkait. Setiap skill berdiri sendiri; berkas di `references/` adalah bahan wajibnya, jangan dipisah.

## Catatan

- Skill ini lahir dari kegagalan nyata (naskah yang lolos penilai analitis tetapi divonis penonton pertama membingungkan) — gerbangnya sengaja mengukur apa yang dulu tidak diukur: janji hook terbayar + pendengar pertama bisa mengikuti.
- Beberapa contoh di `references/` memakai nama episode dan konteks channel kami; metodenya berlaku umum, contohnya tinggal diganti.
- Lisensi tema pihak ketiga yang dirujuk (Hallmark) adalah MIT, sesuai sumbernya.
