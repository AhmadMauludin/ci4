Materi CodeIgniter 4: Extend Content dengan Layouts dan Views

1. Pendahuluan
Dalam pengembangan aplikasi web dengan CodeIgniter 4, sering kali kita perlu menggunakan layout atau template yang bisa digunakan kembali di berbagai halaman. Dengan fitur extend content, kita bisa membuat tampilan yang lebih terstruktur dan efisien menggunakan konsep inheritance pada views.

2. Konsep Extend Content di CodeIgniter 4
Extend content dalam CodeIgniter 4 dapat dilakukan dengan cara membuat template utama dan menggunakan view yang dapat mengisi kontennya. Teknik ini sangat berguna untuk menjaga konsistensi tampilan dan mengurangi duplikasi kode.

Struktur Folder:
app/
├── Views/
│   ├── layouts/
│   │   ├── main.php
│   ├── pages/
│   │   ├── home.php
│   │   ├── about.php

```layouts/main.php → Template utama
pages/home.php → Konten halaman Home
pages/about.php → Konten halaman About```

3. Membuat Layout Utama (main.php)
File ini berfungsi sebagai template utama yang akan digunakan oleh halaman-halaman lainnya.

Buat di folder ```app/Views/layouts/main.php

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><?= $title ?? 'Default Title' ?></title>
    <link rel="stylesheet" href="<?= base_url('css/style.css') ?>">
</head>
<body>
    <header>
        <h1>My Website</h1>
        <nav>
            <a href="<?= base_url('/') ?>">Home</a> |
            <a href="<?= base_url('/about') ?>">About</a>
        </nav>
    </header>

    <main>
        <?= $this->renderSection('content') ?>
    </main>

    <footer>
        <p>© 2025 My Website</p>
    </footer>
</body>
</html>
```

Penjelasan:
```<?= $title ?? 'Default Title' ?>``` → Menampilkan judul halaman, default jika tidak ada.

```<?= $this->renderSection('content') ?>``` → Tempat untuk menampilkan konten dari view lain.

4. Membuat Halaman Home (home.php)
Halaman ini akan menggunakan layout utama (main.php) dan hanya mengisi bagian content.
buat di folder ```app/Views/pages/home.php


<?= $this->extend('layouts/main') ?>
<?= $this->section('content') ?>
    <h2>Welcome to Home Page</h2>
    <p>Ini adalah halaman utama website.</p>
<?= $this->endSection() ?>```

Penjelasan:
```<?= $this->extend('layouts/main') ?> ```→ Menentukan bahwa halaman ini menggunakan template main.php.

```<?= $this->section('content') ?>``` → Mulai bagian konten yang akan dimasukkan ke dalam renderSection('content').

```<?= $this->endSection() ?>``` → Menutup bagian konten.

5. Membuat Halaman About (about.php)
Halaman About juga menggunakan layout yang sama tetapi memiliki isi yang berbeda.

Buat di folder ```app/Views/pages/about.php


<?= $this->extend('layouts/main') ?>
<?= $this->section('content') ?>
    <h2>About Us</h2>
    <p>Ini adalah halaman tentang kami.</p>
<?= $this->endSection() ?>```

6. Menampilkan Halaman di Controller
Kita perlu membuat controller untuk menampilkan halaman-halaman tersebut.

Buat di folder ```app/Controllers/PageController.php


namespace App\Controllers;
use CodeIgniter\Controller;
class PageController extends Controller
{
    public function home()
    {
        return view('pages/home', ['title' => 'Home']);
    }

    public function about()
    {
        return view('pages/about', ['title' => 'About']);
    }
}
```

Penjelasan:
Method home() dan about() akan memanggil view yang sudah dibuat.

Menggunakan ```view('pages/home', ['title' => 'Home'])``` untuk mengisi variabel $title di template utama.

7. Menambahkan Route
Tambahkan route ke dalam app/Config/Routes.php untuk mengakses halaman.
```
$routes->get('/', 'PageController::home');
$routes->get('/about', 'PageController::about');```

8. Kesimpulan
Extend content di CodeIgniter 4 memungkinkan kita membuat template utama dan menggunakan ulang layout di berbagai halaman.

Gunakan extend() dan section() untuk mengisi konten dalam template utama.
Dengan cara ini, kode menjadi lebih rapi, terstruktur, dan mudah dikelola. Dengan teknik ini, kamu bisa mengembangkan aplikasi web yang lebih modular dan efisien.
