# Daftar Pola Anti-Slop Bergrada — untuk naskah suara 60 detik

Lapisan permukaan dari skill ini. Diadaptasi dari `humanizer` (blader, MIT — daftar pola berbasis Wikipedia "Signs of AI writing", WikiProject AI Cleanup) dan aturan unik `stop-slop` (hardikpandya, MIT), diekstrak untuk naskah VO oleh penilaian divisi `PENILAIAN-REPO-TULIS-2026-11-18.md` §2. Temuan preseden atas naskah kita sendiri ada di [contoh-anti-slop-ep2.md](contoh-anti-slop-ep2.md).

## Prinsip payung

Model menulis "pilihan yang paling mungkin", sehingga hasilnya rata dan generik; tulisan manusia memilih untuk satu pendengar dan satu subjek. Dua konsekuensinya:

- **Setiap kalimat yang dipertahankan wajib menambah sesuatu yang belum dimiliki pendengar.** Kalimat yang hanya memberi bobot (bukan isi) adalah tell — uji tiap kalimat terhadap beat sebelumnya.
- **Grada menentukan tindakan.** Tell kuat: bertindak pada SATU temuan. Tell lemah-sendiri: jangan bertindak pada satu temuan; bertindak pada kepadatannya. Menghapus semua pola tanpa grada akan merusak naskah lisan (adverbia ritme lisan ≠ adverbia prosa; fragmen adalah alat genre Shorts).

## Tell KUAT — bertindak pada satu temuan

| Pola | Wujud di naskah suara | Perbaikan |
|---|---|---|
| **False agency** (stop-slop) | Benda/abstraksi mati diberi verba manusia: "Physics locks the door", "the data tells us" | Namai pelaku fisik/sebenarnya: "Pressure locks the door" |
| **Kontras panggung / arguing with no one** (humanizer §1, §5) | "Eight pounds sounds like nothing. But the door has…" — separuh kalimat menjawab kesan/keberatan yang tidak pernah diajukan penonton | Nyatakan kedua fakta sebagai tangga: "Eight pounds on one square inch. The door has three thousand of them." |
| **Staged run-up** (§4) | "Here's the thing…", "let's break this down", mengumumkan sebelum menyampaikan | Sampaikan langsung; pengumuman dibuang |
| **Sisa chatbot & penafian** (§22–23) | Sapaan model, "as an AI", penafian pengetahuan di teks final | Hapus; tidak pernah sah di naskah tayang |
| **Inflated significance** (§13) | Fakta biasa dibungkus "pivotal / testament / legacy / game-changer" | Turunkan ke fakta + akibat konkretnya |
| **Kata AI jenuh** (§12) | delve, crucial, tapestry, landscape (metaforis), underscore, pivotal, intricate, foster, garner… | Ganti kata kerja/kata benda polos. (Di naskah Ep 002: nol temuan — kosakata kita bersih; jangan mengira lapisan ini selesai hanya karena daftar ini bersih.) |

## Tell LEMAH-SENDIRI — nilai kepadatannya, bukan keberadaannya

| Pola | Catatan kalibrasi divisi |
|---|---|
| **Em dash sebagai konektor serbaguna** (§8) | Di naskah suara, dash berfungsi ganda sebagai tanda jeda delivery. Aturan divisi: dash hanya sebagai jeda delivery yang DISENGAJA dan jarang; yang dinilai adalah kepadatannya (preseden Ep 002: 8 dash / 152 kata, 6 dari 9 beat — blocking, lihat pemeriksa-mekanis.md). Kalimat final sebaiknya tidak bergantung pada dash sebagai satu-satunya sambungan. |
| **Fragmen dramatis / one-line closers** (§2) | Alat genre Shorts yang sah (model positif Scale Shock memakainya). Jadi tell bila ADA DI SETIAP beat dengan denyut yang sama — ritme berbasis aturan, bukan ritme dari isi. Kepadatan dihitung pemeriksa mekanis. |
| **Quotable engineering** (stop-slop: cut quotables) | Naskah Shorts memang direkayasa quotable per beat. Bedakan: pukulan yang MEMBAWA fakta (pertahankan) vs pukulan yang hanya bergaya (tulis ulang). |
| **Peredam bertumpuk** (§9) | "sure", "even", "just", "actually" menumpuk sebagai peredam. Satu peredam kadang ritme lisan; tiga dalam dua beat = pola. Preseden: "The locks help, sure — but they're backup." |
| **Menghindari is/are/has** (§18) | "works like / serves as / acts as" menggantikan "is". "The door is a plug" lebih kuat dan lebih pendek. |
| **Pasif tanpa pelaku** (§11) | "the cabin is pumped full of air" — pelaku hilang, energi turun. Namai pelaku bila ia diketahui dari lembar fakta. |
| **Frasa -ing dangkal** (§15) | Frasa -ing tempelan demi kesan dalam ("…highlighting the danger, underscoring the stakes") di ekor kalimat. Buang atau jadikan kalimat sendiri yang berisi. |
| **Metafora pepatah** (§3) | Sayings yang terdengar dalam menggantikan klaim spesifik. Metafora yang DITANAM dan dipanen (P7) bukan pola ini — bedanya: metafora kita menempel ke benda yang sudah dilihat. |
| **Triad paksa** (§6; stop-slop: two items beat three) | Tiga contoh/frasa paralel demi rasa lengkap. Dua yang kuat mengalahkan tiga yang lengkap. Rangkaian isi yang memang bertiga (tiga langkah mekanisme dari lembar fakta) bukan triad gaya — nyatakan dasarnya dari fakta. |
| **Pembuka kalimat berulang** (§7; stop-slop sentence starters) | Beat demi beat membuka dengan subjek/pola yang sama; pembuka "So" dan Wh- yang berulang. Variasi pembuka adalah ritme termurah. Pembuka "So" pada echo penutup yang disengaja = daftar putih, bukan temuan. |

## Daftar putih (perangkat disengaja)

Pola yang dipilih sadar oleh penulis boleh dipertahankan — klausul humanizer: sampel/gaya penulis mengalahkan pola. Syarat divisi: perangkat itu DICATAT di lembar janji bagian pengecualian atau di catatan naskah, dengan alasan satu baris (mis. "fragmen Beat 1+9 = tantangan hook + echo loop, disengaja"). Pemeriksa mekanis membaca daftar putih ini dan tidak menghitung yang tercantum. Yang tidak tercatat tetap temuan.

## Prosedur (ringkas; versi penuh di SKILL.md)

Tandai → tulis ulang → cek kehilangan fakta ke lembar fakta/premis → baca keras (dengarkan render VO). Pindai-ulang mekanis maksimal 3 putaran; sesudah itu sengketa pola diputuskan penilai gerbang, bukan putaran keempat.
