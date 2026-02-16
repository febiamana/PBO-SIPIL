# Tugas UAS Pemrograman Berorientasi Objek (PBO)

## Tentang Aplikasi (SIPIL)
SIPIL (Sistem Informasi Peminjaman Inventaris Laboratorium) adalah aplikasi desktop berbasis Java Swing untuk mengelola inventaris laboratorium kampus.

## Fitur Utama
- Login admin
- CRUD data barang
- Peminjaman barang dengan validasi stok
- Pengembalian barang dengan pembaruan stok
- Riwayat transaksi peminjaman

## Teknologi
- Java 17, Swing + FlatLaf (tema modern)
- MariaDB (mariadb-java-client)
- Maven

## Struktur Proyek
```text
tugasuas/
├─ pom.xml
├─ database.sql
├─ src/main/java/com/pbo/inventaris/
│  ├─ DatabaseHelper.java
│  ├─ model/
│  │  ├─ User.java
│  │  ├─ Barang.java
│  │  └─ Peminjaman.java
│  ├─ dao/
│  │  ├─ UserDAO.java
│  │  ├─ BarangDAO.java
│  │  └─ PeminjamanDAO.java
│  └─ ui/
│     ├─ LoginFrame.java
│     └─ MainFrame.java
```

## Alur Program
- Login: pengguna memasukkan kredensial → validasi ke database → jika benar, buka halaman utama.
- Halaman Utama: tab Manajemen Barang dan Peminjaman/Pengembalian.
- Manajemen Barang: isi form → Tambah/Update/Hapus → tabel ter-update.
- Peminjaman: isi nama peminjam + pilih barang → cek stok → simpan transaksi → stok berkurang.
- Pengembalian: pilih transaksi berstatus DIPINJAM → simpan pengembalian → stok bertambah.

## Panduan Instalasi dan Penggunaan

### 1. Persiapan Database
1. Pastikan MariaDB sudah terinstall dan berjalan.
2. Buat database baru dengan nama `inventaris_lab`.
3. Import file `database.sql` ke dalam database tersebut.
   ```bash
   mysql -u root -p < database.sql
   ```
   Atau buka file `database.sql` di aplikasi manajemen database (seperti DBeaver/HeidiSQL) dan eksekusi scriptnya.
4. Sesuaikan konfigurasi koneksi di file `src/main/java/com/pbo/inventaris/DatabaseHelper.java` jika username/password berbeda.

### 2. Menjalankan Aplikasi
Jika menggunakan Maven:
```bash
mvn clean compile exec:java -Dexec.mainClass="com.pbo.inventaris.ui.LoginFrame"
```

Jika menggunakan IDE (IntelliJ IDEA / NetBeans / Eclipse):
1. Buka folder proyek ini sebagai Project.
2. Pastikan library `mariadb-java-client` sudah ditambahkan ke classpath.
3. Jalankan file `LoginFrame.java`.
