**Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat**

 - Navigator.push() digunakan untuk menambahkan layar baru ke dalam tumpukan navigasi

 - Navigator.pushReplacement() digunakan untuk menambahkan layar baru ke tumpukan navigasi sekaligus mengganti layar saat ini dengan layar yang baru

 - Penggunaan Navigator.push() dan Navigator.pushReplacement() tergantung dengan kebutuhan aplikasi. Jika kita ingin pengguna kembali ke layar sebelumnya maka gunakan Navigator.push, sedangkan jika kita ingin pengguna tidak dapat kembali ke layar sebelumnya maka gunakan Navigator.pushReplacement.


**Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**
1. Single-child Layout Widgets
Widget yang hanya bisa memiliki satu child widget di dalamnya, contoh:
 - Container
 - Center
 - Align
 Widget ini cocok digunakan untuk mengatur tiap layout widget secara independent

 2. Multi-child Layout Widgets
 Widget yang dapat memiliki lebih dari satu child widget di dalamnya, contoh:
 - Row & Column
 - ListView
 Widget ini cocok digunakan jika kita mempunyai beberapa widget yang ingin dikelompokan ke dalam layout yang sama

3. **Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**

Elemen input yang digunakan pada tugas ini adalah `TextFormField`, alasan menggunakan elemen input ini adalah data yang kita butuhkan dari input berupa teks. Selain itu kita juga bisa melakukan validasi input sesuai kebutuhan

4. **Bagaimana penerapan clean architecture pada aplikasi Flutter?**

Penerapan clean architecture pada flutter dapat dilakukan dengan membagi aplikasi menjadi tiga layer, yaitu presentation layer, domain layer, dan data layer. 

Presentation layer adalah bagian yang menampilkan presentasi dari aplikasi kita, hal ini mencakup UI aplikasi dan event handlers dari UI yang dibuat. Domain layer adalah bagian yang mengurus *business logic* dari aplikasi, pada bagian ini kode ditulis hanya dengan flutter hal ini karena bagian ini hanya mementingkan *business logic* dari aplikasi yang dibuat tanpa memikirkan implementasi detailnya. Data layer bagian yang bertanggung jawab untuk pengambilan data dari aplikasi, bagian ini bisa berupa bentuk pemanggilan API ke server dan/atau database lokal.


5. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step!**

1. Membuat drawer menu pada aplikasi untuk navigasi ke layar lain
2. Memasukan widget drawer yang sudah dibuat pada home page
3. Membuat form untuk menambahkan item ke inventory
4. Mengatur navigasi untuk tombol yang ada pada drawer
5. Membuat fungsi untuk memunculkan dialog message saat menyimpan item di form
6. Memberikan navigasi untuk tombol tambah item di home page
7. Melakukan refacor pada aplikasi untuk mengubah struktur dari aplikasi