# Panduan Laragon untuk PHP dan Laravel

Panduan lengkap untuk menjalankan project **PHP Native** dan **Laravel** secara lokal menggunakan **Laragon**.

Panduan ini membahas mulai dari instalasi Laragon, penempatan project, menjalankan Web Server dan MySQL, konfigurasi database, virtual host, hingga troubleshooting dasar.

## 📋 Daftar Isi

- [Apa Itu Laragon?](#apa-itu-laragon)
- [Persiapan](#persiapan)
- [Install dan Menjalankan Laragon](#install-dan-menjalankan-laragon)
- [Menyimpan Project](#menyimpan-project)
- [Menjalankan Project PHP Native](#menjalankan-project-php-native)
- [Membuat Database MySQL](#membuat-database-mysql)
- [Konfigurasi Database](#konfigurasi-database)
- [Menjalankan Project Laravel](#menjalankan-project-laravel)
- [Virtual Host Laragon](#virtual-host-laragon)
- [Mengganti Versi PHP](#mengganti-versi-php)
- [Troubleshooting](#troubleshooting)
- [Laragon vs XAMPP](#laragon-vs-xampp)
- [Struktur Project](#struktur-project)
- [Alur Menjalankan Project](#alur-menjalankan-project)
- [Kesimpulan](#kesimpulan)

---

## Apa Itu Laragon?

[Laragon](https://laragon.org/) adalah local development environment yang dapat digunakan untuk mengembangkan dan menjalankan website secara lokal.

Laragon menyediakan berbagai kebutuhan untuk pengembangan web, seperti:

- Web Server
- PHP
- MySQL
- Database management
- Virtual Host
- Composer
- Tools pendukung pengembangan web

Dengan Laragon, project website dapat dijalankan di komputer sendiri tanpa membutuhkan hosting terlebih dahulu.

---

## Persiapan

Sebelum memulai, pastikan sudah tersedia:

- Laragon
- Browser
- Code editor seperti Visual Studio Code
- Composer jika menggunakan Laravel
- Project website yang akan dijalankan

---

## Install dan Menjalankan Laragon

Setelah Laragon berhasil diinstall, buka aplikasi Laragon.

Pada halaman utama Laragon, klik:

**Start All**

Perintah tersebut akan menjalankan service yang diperlukan, seperti Web Server dan MySQL.

Pastikan service yang dibutuhkan sudah berjalan sebelum menjalankan project.

---

## Menyimpan Project

Secara default, Laragon menggunakan folder berikut sebagai lokasi project:

```text
C:\laragon\www\
```

Sebagai contoh, project dengan nama `website-saya` dapat disimpan di:

```text
C:\laragon\www\website-saya
```

Contoh struktur folder:

```text
C:\laragon\www\
└── website-saya\
    ├── index.php
    ├── css\
    ├── js\
    └── images\
```

Pastikan folder utama project berada di dalam folder `www`.

---

## Menjalankan Project PHP Native

Untuk project PHP Native, pastikan file utama seperti `index.php` berada di dalam folder project.

Contoh:

```text
C:\laragon\www\website-saya\index.php
```

Setelah Laragon aktif, project dapat dibuka melalui:

```text
http://localhost/website-saya
```

Laragon juga mendukung virtual host sehingga project dapat diakses menggunakan:

```text
http://website-saya.test
```

Nama `website-saya` mengikuti nama folder project.

---

## Membuat Database MySQL

Jika project menggunakan database, buat database terlebih dahulu.

Laragon dapat digunakan bersama database manager seperti HeidiSQL.

Buat database baru, misalnya:

```text
website_saya
```

Jika project memiliki file database dengan ekstensi `.sql`, import file tersebut ke database yang telah dibuat.

Contoh:

```text
website_saya.sql
```

---

## Konfigurasi Database

Konfigurasi database bergantung pada jenis project.

Jika project menggunakan file `.env`, konfigurasi dapat dibuat seperti berikut:

```env
DB_HOST=127.0.0.1
DB_DATABASE=website_saya
DB_USERNAME=root
DB_PASSWORD=
```

Pastikan nama database sesuai dengan database yang telah dibuat.

Username dan password juga harus disesuaikan dengan konfigurasi MySQL yang digunakan.

---

## Menjalankan Project Laravel

Untuk project Laravel, simpan project di dalam:

```text
C:\laragon\www\
```

Contohnya:

```text
C:\laragon\www\website-saya
```

### 1. Install Dependency
Buka Terminal pada folder project dan jalankan:

```bash
composer install
```

### 2. Membuat File `.env`
Jika file `.env` belum tersedia, salin:

```text
.env.example
```

menjadi:

```text
.env
```

Kemudian sesuaikan konfigurasi database.

Contoh:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=website_saya
DB_USERNAME=root
DB_PASSWORD=
```

### 3. Generate Application Key
Jalankan:

```bash
php artisan key:generate
```

### 4. Menjalankan Migration
Jika project menggunakan Laravel Migration:

```bash
php artisan migrate
```

Jika project membutuhkan database seeder:

```bash
php artisan db:seed
```

Atau migration dan seeder sekaligus:

```bash
php artisan migrate --seed
```

Setelah konfigurasi selesai, project dapat diakses melalui:

```text
http://website-saya.test
```

---

## Virtual Host Laragon

Salah satu fitur Laragon adalah virtual host otomatis.

Dengan virtual host, project tidak harus selalu diakses menggunakan:

```text
http://localhost/website-saya
```

Project dapat diakses menggunakan:

```text
http://website-saya.test
```

Nama virtual host biasanya mengikuti nama folder project.

Jika URL `.test` belum tersedia setelah menambahkan project, lakukan **Reload** pada Laragon.

---

## Mengganti Versi PHP

Beberapa project membutuhkan versi PHP tertentu.

Laragon mendukung penggunaan beberapa versi PHP sehingga versi PHP dapat disesuaikan dengan kebutuhan project.

Versi PHP yang dibutuhkan dapat diperiksa melalui:
- `composer.json`
- Dokumentasi framework
- Dokumentasi project
- Dependency yang digunakan

Untuk project Laravel, periksa requirement PHP pada file `composer.json`.

Menggunakan versi PHP yang tidak sesuai dapat menyebabkan error ketika menjalankan project atau dependency.

---

## Troubleshooting

### Website Tidak Bisa Dibuka
Jika website tidak dapat dibuka, periksa beberapa hal berikut:
1. Pastikan Laragon sudah menjalankan **Start All**.
2. Pastikan Web Server sudah aktif.
3. Pastikan project berada di `C:\laragon\www\`.
4. Pastikan nama folder project sudah benar.
5. Pastikan URL yang digunakan sesuai dengan nama project.
6. Jika menggunakan virtual host, lakukan **Reload** pada Laragon.

### Database Tidak Terhubung
Periksa:
- MySQL sudah berjalan.
- Nama database sudah benar.
- Username database sudah benar.
- Password database sudah benar.
- Host database sudah benar.
- Port MySQL sudah sesuai.
- Konfigurasi `.env` sudah benar.

### Laravel Error pada `.env`
Pastikan file `.env` sudah tersedia di root project.

Periksa konfigurasi database:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=website_saya
DB_USERNAME=root
DB_PASSWORD=
```

Setelah melakukan perubahan konfigurasi, jalankan:
```bash
php artisan config:clear
```

Jika diperlukan, cache konfigurasi dapat dibuat kembali:
```bash
php artisan config:cache
```

### Error `vendor/autoload.php`
Jika muncul error yang berkaitan dengan `vendor/autoload.php`, jalankan:
```bash
composer install
```
Perintah tersebut akan menginstall dependency yang dibutuhkan project.

### Error Versi PHP
Jika project mengalami error karena versi PHP, periksa requirement pada `composer.json`, kemudian gunakan versi PHP yang sesuai dengan requirement project.

---

## Laragon vs XAMPP

Laragon dan XAMPP sama-sama dapat digunakan untuk menjalankan website secara lokal. Perbedaan yang umum ditemukan adalah lokasi penyimpanan project.

**XAMPP**
```text
C:\xampp\htdocs\
```
Contoh:
```text
C:\xampp\htdocs\website-saya
```

**Laragon**
```text
C:\laragon\www\
```
Contoh:
```text
C:\laragon\www\website-saya
```

Jadi, jika sebuah tutorial menggunakan folder `htdocs`, pada Laragon lokasi project biasanya disesuaikan menjadi folder `www`.

---

## Struktur Project

### PHP Native
Contoh struktur project PHP Native:
```text
C:\laragon\www\
└── website-saya\
    ├── index.php
    ├── css\
    ├── js\
    ├── images\
    └── config\
```

### Laravel
Contoh struktur project Laravel:
```text
C:\laragon\www\
└── website-saya\
    ├── app\
    ├── bootstrap\
    ├── config\
    ├── database\
    ├── public\
    ├── resources\
    ├── routes\
    ├── storage\
    ├── .env
    ├── artisan
    └── composer.json
```

---

## Alur Menjalankan Project

Secara umum, alur menjalankan project menggunakan Laragon adalah:

1. Install Laragon
2. Buka Laragon
3. Klik **Start All**
4. Simpan project di `C:\laragon\www\`
5. Buat database jika diperlukan
6. Konfigurasi database
7. Install dependency jika diperlukan
8. Jalankan project
9. Buka project melalui browser

Untuk project sederhana:
```text
http://localhost/nama-project
```
Atau menggunakan virtual host Laragon:
```text
http://nama-project.test
```

---

## Kesimpulan

Laragon dapat digunakan untuk menjalankan berbagai jenis project website secara lokal, termasuk PHP Native dan Laravel.

Hal-hal utama yang perlu diperhatikan:
- Project disimpan di `C:\laragon\www\`.
- Web Server dijalankan melalui **Start All**.
- MySQL dijalankan jika project membutuhkan database.
- Konfigurasi database harus sesuai dengan project.
- Project Laravel membutuhkan dependency melalui Composer.
- Versi PHP harus sesuai dengan requirement project.
- Project dapat diakses melalui `localhost` atau virtual host `.test`.

Dengan konfigurasi yang sesuai, Laragon dapat digunakan sebagai environment lokal untuk proses pengembangan, pengujian, dan pembelajaran web development.

---

## 📄 License

Dokumentasi ini dapat digunakan untuk keperluan pembelajaran dan pengembangan.
