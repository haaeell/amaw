# Amaw's Little Universe ♡

Game ulang tahun interaktif berbasis `index.html` dan `content.js`. Tidak membutuhkan npm, server, database, framework, atau internet. Simpan `amaw.webp` dan enam gambar `hael-said*.webp` bersama `index.html`.

## Cara main

1. Simpan `index.html` dan `content.js` dalam folder yang sama. Buka `index.html` dengan browser modern yang mendukung WebGL 2 (Chrome, Safari, Firefox, atau Edge).
2. Tekan **Mulai petualangan**.
3. Berjalan mengikuti jalan setapak dan kumpulkan **5 hati kenangan**. Hati berada di sepanjang jalan utama.
   Hati yang belum ditemukan menyala; saat sudah dekat, ketuk atau klik hati di dunia untuk membuka kartunya. Tombol **E / ♡** tetap bisa dipakai.
4. Setelah semuanya ditemukan, berjalan sampai **jembatan pink** untuk membuka kejutan ulang tahun.

Setelah hati kelima, kelinci berlari menuju jembatan. Hael yang lebih tinggi menunggu di sana dengan hadiah kecil; dekati dan tekan **E / ♡**, pilih pertanyaan untuk mendengar jawabannya, lalu buka kejutan ulang tahun.
Di kartu ulang tahun, tekan **Tiup lilin 🎂**: Hael menghadap Amaw sambil memegang kue, Amaw meniup lilin angka 25. Balon dialog Hael muncul di dekat kepalanya; tekan **Jawab Hael ♡** agar Amaw membalas. Mereka lalu berpelukan selama lima detik. Tombol **Tiup lagi** mengulang adegan.
Tekan **Peluk Hael ♡** di dialog jembatan untuk pindah ke adegan romantis selama lima detik: kamera menyorot keduanya mendekat dan saling merangkul, tanpa hati jembatan menutupi karakter. Dialog kembali setelah adegan, jadi hadiah masih bisa dibuka.

Setiap kartu hati memakai pose berbeda `hael-said-1.webp` hingga `hael-said-5.webp` sesuai urutan hati. Dialog di jembatan tetap memakai `hael-said.webp`. Semua gambar WebP dikompres dari PNG, menonjol dari tepi kartu tanpa terpotong bawahnya; nama pembicara mengikuti `from` di `content.js`.

Jalan setapak berkelok melewati lima hati; ikuti batu jalan, penanda krem di tengah, garis tepi kiri-kanan, atau minimap. Tikungan dihiasi gerbang hati dan bunga.
Lima batang berpita melintang di sela hati dan **wajib dilompati**; Amaw tidak bisa menerobos atau memutar lewat pinggir. Tabrakan hanya menghentikan langkah, tanpa kehilangan progress.

Mampir ke **air mancur** di sisi jalan dan tekan interaksi untuk mendengar pesan manis bergantian.

Kelinci kecil menemani di samping karakter, berkedip saat diam dan melompat senang setelah hati ditemukan.
Nama karakter tampil di atas kepala dan mengikuti kamera. Kaki melangkah bergantian saat berjalan dan berlari. Karakter 3D dibuat prosedural secara sederhana; detail mesh dan resolusi render tetap ringan untuk perangkat yang patah-patah.
Tekan **E / ♡** saat dekat kelinci untuk mengelusnya; Amaw berhenti dan menjulurkan tangan, kelinci mendekat, telinganya bergoyang, hati kecil muncul, dan pesannya berganti. Di dekat hati atau kejutan, interaksi cerita tetap diprioritaskan.

Tekan **📖** di bagian atas untuk membuka buku kenangan. Pesan hati yang sudah ditemukan bisa dibaca ulang; halaman lain tetap terkunci sampai ditemukan.

Tekan **📸** untuk mode foto: HUD tersembunyi, lalu tekan **Simpan PNG** untuk mengunduh foto dunia, karakter, dan kelinci. Tekan **Kembali** atau Escape untuk melanjutkan.

**Laptop:** W/A/S/D atau panah untuk bergerak, Shift untuk berlari, **Spasi** untuk lompat, E untuk interaksi, geser mouse untuk memutar kamera, scroll untuk zoom.

**HP:** Joystick kiri untuk bergerak, tombol panah kanan untuk berlari, **⤴** untuk lompat, tombol ♡ untuk interaksi. Geser area dunia untuk memutar kamera.

## Personalisasi

Buka **`content.js`** di editor teks. Semua teks cerita dan musik yang bisa diganti berada di sana:

- `player` dan `from` = nama penerima dan pengirim.
- `age` = angka lilin di kue, default `25`.
- `candleConversation` = ucapan Hael dan balasan Amaw setelah tombol **Jawab Hael ♡** ditekan.
- `intro`, `ending`, `letter`, `welcome`, `questStart`, `questFinish`, `help` = tulisan pembuka, penutup, petunjuk, dan misi. `{player}` dan `{remaining}` adalah penanda yang akan diganti otomatis.
- `memories` = lima pesan hati; ubah `title`, `icon`, `text`, dan `photo`. Pertahankan lima entri. Isi `photo:'foto-1.jpg'` pada hati pertama setelah menaruh file foto di folder yang sama (atau gunakan `foto/foto-1.jpg` untuk subfolder). Jika kosong atau file tidak ditemukan, kartu menampilkan foto placeholder bernomor.
- `fountainMessages` = pesan air mancur.
- `haelGreeting` = ucapan Hael sebelum kejutan ulang tahun.
- `haelQuestions` = tombol pertanyaan (`question`) dan jawaban Hael (`answer`) di jembatan.
- `bunnyMessages` = reaksi kelinci saat dielus.
- `musicFile` = nama file lagu lokal, misalnya `musik.mp3`. Kosong sampai lagu diunggah; setelah mengunggah, isi nama file beserta ekstensi. Bisa juga `lagu/namafile.mp3` untuk subfolder.

Layar pembuka memakai `amaw.webp` yang dikompres dari ilustrasi Amaw. Karakter 3D dibuat prosedural secara sederhana; untuk karakter yang sangat mirip ilustrasi asli, perlu proses modeling 3D/GLB tambahan.
Di HP, foto pada layar pembuka tampil utuh. Ketuk fotonya untuk mengirim hati animasi sebelum memulai petualangan.

## Catatan

- Progress kelima hati disimpan di `localStorage` browser; tombol **Main lagi** mengulang cerita.
- Tombol ♫ menghidupkan atau mematikan lagu dan semua efek suara (langkah, hati, kelinci, air mancur, kejutan). Lagu dimulai setelah **Mulai petualangan**, berulang otomatis, dan berhenti sementara saat suara dimatikan. Jika file belum ada, efek suara tetap bisa dimainkan; unggah lagunya lalu buka ulang halaman.
- Render dunia berhenti saat tab tersembunyi atau layar pembuka tampil; animasi dekorasi mengikuti preferensi gerak perangkat.
- Game dan musik bisa dimainkan offline setelah file lagu tersedia.
- Browser atau perangkat yang tidak mendukung WebGL 2 tidak bisa menampilkan dunia 3D.
