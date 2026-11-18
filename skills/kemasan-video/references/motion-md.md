# Format MOTION.md

Sumber format: OpenMotion (github.com/nexu-io/openmotion), lisensi Apache-2.0.
Yang diadopsi hanya format spesifikasinya. Aplikasi OpenMotion tidak diadopsi.

Satu berkas MOTION.md ditulis untuk setiap video referensi yang dipelajari,
sebelum adegan dibangun. Berkas ini menggantikan beatmap bentuk bebas.

## Anatomi berkas

1. Judul berisi nama studi dan nama referensinya.
2. Satu baris tautan referensi, jendela waktu yang dipelajari, rasio aspek, dan durasi.
3. Satu paragraf pendek tentang apa yang dilakukan referensi pada jendela itu.
4. Tabel beat tiga kolom (struktur wajib, lihat templat).
5. Baris tautan ke komposisi yang bisa diedit, film hasil, dan video perbandingan berdampingan.

Kolom tabel:

- `Time in cut` — rentang detik beat di dalam potongan referensi.
- `Motion to carry across` — gerak referensi yang dipertahankan, ditulis sebagai perbuatan yang terlihat, bukan kata sifat.
- `OpenMotion adaptation` — versi kita dari beat itu. Di pipa kita kolom ini dibaca sebagai "adaptasi kita": bahan, objek, dan teks diganti milik kita, geraknya dipertahankan.

## Templat kosong

```markdown
# <Nama studi> · <Nama referensi> study

[<Judul referensi>](<tautan>) · <mm:ss.mm–mm:ss.mm> · <rasio> · <durasi> detik

<Satu paragraf: apa yang dilakukan referensi pada jendela ini, objek apa yang
bergerak, dan ke mana mata penonton dibawa.>

| Time in cut | Motion to carry across | Adaptasi kita |
| --- | --- | --- |
| 0.00–0.00 s | <gerak referensi> | <versi kita> |
| 0.00–0.00 s | <gerak referensi> | <versi kita> |

[Komposisi bisa diedit](<tautan>) · [Film hasil](<tautan>) · [Berdampingan](<tautan>)
```

## Contoh terisi (dari repo OpenMotion, Apache-2.0)

# Stripe Treasury · Coast study

[Stripe Treasury reference](https://x.com/stripe/status/2049621560743608481) · 00:21.50–00:26.50 · 16:9 · 5 seconds

Stripe moves from a button to a form, then takes the violet payment card out of its interface and turns it in space. OpenMotion uses those beats to present a coastal landscape as a perforated film slide. The sky, sun, coastline, film stock, pointer and type are drawn in editable HTML and CSS.

| Time in cut | Motion to carry across | OpenMotion adaptation |
| --- | --- | --- |
| 0.00–0.41 s | Press a centered pill. | A warm paper field frames the “Frame a shot” button. |
| 0.41–2.13 s | Open the form and move the pointer to its options. | The preview shows a sunset framed in film stock. Choose the release format. |
| 2.13–3.01 s | Push in for confirmation and pull out on the click. | The pointer selects the landscape print. |
| 3.01–3.61 s | Lift the object from the form, flip once and reveal the accompanying figure. | The film slide turns past its striped back. “03” names the scene. |
| 3.61–5.00 s | Settle on the left and hold the caption on the right. | Hold on the coastline and the title “Coast study”. |

[Editable composition](index.html) · [OpenMotion film](film.mp4) · [Side by side](comparison.mp4) · [Portrait comparison](comparison.mobile.mp4)

## Aturan pakai di pipa kita

- Tulis MOTION.md pada tahap beatmap atau storyboard, sebelum mesin render dipilih.
- Isi kolom adaptasi dengan bahan kita sendiri. Jangan menyalin naskah, karakter, atau shot referensi.
- Simpan berkas di folder kerja video itu, di samping bukti gerbangnya.
- Sertakan tautan perbandingan berdampingan begitu film pertama ada. Tabel tanpa bukti visual belum selesai.
