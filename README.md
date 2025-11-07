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

o Informasi Stok/Katalog

o Tracking Pengiriman

o Laporan Pemesanan

o History Transaksi

- Tampilkan greeting otomatis:
- “Selamat pagi/siang/sore” sesuai waktu lokal (gunakan Date() di JS)

# 3. Stok.Html
- Ambil data dari file data.js:

- Tampilkan tabel katalog buku secara dinamis (JS DOM)

- Ada tombol Tambah Stok Baru → menambah baris baru ke tabel dengan JS

# 4.Checkout.Html
- Menampilkan data pemesanan (bisa tambah/ubah)

- Form:

 o Nama Pemesan

 o Alamat

 o Metode Pembayaran

 oJumlah buku

- Gunakan JS untuk validasi & menampilkan total harga

# 5. Tracking.Html
- Input: Nomor Delivery Order

- Ketika tombol "Cari" ditekan → tampilkan:

o Nama Pemesan

o Status Pengiriman (pakai progress bar / warna / list)

oDetail ekspedisi, tanggal kirim, jenis paket, total pembayaran


# 1. Halaman Login
Di halaman login ini berisi input email dan password dan berisi button Login, Daftar, dan Lupa password. jika salah memasuki email/password maka akan muncul pop up alert "Email/password yang anda masukkan salah". jikalau berhasil maka muncul pop up "Login berhasil! Selamat datang, Rina Wulandari" dan berhasil masuk ke dalam page selanjutnya yaitu dashboard.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Toko Buku</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div class="login-container">
        <h2>Login</h2>
        <input type="email" id="email" placeholder="Email">
        <input type="password" id="password" placeholder="Password">
        <button id="loginBtn">Login</button>
        <button id="lupaBtn">Lupa Password</button>
        <button id="daftarBtn">Daftar</button>
    </div>

    <div id="modal" class="modal">
        <div class="modal-content" id="modalContent">
            <span id="closeModal">&times;</span>
            <p id="modalText">Isi modal</p>
        </div>
    </div>

    <script src="js/data.js"></script>
    <script src="js/main.js"></script>

</body>
</html>
```
## main.js
```
/*login*/
const loginBtn = document.getElementById('loginBtn');
const lupaBtn = document.getElementById('lupaBtn');
const daftarBtn = document.getElementById('daftarBtn');
const modal = document.getElementById('modal');
const modalContent = document.getElementById('modalContent');
const closeModal = document.getElementById('closeModal');
const modalText = document.getElementById('modalText');

loginBtn.addEventListener('click', () => {
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;

    const pengguna = dataPengguna.find(user => user.email === email && user.password === password);

    if(pengguna) {
        alert(`Login berhasil! Selamat datang, ${pengguna.nama}`);
        sessionStorage.setItem("userLogin", JSON.stringify(pengguna));
        window.location.href = "dashboard.html";
    } else {
        alert("Email/password yang anda masukkan salah");
    }
});

function openModal(text) {
    modal.style.display = "block";
    modalText.textContent = text;
}

lupaBtn.addEventListener('click', () => {
    openModal("Masukkan email Anda untuk reset password.");
});

daftarBtn.addEventListener('click', () => {
    openModal("Isi data untuk mendaftar akun baru.");
});

closeModal.addEventListener('click', () => {
    modal.style.display = "none";
});

window.addEventListener('click', (e) => {
    if(e.target === modal) {
        modal.style.display = "none";
    }
});
```

output:
<img width="639" height="598" alt="image" src="https://github.com/user-attachments/assets/710c8762-abb7-4bb0-b7d1-57337b4d3ea1" />

output jika login berhasil:
<img width="1057" height="773" alt="image" src="https://github.com/user-attachments/assets/ec01386c-0ed9-4f1d-a641-63ff1663af68" />

output jika login gagal:
<img width="827" height="854" alt="image" src="https://github.com/user-attachments/assets/a7129810-fc2d-45af-ae46-be85ec87bd10" />

# 2. Halaman Dashboard
Halamani ini berisi ucapan selamat datang dan selamat pagi/siang/sore/malam tergantung waktu real time yang diatur oleh greeting. terdapat 4 opsi menu yakni informasi katalog, tracking, chekout/pemesanan, dan history.

Input HTML:
```
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard Toko Buku</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <div class="dashboard-container">
    <header>
      <h1 id="greeting">Selamat Datang!</h1>
      <p>Pilih menu di bawah:</p>
    </header>

    <main class="menu-grid">
      <button onclick="location.href='stok.html'">Informasi Stok/Katalog</button>
      <button onclick="location.href='tracking.html'">Tracking Pengiriman</button>
      <button onclick="location.href='checkout.html'">Laporan Pemesanan</button>
      <button onclick="location.href='history.html'">History Transaksi</button>
    </main>
  </div>

  <script src="js/main.js"></script>
  <script>
    tampilkanGreeting();
  </script>
</body>
</html>
```
# main.js
```
/*dashboard*/
function tampilkanGreeting() {
  const jam = new Date().getHours();
  let sapaan;

  if (jam < 12) sapaan = "Selamat Pagi";
  else if (jam < 18) sapaan = "Selamat Siang";
  else sapaan = "Selamat Malam";

  const nama = localStorage.getItem("namaUser") || "";
  document.getElementById("greeting").textContent =
    `${sapaan}, ${nama}! Selamat datang di Dashboard Toko Buku.`;
}
```

output:
<img width="1802" height="884" alt="image" src="https://github.com/user-attachments/assets/29c2006e-98e1-405c-a840-28f591966943" />

# 3. Halaman Katalog
Halamani ini berisi no, kode, ,nama barang, jenis barang, edisi, stok, harga, dan cover. ada button kembali ke dashboard.

Input HTML:
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Informasi Stok Katalog</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body onload="tampilkanKatalog()">
    <div class="header-katalog">
            <button class="back-btn" onclick="window.location.href='dashboard.html'">← Kembali ke Dashboard</button>
        </div>
    
    <table id="tabelStok">
        <thead>
          <tr>
            <th>
              <h1 class="h1-stok">Informasi Stok Katalog</h1>
            </th>
          </tr>
        </thead>
        <thead>
            <tr>
                <th>No</th>
                <th>Kode</th>
                <th>Nama Barang</th>
                <th>Jenis</th>
                <th>Edisi</th>
                <th>Stok</th>
                <th>Harga</th>
                <th>Cover</th>
            </tr>
        </thead>
        <tbody>
            <!-- Data akan dimuat lewat JS -->
        </tbody>
    </table>



    <script src="js/data.js"></script>
    <script>
        function tampilkanKatalog() {
            const tbody = document.querySelector("#tabelStok tbody");
            tbody.innerHTML = ""; 

            dataKatalogBuku.forEach((item, index) => {
                const row = document.createElement("tr");
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${item.kodeBarang}</td>
                    <td>${item.namaBarang}</td>
                    <td>${item.jenisBarang}</td>
                    <td>${item.edisi}</td>
                    <td>${item.stok}</td>
                    <td>${item.harga}</td>
                    <td><img src="${item.cover}" alt="${item.namaBarang}"></td>
                `;
                tbody.appendChild(row);
            });
        }
    </script>
</body>
</html>
```
# main.js
```
/*katalog*/
function tampilkanKatalog() {
    const tbody = document.querySelector("#tabelStok tbody");
    tbody.innerHTML = ""; 

    dataKatalogBuku.forEach((item, index) => {
        const row = document.createElement("tr");
        row.innerHTML = `
            <td>${index + 1}</td>
            <td>${item.kode}</td>
            <td>${item.nama}</td>
            <td>${item.jenis}</td>
            <td>${item.edisi}</td>
            <td>${item.stok}</td>
            <td>${item.harga}</td>
            <td><img src="${item.cover}" alt="${item.nama}" style="width:60px; border-radius:5px;"></td>
        `;
        tbody.appendChild(row);
    });
}

document.addEventListener("DOMContentLoaded", tampilkanKatalog);
```
Output:
<img width="1836" height="666" alt="image" src="https://github.com/user-attachments/assets/0a985889-4fe7-4fa7-9682-7fa19ae850cf" />

# 4. Halaman Checkout
Halamani ini berisi input buku, jumlah, nama, alamat, dan metode pembayaran. ada 2 tombol yakni tambahkan keranjang dan tampilkan ringkasan. riwayat transaksi akan tersimpan ke localstorage dan nanti tersimpan di history.

Input HTML:
```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pemesanan Buku</title>
  <link rel="stylesheet" href="CSS/style.css">
</head>
<body>
  <div class="checkout-container">
    <h1>Pemesanan Buku</h1>

    <section class="card">
      <h2>Form Pemesanan</h2>
      <form id="formPemesanan">
        <div class="form-group">
          <label for="pilihBuku">Pilih Buku</label>
          <select id="pilihBuku"></select>
        </div>
        <div class="form-group">
          <label for="jumlahBuku">Jumlah</label>
          <input type="number" id="jumlahBuku" min="1" placeholder="Masukkan jumlah" required>
        </div>
        <button type="button" onclick="tambahPesanan()">Tambah ke Keranjang</button>
      </form>
    </section>

    <section class="card">
      <h2>Keranjang Pemesanan</h2>
      <table id="tabelPemesanan">
        <thead>
          <tr>
            <th>Nama Buku</th>
            <th>Harga</th>
            <th>Jumlah</th>
            <th>Total</th>
            <th>Aksi</th>
          </tr>
        </thead>
        <tbody></tbody>
      </table>
      <h3 id="totalBayar">Total Bayar: Rp0</h3>
    </section>

    <section class="card">
      <h2>Informasi Pemesan & Pembayaran</h2>
      <form id="formInfo">
        <div class="form-group">
          <label>Nama Lengkap</label>
          <input type="text" id="namaPemesan" placeholder="Masukkan nama lengkap" required>
        </div>
        <div class="form-group">
          <label>Alamat</label>
          <textarea id="alamatPemesan" placeholder="Masukkan alamat pengiriman" required></textarea>
        </div>
        <div class="form-group">
          <label>Metode Pembayaran</label>
          <select id="metodePembayaran">
            <option value="Transfer Bank">Transfer Bank</option>
            <option value="COD">COD (Bayar di Tempat)</option>
            <option value="E-Wallet">E-Wallet (Dana / OVO / Gopay)</option>
          </select>
        </div>
        <button type="button" onclick="tampilkanPesanan()">Tampilkan Ringkasan</button>
      </form>
    </section>

    <section class="card" id="hasilPesanan" style="display: none;">
      <h2>Ringkasan Pesanan</h2>
      <div id="outputPesanan"></div>
    </section>

    <a href="dashboard.html" class="kembali-btn">Kembali ke Dashboard</a>
  </div>

  <script>
    const dataBuku = [
      { nama: "Pengantar Ilmu Komunikasi", harga: 180000 },
      { nama: "Manajemen Keuangan", harga: 220000 },
      { nama: "Kepemimpinan", harga: 150000 },
      { nama: "Mikrobiologi Dasar", harga: 200000 },
      { nama: "Perkembangan Anak Usia Dini", harga: 250000 }
    ];

    const pilihBuku = document.getElementById("pilihBuku");
    dataBuku.forEach((buku, index) => {
      const opt = document.createElement("option");
      opt.value = index;
      opt.textContent = buku.nama + " - Rp " + buku.harga.toLocaleString("id-ID");
      pilihBuku.appendChild(opt);
    });

    let keranjang = [];

    function tambahPesanan() {
      const idx = pilihBuku.value;
      const jumlah = parseInt(document.getElementById("jumlahBuku").value);
      if (!jumlah || jumlah <= 0 || idx === "") {
        alert("Pilih buku dan jumlah yang valid!");
        return;
      }

      const buku = dataBuku[idx];
      const total = buku.harga * jumlah;
      keranjang.push({ nama: buku.nama, harga: buku.harga, jumlah, total });
      renderTabel();
    }

    function renderTabel() {
      const tbody = document.querySelector("#tabelPemesanan tbody");
      tbody.innerHTML = "";
      let totalBayar = 0;

      keranjang.forEach((item, i) => {
        totalBayar += item.total;
        const row = `
          <tr>
            <td>${item.nama}</td>
            <td>Rp ${item.harga.toLocaleString("id-ID")}</td>
            <td>${item.jumlah}</td>
            <td>Rp ${item.total.toLocaleString("id-ID")}</td>
            <td><button onclick="hapusItem(${i})">Hapus</button></td>
          </tr>`;
        tbody.innerHTML += row;
      });

      document.getElementById("totalBayar").textContent =
        "Total Bayar: Rp " + totalBayar.toLocaleString("id-ID");
    }

    function hapusItem(index) {
      keranjang.splice(index, 1);
      renderTabel();
    }

    function tampilkanPesanan() {
      if (keranjang.length === 0) {
        alert("Keranjang masih kosong!");
        return;
      }
      const nama = document.getElementById("namaPemesan").value;
      const alamat = document.getElementById("alamatPemesan").value;
      const metode = document.getElementById("metodePembayaran").value;

      if (!nama || !alamat) {
        alert("Isi semua data pemesan!");
        return;
      }

      let totalBayar = keranjang.reduce((acc, item) => acc + item.total, 0);

      const transaksi = {
        nama,
        alamat,
        metode,
        total: totalBayar,
        tanggal: new Date().toLocaleString(),
        detail: keranjang
      };

      const history = JSON.parse(localStorage.getItem("riwayatTransaksi")) || [];
      history.push(transaksi);
      localStorage.setItem("riwayatTransaksi", JSON.stringify(history));

      let ringkasan = `<p><strong>Nama Pemesan:</strong> ${nama}</p>
                       <p><strong>Alamat:</strong> ${alamat}</p>
                       <p><strong>Metode Pembayaran:</strong> ${metode}</p>
                       <h3>Detail Pesanan:</h3><ul>`;

      keranjang.forEach(item => {
        ringkasan += `<li>${item.nama} - ${item.jumlah} pcs (Rp ${item.total.toLocaleString("id-ID")})</li>`;
      });

      ringkasan += `</ul><p><strong>Total Bayar:</strong> Rp ${totalBayar.toLocaleString("id-ID")}</p>`;

      document.getElementById("outputPesanan").innerHTML = ringkasan;
      document.getElementById("hasilPesanan").style.display = "block";

      keranjang = [];
      renderTabel();
      alert("Pesanan berhasil disimpan ke riwayat transaksi!");
    }
  </script>
  <script src="js/main.js"></script>
</body>
</html>
```
# main.js
```
/*chekout*/
document.getElementById("formPemesanan").addEventListener("submit", function(e) {
  e.preventDefault();

  var nama = document.getElementById("nama").value;
  var buku = document.getElementById("buku").value;
  var jumlah = document.getElementById("jumlah").value;
  var metode = document.getElementById("metode").value;
  var total = document.getElementById("total").value;
  var dataLama = JSON.parse(localStorage.getItem("riwayatTransaksi")) || [];
  var transaksiBaru = {
    namaPemesan: nama,
    bukuDipesan: buku + " (" + jumlah + " pcs)",
    metode: metode,
    total: "Rp " + total,
    status: "Menunggu Pembayaran"
  };

  dataLama.push(transaksiBaru);
  localStorage.setItem("riwayatTransaksi", JSON.stringify(dataLama));

  alert("Pemesanan berhasil! Data disimpan ke riwayat transaksi.");

  document.getElementById("formPemesanan").reset();
  window.location.href = "dashboard.html";
});
```

Output:
<img width="1639" height="956" alt="image" src="https://github.com/user-attachments/assets/1efb22d2-e0fe-43f3-9c05-4dcbb17eafb4" />

Output jika keranjang kosong:
<img width="1716" height="952" alt="image" src="https://github.com/user-attachments/assets/4211e1a0-393f-4a55-aed8-537ff1c5ad2d" />

output jika data blm lengkap:
<img width="1744" height="932" alt="image" src="https://github.com/user-attachments/assets/d7e5f78a-1555-4268-bcce-02c702b0a5da" />

output Hasil ringkasan:
<img width="701" height="529" alt="image" src="https://github.com/user-attachments/assets/2bca21fe-b10d-42fe-87b8-29df591a04dc" />

# 5. Halaman Tracking
Halamani ini berisi input kode DO yang didalamnya berisi nama pemesan, status pengiriman, detail pengiriman, dan riwayat perjalanan. ketika kode DO tidak diinput maka akan muncul pop up.

Input HTML:
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tracking Pengiriman</title>
    <link rel="stylesheet" href="CSS/style.css">
</head>
<body>
    <div class="tracking-container">
        <div class="header-tracking">
            <button class="back-btn" onclick="window.location.href='dashboard.html'">← Kembali ke Dashboard</button>
            <h1>Informasi Pengiriman</h1>
        </div>

        <div class="tracking-form">
            <label for="nomorDO">Masukkan Nomor Delivery Order:</label>
            <input type="text" id="nomorDO" placeholder="Contoh: 20230012">
            <button onclick="tampilkanTracking()">Cari</button>
        </div>

        <div id="hasilTracking" class="tracking-result" style="display:none;">
            <h2>Hasil Tracking</h2>
            <p><strong>Nama Pemesan:</strong> <span id="namaPemesan"></span></p>
            <p><strong>Status Pengiriman:</strong> <span id="status"></span></p>

            <div class="progress-bar">
                <div id="progress" class="progress"></div>
            </div>

            <h3>Detail Pengiriman</h3>
            <table>
                <tr><th>Ekspedisi</th><td id="ekspedisi"></td></tr>
                <tr><th>Tanggal Kirim</th><td id="tanggal"></td></tr>
                <tr><th>Jenis Paket</th><td id="jenis"></td></tr>
                <tr><th>Total Pembayaran</th><td id="total"></td></tr>
            </table>

            <h3>Riwayat Perjalanan</h3>
            <ul id="riwayat"></ul>
        </div>
    </div>

    <script src="js/data.js"></script>
    <script src="js/main.js"></script>
</body>
</html>
```
# main.js
```
/*tracking*/
function tampilkanTracking() {
    var nomor = document.getElementById("nomorDO").value.trim();
    var hasilDiv = document.getElementById("hasilTracking");
    var riwayatList = document.getElementById("riwayat");

    if (dataTracking[nomor]) {
        var data = dataTracking[nomor];
        document.getElementById("namaPemesan").textContent = data.nama;
        document.getElementById("status").textContent = data.status;
        document.getElementById("ekspedisi").textContent = data.ekspedisi;
        document.getElementById("tanggal").textContent = data.tanggalKirim;
        document.getElementById("jenis").textContent = data.paket;
        document.getElementById("total").textContent = data.total;

        document.getElementById("progress").style.width = data.progress + "%";
        if (data.progress === 100) {
            document.getElementById("progress").style.backgroundColor = "#16a34a";
        } else {
            document.getElementById("progress").style.backgroundColor = "#facc15";
        }

        riwayatList.innerHTML = "";
        data.perjalanan.forEach(item => {
            let li = document.createElement("li");
            li.innerHTML = `<strong>${item.waktu}</strong> - ${item.keterangan}`;
            riwayatList.appendChild(li);
        });

        hasilDiv.style.display = "block";
    } else {
        alert("Nomor Delivery Order tidak ditemukan!");
        hasilDiv.style.display = "none";
    }
}
```

Output:
<img width="1886" height="581" alt="image" src="https://github.com/user-attachments/assets/8ab5cf8c-e79f-4207-b06d-da2f6d24b7cd" />
<img width="1450" height="951" alt="image" src="https://github.com/user-attachments/assets/dca800bc-f7c3-4a0a-8841-55c1af84c01f" />

Output jika code do tidak di input:
<img width="1531" height="688" alt="image" src="https://github.com/user-attachments/assets/de1738f6-d7c9-4418-8a48-713ea6190f45" />

# 6. Halaman History
Halamani ini berisi riwayat transaksi pemesan yang dari halaman chekout. isinya nama, metode pembayaran, total, dan tanggal. tersedia juga button kembali ke dasboard.

Input HTML:
```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard - Riwayat Transaksi</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <div class="container">
    <h1>Riwayat Transaksi Buku</h1>
    <table id="tabelTransaksi">
      <thead>
        <tr>
          <th>Nama Pemesan</th>
          <th>Metode Pembayaran</th>
          <th>Total</th>
          <th>Tanggal</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>

    <a href="checkout.html" class="btn">Kembali ke Pemesanan</a>
  </div>

  <script>
    const tbody = document.querySelector("#tabelTransaksi tbody");
    const history = JSON.parse(localStorage.getItem("riwayatTransaksi")) || [];

    function tampilkanHistory() {
      tbody.innerHTML = "";
      if (history.length === 0) {
        tbody.innerHTML = `<tr><td colspan="4">Belum ada transaksi.</td></tr>`;
        return;
      }

      history.forEach(item => {
        const row = `
          <tr>
            <td>${item.nama}</td>
            <td>${item.metode}</td>
            <td>Rp ${item.total.toLocaleString("id-ID")}</td>
            <td>${item.tanggal}</td>
          </tr>`;
        tbody.innerHTML += row;
      });
    }

    function hapusHistory() {
      if (confirm("Hapus semua riwayat transaksi?")) {
        localStorage.removeItem("riwayatTransaksi");
        tampilkanHistory();
      }
    }

    tampilkanHistory();
  </script>
</body>
</html>
```
# main.js
```
<h1>Riwayat Transaksi Buku</h1>
    <table id="tabelTransaksi">
      <thead>
        <tr>
          <th>Nama Pemesan</th>
          <th>Metode Pembayaran</th>
          <th>Total</th>
          <th>Tanggal</th>
        </tr>
      </thead>
      <tbody></tbody>
    </table>

    <a href="checkout.html" class="btn">Kembali ke Pemesanan</a>
  </div>
```

output:
<img width="688" height="468" alt="image" src="https://github.com/user-attachments/assets/ef04e327-9bab-4ee2-befb-d12e7e1ddbc0" />







