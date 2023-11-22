**Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?**

Kita tetap bisa melakukan pengambilan data JSON tanpa membuat model terlebih dahulu di flutter. Tetapi terdapat beberapa kekurangan jika kita melakukan pengambilan data JSON tanpa membuat modelnya, seperti kurangnya struktur dari kode kita, rentan terhadap kesalahan, dan kurangnya keamanan.

**Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter**

`CookieRequest` berfungsi untuk menyimpan cookies yang diberikan oleh Django. Instance `CookieRequest` ini perlu dibagikan ke semua komponen di aplikasi flutter kita untuk menyimpan state yang sama. Contoh penggunaan instance ini adalah saat kita ingin melakukan navigasi di aplikasi kita maka kita harus login terlebih dahulu, agar kita tidak perlu login setiap melakukan navigasi maka setiap komponen flutter perlu instance cookies tersebut.

**Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.**

Untuk mengambil data dalam bentuk kita menggunakan library `http`, kemudian kita meng-convert data dersebut menggunakan `dart:convert`. Setelah itu, kita dapat menampilkan data tersebut dpada flutter dengan membuat model berdasarkan data tersebut.

**Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter**
Saat melakukan login kita akan mengirim method POST request ke web django kita, hal ini kita lakukan dengan menggunakan package `pbp_django_auth`. Jika request kita berhasil, maka kita akan masuk ke tampilan home dari aplikasi kita dan mendapatkan cookies, cookies ini berguna untuk melakukan navigasi di aplikasi kita.


**Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.**

1. MaterialApp

Berfungsi untuk mengatur tema, bahasa, dll. 

2. Scaffold

Berfungsi sebagai struktur dasar dari aplikasi, widget ini menyediakan berbagai child widget yang dapat digunakan untuk mengembangkan aplikasi

3. Container

Wisget yang digunakan untuk membungkus widget lain, widget ini dapat mengatur properti tampilan, seperti ukuran, warna, margin, padding, dll.

4. Column

Berfungsi untuk menampilkan child widget secara vertikal

5. TextField

Berfungsi untuk menerima input teks dari pengguna

6. ElevatedButton

Berfungsi untuk menampilkan button dengan efek timbul

7. TextButton

Menampilkan button yang berisi teks

8. ListView

Berfungsi untuk membuat tampilan yang dapat di-scroll dalam bentuk list

9. ListTile

Digunakan di dalam widget ListView dan berfungsi untuk mengatur detail dari item yang ditampilkan dalam list

10. Navigator
Berfungsi untuk mengatur perpindahan layar yang ditampilkan kepada pengguna

**Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step!**

1. Membuat app `authentication` pada project Django dan menambahkan ke `INSTALLED_APPS`.
2. Menjalankan `pip install django-cors-headers` dan menambahkan `corsheaders` ke `INSTALLED_APPS`.
3. Menambahkan kode berikut pada `settings.py`
```
CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOW_CREDENTIALS = True
CSRF_COOKIE_SECURE = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SAMESITE = 'None'
SESSION_COOKIE_SAMESITE = 'None'
```
4. Membuat mehtod `login` pada `authentication/views.py` dan menambahkan routing ke `urls.py` di app dan project
5. Mengistall package `provider` dan `pbp_django_auth` pada flutter
6. Membuat objek `Provider` pada `main` untuk menyediakan `CookieRequest`library ke semua child widgets
7. Membuat file `login.dart` pada folder `screens` dan mengisi file tersebut
8. Mengatur `home:MyHomePage()` pada `main.dart` menjadi `home: LoginPage()`
9. Membuat folder `lib/models` dan membuat file `product.dart` dan mengisinya dengan custom model
10. Melakuakan `flutter pub add http` untuk menambahkan package `http`
11. Menambahkan kode berikut pada `android/app/src/main/AndroidManifest.xml`
```
<!-- Required to fetch data from the Internet. -->
    <uses-permission android:name="android.permission.INTERNET" />
```
12. Membuat file `list_product.dart` pada `lib/screens` dan mengisi file tersebut
13. Menambahkan halaman `list_product.dart` ke `widgets/left_drawer.dart`
14. Membuat navigasi untuk tombol `Lihat Item` pada `inventory_card.dart` agat mengarahkan ke halaman `list_product.dart`
15. Membuat fungsi `create_product_flutter` pada `main/views.py`dan menambahkan path baru pada `main/urls.py`
16. Menghubungkan `shoplist_form.dart` dengan `CookieRequest`
17. Mengubah perintah pada `onPressed: ()`
18. Membuat method `logout` pada `authentication/views.py`
19. Menambahkan path baru pada `authentication/urls.py`
20. Menambahkan kode `final request = context.watch<CookieRequest>();` pada `lib/widgets/inventory_card.dart`
21. Mengatur `response` jika tombol `Logout` dipencet dan memberi message setelahnya.