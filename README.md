# Aksara Accounting

Aplikasi akuntansi berbasis web yang berjalan sepenuhnya di browser. Bisa dipasang seperti aplikasi di HP maupun komputer (PWA) dan tetap bisa dibuka tanpa internet.

**Fitur:** Chart of Accounts, transaksi double-entry, saldo awal, jurnal umum, buku besar, neraca saldo, jurnal penyesuaian (template atau manual), laporan laba rugi, perubahan modal, neraca, arus kas, closing periode, dashboard dengan diagram lingkaran (pendapatan vs beban) dan diagram batang (rincian beban), backup/restore (JSON), ekspor laporan ke Excel (tersusun rapi, siap cetak) dan PDF, login lokal dengan ganti username/password.

---

## 1. Menerbitkan lewat GitHub Pages

Repositori harus berstatus **Public** (GitHub Pages gratis tidak mendukung repositori privat).

### Cara A: lewat situs GitHub (tanpa install apa pun)

1. Masuk ke GitHub, klik **New repository**, beri nama (misalnya `aksara-accounting`), pilih **Public**, lalu **Create repository**.
2. Klik **uploading an existing file**, lalu seret **seluruh isi** folder ini (`index.html`, `manifest.webmanifest`, `sw.js`, folder `icons`, dan `README.md`). Unggah isinya, bukan folder pembungkusnya, supaya `index.html` berada di lapisan paling atas repositori.
3. Klik **Commit changes**.
4. Buka **Settings → Pages**. Pada **Build and deployment**, pilih **Source: Deploy from a branch**, **Branch: `main`**, folder **`/ (root)`**, lalu **Save**.
5. Tunggu 1–2 menit. Alamat aplikasi muncul di halaman yang sama:

   `https://USERNAME.github.io/aksara-accounting/`

### Cara B: lewat Git

```bash
git init
git add .
git commit -m "Aksara Accounting"
git branch -M main
git remote add origin https://github.com/USERNAME/aksara-accounting.git
git push -u origin main
```

Lalu lanjutkan dengan langkah 4 di atas.

### Memperbarui aplikasi

Ubah `index.html` (di GitHub: buka file, klik ikon pensil, edit, **Commit changes**). Situs diperbarui dalam 1–2 menit dan pengguna otomatis mendapat versi terbaru saat terhubung internet.

---

## 2. Cara memasang di perangkat

| Perangkat | Langkah |
|---|---|
| **Android (Chrome)** | Buka alamat aplikasi, ketuk tombol **Pasang Aplikasi** di menu aplikasi, atau menu ⋮ → **Instal aplikasi** |
| **iPhone / iPad (Safari)** | Buka alamat aplikasi di Safari → tombol **Bagikan** → **Tambah ke Layar Utama** |
| **Windows / Mac / Linux (Chrome atau Edge)** | Klik ikon pasang di kolom alamat, atau tombol **Pasang Aplikasi** di aplikasi |

Setelah dipasang, aplikasi muncul dengan ikonnya sendiri dan bisa dibuka tanpa internet. Pustaka PDF disimpan di perangkat setelah pemakaian pertama saat online.

---

## 3. Hal penting untuk dipahami

- **Data tersimpan di browser masing-masing pengguna**, bukan di server. Banyak orang bisa memakai alamat yang sama, tetapi data setiap orang terpisah dan tidak saling terlihat. Data **tidak sinkron antar perangkat**.
- **Backup rutin.** Menghapus data situs di browser ikut menghapus data akuntansi. Gunakan menu **Data & Backup → Unduh Backup (.json)**, dan pulihkan lewat **Pilih File Backup**. Cara yang sama dipakai untuk memindahkan data ke perangkat lain.
- **Login bersifat lokal.** Akun awal `admin` / `admin123` ada di kode yang bersifat publik. Setiap pengguna sebaiknya langsung menggantinya di menu **Identitas Usaha**. Password disimpan sebagai hash hanya di browser pemiliknya. Ini membatasi akses yang tidak sengaja, bukan pengaman data yang kuat.
- **Belum ada data bersama antar pengguna.** Untuk beberapa pengguna yang berbagi satu data (misalnya satu perusahaan dengan beberapa akuntan), dibutuhkan server dan database (misalnya Supabase atau Firebase).

---

## 4. Menjadi file APK (opsional)

Aplikasi ini berupa PWA, bukan file `.apk`. Jika nanti diperlukan paket Android, alamat GitHub Pages di atas bisa dikonversi dengan layanan seperti [PWABuilder](https://www.pwabuilder.com). Untuk distribusi ke Play Store diperlukan akun pengembang dan penandatanganan aplikasi.

---

## Struktur berkas

```
index.html              aplikasi (HTML, CSS, JavaScript dalam satu berkas)
manifest.webmanifest    data pemasangan PWA (nama, warna, ikon)
sw.js                   service worker untuk mode offline
icons/                  ikon aplikasi
README.md               panduan ini
```

Pustaka eksternal (jsPDF untuk ekspor PDF dan font Plus Jakarta Sans) dimuat dari CDN dengan versi yang dikunci.
