# Templat Lembar Janji

Satu lembar janji per naskah, disimpan sebagai berkas pendamping NASKAH.md (atau bagian di kepala NASKAH.md). Diisi pada tahap perencanaan, diperbarui statusnya saat penulisan, dan diperiksa di gerbang.

Diadaptasi dari registri setup/payoff `story-skills` (danjdewhurst, MIT): record promise `planned → planted → paid-off` dan question `open → answered`, plus pola berkas pengecualian beralasan untuk temuan yang disengaja.

## Aturan pengisian

- **Satu record, satu tempat.** Setiap janji/pertanyaan/setup dicatat tepat satu kali di tabel ini. Jangan menyalinnya ke berkas lain sebagai record kedua.
- **ID stabil.** Pakai `P1, P2, …` untuk janji, `Q1, Q2, …` untuk pertanyaan, `S1, S2, …` untuk setup (Mode CERITA). ID tidak berubah antar-revisi.
- **Status jujur.** Record baru = `planned`. Sesudah kalimatnya benar-benar ada di naskah = `planted` (janji/setup) atau `open` (pertanyaan). Sesudah bayarannya ada di naskah = `paid-off` / `answered`. Jangan menaikkan status berdasarkan niat.
- **Beat membayar direncanakan sejak awal.** Kolom "Dibayar" diisi pada tahap perencanaan, bukan sesudah naskah jadi. Janji yang saat perencanaan belum diketahui bayarannya = premis belum matang; kembali ke lembar fakta / premise workshop.
- **Ambang tanam akhir.** Tidak ada pertanyaan atau setup baru ditanam sesudah ±70% durasi tanpa bayaran di episode yang sama. Satu-satunya jalan keluar adalah pengecualian tercatat (di bawah).
- **Pengecualian beralasan, bukan selip.** Janji yang sengaja dibiarkan terbuka (seri berikutnya, batas fakta yang memang belum diketahui) dicatat di tabel Pengecualian dengan alasan + siapa menyetujui. Pengecualian tanpa alasan = janji tak terbayar = gerbang menolak.

## Templat kosong

```markdown
# LEMBAR JANJI — <judul episode>

- Mode: PENJELAS / CERITA
- Pertanyaan hook (satu kalimat): <pertanyaan yang diajarkan 2 detik pertama>
- Janji hook (satu kalimat): <apa yang penonton berhak terima sebelum video selesai>

## Registri

| ID | Jenis | Isi (satu baris) | Ditanam (beat) | Dibayar (beat) | Status |
|---|---|---|---|---|---|
| P1 | janji |  |  |  | planned |
| Q1 | pertanyaan |  |  |  | open |

## Pengecualian beralasan

| ID | Alasan dibiarkan terbuka | Disetujui oleh | Dibayar di |
|---|---|---|---|
| — | (kosongkan bila tidak ada) |  |  |

## Cek gerbang (diisi penilai)

- [ ] Semua record `paid-off` / `answered`, atau tercatat di Pengecualian
- [ ] Tidak ada tanam baru sesudah ±70% durasi tanpa bayaran
- [ ] Pertanyaan terakhir yang ditanam = pertanyaan yang dibayar penutup
```

## Contoh terisi (dari tulis-ulang Episode 002 — versi lengkap di contoh-penjelas-ep2.md)

| ID | Jenis | Isi | Ditanam | Dibayar | Status |
|---|---|---|---|---|---|
| P1 | janji | Penonton menyaksikan sendiri apakah pintu bisa dibuka (dare) | Beat 1 | Beat 9 | paid-off |
| Q1 | pertanyaan | Apa yang sebenarnya menahan pintu? | Beat 2 | Beat 3–7 (bertahap, tuntas di 7) | answered |
| Q2 | pertanyaan | Kalau begitu, kapan pintu pernah bisa dibuka? | Beat 8 | Beat 8 (beat yang sama) | answered |

Perhatikan Q2: inilah pola pengecualian beralasan untuk caveat — pertanyaan kejujuran ditanam dan dibayar di beat yang sama, sehingga ia menjadi bayaran, bukan lubang di penutup.
