# Loop look-match dan QA frame

Sumber metode: Claude Animated Shorts (github.com/mromidev/claude-animated-shorts), lisensi MIT.
Yang diadopsi adalah metodenya. Aturan tampilannya tidak ikut (lihat bagian akhir berkas ini).

## Loop look-match

Dipakai setiap kali ada permintaan "buat seperti referensi ini" pada bukti visual atau episode.

1. Ukur referensi lebih dulu. Tugaskan satu analis per topik: gerak, kedalaman, tekstur, karakter, cahaya, garis, dan grade. Setiap analis menulis angka, bukan kata sifat, ke `references/reports/<topik>.md`. Laporan itu menjadi sumber kebenaran bagi semua pekerja sesudahnya.
2. Kunci angka menjadi bible. Nilai terukur ditulis sebagai nilai tetap di berkas gaya proyek, misalnya preset cahaya per jenis shot, ketebalan garis per jarak, dan nilai blur per jenis shot. Contoh pola dari proyek sumber: cahaya siang dan cahaya emas masing-masing punya preset angka sendiri, dan skor awal proyek itu naik dari kisaran 3 sampai 7 menjadi 5 sampai 7 per area sesudah empat ronde.
3. Iterasi di sandbox. Salin folder proyek menjadi satu sandbox per pemilik berkas (kamera, dunia, material, karakter, pasca). Setiap pemilik hanya mengedit berkasnya di sandbox miliknya. Gabungkan hasil ke proyek utama, lalu sinkronkan ulang semua sandbox dari utama sebelum ronde berikutnya.
4. Nilai dengan penilai segar. Penilai yang tidak ikut membangun membandingkan lembar berdampingan antara hasil kita dan frame referensi, memberi skor per area dari 10, dan mengembalikan daftar perbaikan bernomor yang menyebut nomor frame. Petakan setiap perbaikan ke pemilik berkasnya.
5. Ulangi sampai skor datar. Metode ini bertahap dan mahal. Skor penulis proyek sumbernya sendiri sesudah empat ronde hanya 5 sampai 7 per area, jadi rencanakan beberapa ronde dan jangan menjanjikan kecocokan penuh pada ronde pertama.

Kontrak antar pemilik tinggal di konstanta yang diekspor bersama, misalnya tabel blur dari berkas cerita dan preset cahaya dari berkas cahaya. Mengubah kontrak berarti memberi tahu setiap pemilik yang membacanya.

## QA frame pada render final

Jalankan ketiga pemeriksaan ini pada setiap MP4 final sebelum diserahkan. Perintah terverifikasi penulis pada 2026-11-18 (di mesin penulis).

Periksa frame hitam:

```bash
ffmpeg -hide_banner -i <final.mp4> -vf blackdetect=d=0.25:pix_th=0.10 -f null -
```

Segmen hitam dilaporkan di keluaran log sebagai baris black_start dan black_end. Nol laporan berarti lulus bagian ini.

Periksa frame beku:

```bash
ffmpeg -hide_banner -i <final.mp4> -vf freezedetect=n=0.003:d=0.5 -f null -
```

Rentang beku dilaporkan sebagai freeze_start, freeze_duration, dan freeze_end. Rentang beku adalah sinyal untuk memeriksa shot itu, bukan vonis otomatis. Gerak sangat lambat yang disengaja bisa ikut tertangkap, seperti drift judul pada klip uji kami yang tertangkap sebagai rentang 2,1 detik.

Periksa kenyaringan:

```bash
ffmpeg -hide_banner -i <final.mp4> -af loudnorm=print_format=json -f null -
```

Baca nilai integrated loudness dari ringkasan JSON di akhir keluaran dan catat bersama bukti gerbang.

Ambil satu frame untuk dibaca manusia:

```bash
ffmpeg -hide_banner -ss <detik> -i <final.mp4> -frames:v 1 <frame.png>
```

Periksa juga frame pop secara visual dari lembar kontak per shot. Pop adalah lompatan gambar satu frame yang tidak tertangkap detektor hitam atau beku.

Dua aturan gerak yang menjaga QA tetap bersih:

- Tahan yang datar terbaca sebagai beku. Setiap hold wajib punya dorongan masuk perlahan, jangan ada hold statis.
- Pass garis harus berjalan sebelum blur kedalaman. Garis yang digabung satu pass dengan blur akan tertimpa.

## Gotcha disk Remotion

Setiap bundle Remotion menyalin folder `public/` proyek ke folder temp dan tidak menghapusnya. Angka berikut adalah contoh kasus dari proyek sumber metode ini — pelajaran perilakunya yang berlaku umum, bukan patokan mesinmu: folder `public/` proyek itu sekitar 1,3 GB, pemakaian temp-nya teramati menghabiskan 60 sampai 110 GB, dan satu render mati karena disk penuh.

- Atur `TEMP` dan `TMPDIR` ke folder di disk besarmu sebelum render Remotion apa pun.
- Hapus folder `remotion-webpack-bundle-*` dan `puppeteer_dev_chrome_profile-*` di folder temp itu ketika proyek selesai dan tidak ada render berjalan.
- Parameter pasca berskala piksel harus diskalakan terhadap tinggi keluaran. Stills setengah skala dan final skala penuh tidak berbagi angka mentah yang sama.

## Yang tidak diadopsi dari proyek sumber

- Larangan caption. Proyek sumber melarang caption; aturan caption adalah parameter proyekmu (proyek penulis mewajibkan caption pendek) — tetapkan di parameter proyek, jangan warisi larangan itu.
- Ekspor 1440x2560. Standar ekspor adalah standar berkas parameter proyekmu (lihat `PIPELINE.md` di akar repo ini); jangan mewarisi angka proyek sumber maupun angka penulis.
- Tumpukan dan karakter proyek sumber. Hanya metode, QA, dan gotcha di berkas ini yang diambil.
