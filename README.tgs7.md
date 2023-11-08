**Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?**

Stateless widget adalah widget yang tidak berubah sedangkan stateful widget adalah widget yang dapat berubah. Perubahan yang dimaksud di sini adalah value yang terdapat di dalam widget tersebut. Pada stateless widget value yang ada di widget tersebut sudah didefinisikan sejak awal, sedangkan pada stateful widget, value yang ada pada widget tersebut dapat berubah sepanjang jalannya aplikasi.

**Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.**

1. MyApp
Custom widget yang berguna sebagai entry point pertama pada projek ini
2. MaterialApp
Berguna untuk mengatur konfigurasi global dari projek
3. MyHomePage
Custom widget untuk menampilkan home page dari aplikasi
4. Scaffold
Berguna untuk mengatur tata letak dasar dari aplikasi
5. SingleChildScrollView
Berfungsi agar tampilan yang ada di dalam widget ini dapat di-scroll
6. Column
Berfungsi untuk menampilkan elemen secara vertikal
7. Text
Berfungsi untuk menampilkan teks
8. Gridview
Berfungsi untuk membuat grid layout
9. ShopCard
Custom widget untuk menampilkan kartu dengan ikon dan teks di dalamnya
10. Material
Berguna untuk mengatur tampilan widget yang ada di dalamnya
11. InkWell
Membuat area tertentu responsif terhadap sentuhan pengguna
12. ScankBar
Menampilkan pesan singkat setelah area "InkWell" ditekan
13. Icon
Berguna untuk menampilkan icon
14. Container
Mengatur letak dan tampilan widget di dalamnya

**Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step.**
1. Membuat file main.dart sebagai entry point projek
2. Membuat file home.dart sebagai tampilan home page dari projek
3. Mengisi file main.dart dengan kode berikut
```
import 'package:flutter/material.dart';
import 'package:mobile_inventory/home.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Mobile Inventory',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
        useMaterial3: true,
      ),
      home: MyHomePage(),
    );
  }
}
``` 
4. Mengisi file home.dart dengan kode berikut
```
import 'package:flutter/material.dart';

class MyHomePage extends StatelessWidget {
    MyHomePage({Key? key}) : super(key: key);

    final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.amber),
    ShopItem("Tambah Item", Icons.add_shopping_cart, const Color.fromARGB(255, 108, 174, 228)),
    ShopItem("Logout", Icons.logout, const Color.fromARGB(255, 194, 20, 20)),
    ];

    @override
    Widget build(BuildContext context) {
        return Scaffold(
        appBar: AppBar(
        backgroundColor: Colors.indigo,
        title: const Text(
          'Mobile Inventory',
        ),
      ),
      body: SingleChildScrollView(
        // Widget wrapper yang dapat discroll
        child: Padding(
          padding: const EdgeInsets.all(10.0), // Set padding dari halaman
          child: Column(
            // Widget untuk menampilkan children secara vertikal
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                // Widget Text untuk menampilkan tulisan dengan alignment center dan style yang sesuai
                child: Text(
                  "Your Inventory", // Text yang menandakan toko
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              // Grid layout
              GridView.count(
                // Container pada card kita.
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  // Iterasi untuk setiap item
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
    }
}

class ShopItem {
  final String name;
  final IconData icon;
  final Color? color;

  ShopItem(this.name, this.icon, this.color);
}

class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key}); // Constructor

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        child: Container(
          // Container untuk menyimpan Icon dan Text
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```