# Anotasi Beatmap — outcome, hook, dan fungsi beat

Setiap beat naskah (kedua mode) dianotasi sebelum naik ke gerbang. Anotasi membuat dua vonis yang dulu soal selera menjadi mekanis: "penutup awkward" dan "beat yang menganggur". Diadaptasi dari pengetikan outcome & hook + peringatan pacing di `plot-structure` story-skills (danjdewhurst, MIT), dan cek scene function di developmental-edit creative-writing-skills (haowjy, Apache-2.0).

## Langkah 0 — Reverse outline (wajib, sebelum anotasi)

Tulis satu baris per beat: apa yang BENAR-BENAR dilakukan beat ini, dari teksnya — bukan dari rencana. Bandingkan dengan rencana beat. Selisihnya adalah diagnosis pertama. (Preseden: reverse outline Episode 002 asli memperlihatkan jawaban utama diberikan di beat 2 dan topik baru dibuka di beat 8 — dua cacat yang tidak terlihat dari rencana beat-nya.) Reverse outline adalah adaptasi ringan dari revision-continuity story-skills.

## Kolom anotasi

| Kolom | Isi |
|---|---|
| Beat | nomor + rentang detik perkiraan |
| Outcome | hasil usaha di layar terhadap tujuannya: `yes` / `no` / `yes-but` / `no-and` |
| Fungsi | apa yang BERUBAH sesudah beat ini: model penonton (PENJELAS) atau keadaan tokoh/dunia (CERITA). Satu frasa konkret |
| Bayaran/Tanam | ID lembar janji yang dibayar atau ditanam beat ini (P…/Q…/S…), atau "—" |
| Hook keluar | tipe pegangan yang dibawa ke beat berikut: `question` / `revelation` / `reversal` / `decision` / `emotional` / `cliffhanger` / `resolution` |

### Cara membaca outcome di Mode PENJELAS

"Usaha" di layar adalah usaha penonton/tokoh-perantara memahami atau melakukan hal di hook. Contoh pola sehat penjelas: mencoba → `no-and` (gagal, DAN ternyata bukan itu penahannya) → potongan jawaban menumpuk → klimaks `yes-but` (terbukti, TAPI dengan syarat yang justru jadi kejujuran episode) → penutup `resolution`.

### Cara membaca outcome di Mode CERITA

Outcome adalah hasil usaha TOKOH terhadap want-nya di beat itu. Yang menggerakkan cerita adalah komplikasi `yes-but` dan `no-and`; rangkaian `yes` bersih menguras tegangan.

## Aturan mekanis (ditegakkan di gerbang)

1. **Penutup bertipe `question` baru = REVISI otomatis.** Beat terakhir wajib `resolution` atau `emotional` yang membayar janji awal (P…/S… yang ditanam di beat awal). Echo hook di penutup sah — ia `resolution` + gema, bukan pertanyaan baru.
2. **Beat tanpa fungsi = potong atau gabung.** Bila kolom Fungsi tidak bisa diisi frasa konkret ("penonton sekarang tahu X" / "tokoh kehilangan Y"), beat itu kandidat potong/kompresi — cek scene function developmental-edit.
3. **Peringatan pacing (pinjam, perlakukan sebagai ajakan membaca ulang, bukan hukum):**
   - ≥3 outcome `yes` bersih berurutan di tengah = tegangan terkuras; selingi komplikasi.
   - ≥3 beat berurutan yang hook keluarnya `resolution` di TENGAH naskah = video terasa selesai berkali-kali sebelum berakhir. (Satu `resolution` di akhir justru wajib.)
   - Beat tanpa hook keluar sama sekali (berakhir datar, tidak membawa pegangan apa pun) = tandai dan periksa.
4. **Setiap baris Bayaran/Tanam harus cocok dengan lembar janji.** ID yang muncul di beatmap tetapi tidak ada di lembar janji (atau sebaliknya) = kedua berkas belum sinkron; gerbang mengembalikan keduanya.
5. **Fungsi ditentukan posisi.** Beat yang isinya sama bisa sah di satu posisi dan gagal di posisi lain (elemen "tekanan sisa" Episode 002: gagal sebagai bukti-kedua di beat 7 asli, sah sebagai anak tangga eskalasi di beat 5–6 tulis-ulang). Saat memindah beat, nilai ulang kolom Fungsinya — jangan menyalin vonis lama.

## Templat kosong

```markdown
## Reverse outline (dari teks, bukan rencana)

| Beat | Yang benar-benar dilakukan beat ini |
|---|---|
| 1 |  |

## Anotasi beatmap

| Beat | Outcome | Fungsi (yang berubah) | Bayaran/Tanam | Hook keluar |
|---|---|---|---|---|
| 1 |  |  |  |  |
| … |  |  |  |  |
| terakhir |  |  |  | resolution / emotional |
```
