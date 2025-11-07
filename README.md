# UTS-Pemograman-WEB

## Nama: Lola Seftyliani
## Kelas: TI.24.A.4
## NIM: 312410339

# Tujuan Tugas 
Website ini dibuat untuk memenuhi tuga Ujian Tengah Semester (UTS) Pemograman Web 1 Proyek ini menampilkan aplikasi web sederhana untuk pemesanan buku online menggunakan HTML, CSS, dan JavaScript murni tanpa database.

Website terdiri dari beberapa halaman utama: login, dashboard, stok buku, checkout, dan tracking pengiriman.

# Struktur Project
```html
project/
│
├── Index.html
├── dashboard.html
├── stok.html
├── checkout.html
├── tracking.html
│
├── css/
│   └── style.css
│
├── js/
│   ├── main.js
│   └── data.js
│
└── assets/
    └── images/
```

# 1. Index.Html
- Input: email dan password

- Tombol: Login

 Jika salah → tampilkan alert("email/password yang anda masukkan salah")
Tambahan:

- Tambahan:
  Tombol “Lupa Password” dan “Daftar” → muncul dalam modal box/pop up
- Validasi menggunakan JavaScript

# 2. Dashboard.Html
- Menu navigasi ke:

 * Informasi Stok/Katalog
 * Tracking Pengiriman
 * Laporan Pemesanan
 * History Transaksi

- Tampilkan greeting otomatis:
- “Selamat pagi/siang/sore” sesuai waktu lokal (gunakan Date() di JS)

# 3. Stok.Html
- Ambil data dari file data.js:

- Tampilkan tabel katalog buku secara dinamis (JS DOM)

- Ada tombol Tambah Stok Baru → menambah baris baru ke tabel dengan JS

# 4.Checkout.Html









