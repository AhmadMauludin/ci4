## Panduan Praktikum P. Web CodeIgniter 4
1.	Unduh package codeigniter4, ekstrak ambil folder yang di dalam lalu rename dengan **nama_aplikasi** dan simpan pada folder htdocs.
2.	Buka file app/Config/Routes.php ubah kodenya dengan kode berikut (Routes.php)
3.	Rename file env menjadi .env lalu ubah seluruh isinya dengan kode berikut (.env)
4.	Pindahkan semua file yang ada dalam folder **public** ke root folder aplikasinya (dalam folder **nama_aplikasi**)
5.	Buka file index.php yang sudah dipindah, ubah bagian `require FCPATH . '../app/Config/Paths.php';` menjadi `require FCPATH . 'app/Config/Paths.php';`
6.	Buka file app/Config/App.php lalu ubah bagian `'http://localhost:8080/'` Menjadi `'http://localhost:80/cruds2/'` atau `'http://localhost/cruds2/'` atau `'http://localhost:6969/cruds2/'` 
7.	Buka file app/Config/Paths.php tambahkan `public string $publicDirectory = __DIR__ . '/../';`
   Di bawah `public string $viewDirectory = __DIR__ . '/../Views';`
8.	Buat file baru (controller) bernama Barang.php pada folder app/Controllers isi dengan kode berikut (Barang.php)
9.	Buat file baru (model) bernama Barang_model pada folder app/Models isikan dengan kode berikut (Barang_model.php)
10.	Buat 2 file pada folder app/Views bernama header_view.php dan footer_view.php isikan dengan kode berikut (header_view.php dan footer_view.php)
11.	Buat folder baru bernama **barang** di dalam folder app/Views
12.	Buat 3 file baru pada folder barang tersebut berupa : barang_view.php edit_view.php dan tambah_view.php Masukan kode berikut ke dalam file sesuai dengan nama filenya.
