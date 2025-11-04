# 📋 Dokumentasi Sistem Manajemen Layanan

## 🎯 Gambaran Umum
Sistem ini merupakan aplikasi web PHP untuk **mengelola data layanan** dengan fitur CRUD (Create, Read, Update, Delete). Menggunakan database MySQL dan mendukung upload gambar.

---

## 📁 Struktur File

### 1. `form_edit_layanan.php` ✏️
**Fungsi**: Form edit data layanan yang sudah ada

**Fitur**:
- Mengambil data dari database berdasarkan ID
- Pre-fill form dengan data existing
- Support upload gambar (`enctype="multipart/form-data"`)
- Validasi required fields

**Field Input**:
- Nama Layanan
- Deskripsi
- Harga (number)
- Durasi (number, min 1)
- Kategori (dropdown)
- Status (Aktif/Tidak Aktif)
- Gambar (file upload)

### 2. `proses_update_layanan.php` 🔄
**Fungsi**: Memproses update data layanan

**Proses**:
```php
Validasi Input → Upload Gambar → Update Database → Redirect
```

**Validasi**:
- ✅ Field required tidak kosong
- ✅ Harga & durasi harus angka positif
- ✅ Format gambar (jpg, jpeg, png, gif)
- ✅ Ukuran gambar maksimal 2MB

**Keamanan**:
- `mysqli_real_escape_string()` untuk prevent SQL injection
- File naming unik dengan timestamp

### 3. `koneksi.php` 🗄️
**Konfigurasi Database**:
```php
Host: localhost
Database: db_digital_service
User: root
Password: (kosong)
Port: 3306
```

### 4. `tampil_layanan.php` 👁️
**Fungsi**: Halaman konfirmasi setelah update berhasil

---

## 🛠️ Teknologi yang Digunakan
- **Backend**: PHP Native
- **Database**: MySQL
- **File Handling**: Upload gambar dengan validasi
- **Security**: Basic SQL injection prevention

---

## ⚙️ Cara Penggunaan

### Edit Layanan:
1. Akses `form_edit_layanan.php?id=[ID_LAYANAN]`
2. Tambahkan URL Parameter `?id=1` setelah `.php`
3. Isi/form data yang ingin diubah
4. Pilih gambar baru (opsional)
5. Klik "Simpan Layanan"
6. Redirect ke `tampil_layanan.php` jika sukses
