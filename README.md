# **Bola AE**

# TUGAS 7

# 1. Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.

Widget tree adalah representasi logis dari seluruh elemen antarmuka (UI) pada aplikasi Flutter. Semua widget (seperti Text, Button, Column, dan Scaffold) disusun dalam bentuk struktur hierarki seperti pohon — di mana setiap node adalah sebuah widget.

Setiap widget bisa memiliki parent (induk) dan child (anak):
- Parent widget bertugas mengatur tata letak (layout) dan perilaku dari anak-anaknya.
- Child widget mewarisi sifat dari parent-nya dan ditempatkan di dalamnya.

# 2. Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.

| **Widget**                                                                                   | **Fungsi**                                                                                                                                          |
| -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **MaterialApp**                                                                              | Menjadi *root widget* aplikasi berbasis Material Design. Mengatur tema, navigasi, dan halaman awal aplikasi.                                        |
| **Scaffold**                                                                                 | Menyediakan struktur dasar tampilan aplikasi seperti `AppBar`, `Body`, `FloatingActionButton`, dll. Pada proyek ini menjadi kerangka utama halaman. |
| **AppBar**                                                                                   | Menampilkan bilah atas (top bar) dengan judul “Bola AE”. Menggunakan `Text` sebagai anaknya.                                                        |
| **Text**                                                                                     | Menampilkan teks statis di layar, misalnya untuk judul (`"Bola AE"`) dan pesan sambutan (`"Selamat datang di Bola AE"`).                            |
| **Padding**                                                                                  | Memberikan jarak di sekitar elemen UI agar tata letak lebih rapi, misalnya `Padding(all: 16.0)` pada body.                                          |
| **Column**                                                                                   | Menyusun widget secara vertikal. Digunakan untuk menampilkan elemen-elemen seperti baris `InfoCard` dan grid `ItemCard`.                            |
| **Row**                                                                                      | Menyusun widget secara horizontal. Pada kode ini digunakan untuk menampilkan tiga kartu informasi: NPM, Name, dan Class.                            |
| **InfoCard (Custom Widget)**                                                                 | Widget buatan sendiri yang menampilkan informasi berupa *title* dan *content* di dalam sebuah `Card`.                                               |
| **Card**                                                                                     | Widget Material Design yang memberikan efek *elevation* (bayangan) untuk tampilan seperti kartu.                                                    |
| **Container**                                                                                | Digunakan untuk membungkus elemen agar bisa diberi padding, lebar, atau dekorasi tambahan.                                                          |
| **GridView.count**                                                                           | Menampilkan daftar elemen (`ItemCard`) dalam format grid dengan jumlah kolom tetap (`crossAxisCount: 3`).                                           |
| **ItemCard (Custom Widget)**                                                                 | Widget buatan sendiri yang menampilkan setiap item pada halaman utama dengan warna, ikon, dan teks yang berbeda.                                    |
| **Material**                                                                                 | Memberikan efek material seperti *ink splash* saat pengguna menekan elemen. Diperlukan agar `InkWell` dapat bekerja.                                |
| **InkWell**                                                                                  | Membuat area dapat diklik (tappable). Saat ditekan, akan memunculkan pesan `SnackBar`.                                                              |
| **Icon**                                                                                     | Menampilkan ikon dari pustaka `Icons`, misalnya `Icons.shopping_bag` atau `Icons.storefront`.                                                       |
| **SnackBar**                                                                                 | Menampilkan notifikasi sementara di bagian bawah layar setiap kali tombol ditekan (`"Kamu telah menekan tombol ..."`).                              |
| **SizedBox**                                                                                 | Memberikan jarak vertikal antar elemen (contohnya `SizedBox(height: 16.0)`).                                                                        |
| **Center**                                                                                   | Menempatkan widget di tengah parent-nya. Digunakan agar teks dan grid berada di posisi tengah layar.                                                |
| **MediaQuery**                                                                               | Digunakan untuk mendapatkan ukuran layar perangkat (`MediaQuery.of(context).size.width`) agar lebar `InfoCard` proporsional.                        |
| **Theme.of(context)**                                                                        | Mengambil skema warna dari tema aplikasi untuk mengatur `AppBar`.                                                                                   |

# 3. Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.

MaterialApp berfungsi sebagai root widget dalam aplikasi Flutter berbasis Material Design.
Beberapa fungsinya:
- Mengatur tema global aplikasi (theme, darkTheme).
- Menentukan halaman awal (home).
- Menyediakan sistem navigasi berbasis Route.
- Mengaktifkan fitur seperti debugShowCheckedModeBanner.
Widget ini sering dijadikan root karena menjadi pembungkus utama yang menyediakan konteks tema dan navigasi bagi seluruh widget di bawahnya

# 4. Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?

| Jenis               | Ciri                                                                                | Contoh Penggunaan                               |
| ------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------- |
| **StatelessWidget** | Tidak memiliki state; tampilannya tetap kecuali ada perubahan dari parent.          | Menampilkan teks statis atau ikon tetap.        |
| **StatefulWidget**  | Memiliki state yang bisa berubah seiring waktu; membutuhkan kelas `State` terpisah. | Tombol counter, form input, animasi interaktif. |


# 5. Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?

BuildContext adalah objek yang merepresentasikan posisi widget dalam widget tree.
Objek ini penting karena digunakan untuk:
- Mengakses informasi dari parent (misalnya Theme.of(context) atau Navigator.of(context)).
- Menghubungkan widget dengan elemen lain dalam tree saat proses build berlangsung.
Dalam metode build(BuildContext context), parameter context memberikan referensi ke lokasi widget dalam struktur pohon aplikasi, memungkinkan komunikasi dengan widget lain

# 6. Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".

| Fitur            | Penjelasan                                                                                                                             | Dampak pada State                            |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Hot Reload**   | Menyuntikkan perubahan kode ke dalam aplikasi yang sedang berjalan, lalu membangun ulang widget tree tanpa menjalankan ulang `main()`. | State aplikasi tetap **dipertahankan**.      |
| **Hot Restart**  | Memuat ulang kode dan menjalankan ulang seluruh aplikasi dari awal (`main()` dijalankan kembali).                                      | State aplikasi **hilang** dan dimulai ulang. |
| **Full Restart** | Memulai ulang seluruh aplikasi dan melakukan kompilasi ulang native code (lebih lama).                                                 | Semua state dan cache **dihapus**.           |

# TUGAS 8

# 1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?

- __`Navigator.push():`__
  
  Menambahkan halaman baru di atas stack tanpa menghapus halaman sebelumnya.
  
  __Contoh:__ Digunakan ketika ingin berpindah ke halaman lain tetapi tetap memungkinkan pengguna kembali ke halaman sebelumnya.

- __`Navigator.pushReplacement():`__
  
  Mengganti halaman saat ini dengan halaman baru (halaman lama dihapus dari stack).
  
  __Contoh:__ Digunakan ketika kamu tidak ingin pengguna kembali ke halaman sebelumnya, misalnya setelah melakukan aksi penting seperti login atau logout.

# 2. Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?
Dalam Flutter, setiap halaman dibangun dari hierarki widget, dan tiga komponen penting untuk halaman aplikasi yang konsisten adalah:
- Scaffold – kerangka utama tiap halaman.
- AppBar – bagian atas halaman (biasanya untuk judul dan tombol navigasi).
- Drawer – panel navigasi samping untuk berpindah antar-halaman.

---
1. `Scaffold`: Pondasi Tiap Halaman
Scaffold adalah widget utama yang menyediakan struktur dasar halaman seperti:
- AppBar (header)
- Drawer (menu samping)
= Body (konten utama)
- FloatingActionButton
- BottomNavigationBar
Dengan Scaffold, kamu memastikan semua halaman memiliki tata letak dan perilaku yang konsisten.  

💡 Kegunaannya:
- Semua halaman (HomePage, ProductFormPage, ProductDetailPage) memakai Scaffold.
- Pengguna langsung mengenali pola tampilan aplikasi.
- Transisi halaman terasa mulus tanpa perubahan besar pada layout.

2. `AppBar`: Identitas & Navigasi
AppBar berfungsi sebagai header konsisten di setiap halaman.

💡 Kegunaannya:
- Memberikan judul halaman yang jelas.
- Menyediakan tombol aksi spesifik (misalnya tambah produk atau pencarian).
- Memberi nuansa konsisten di seluruh halaman (warna, tinggi, font, dll).

3. `Drawer`: Navigasi Konsisten
Drawer adalah panel geser dari sisi kiri layar yang berisi daftar menu ke halaman lain.

💡 Kegunaannya:
- Menyediakan navigasi cepat antar-halaman.
- Terlihat seragam di seluruh aplikasi, cukup buat satu Drawer dan panggil di setiap halaman.
- Menjaga pengalaman pengguna tetap familiar dan mudah.

# 3. Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.

Dalam konteks desain antarmuka, widget seperti `Padding`, `SingleChildScrollView`, dan `ListView` membantu membuat tampilan form lebih rapi, responsif, dan mudah digunakan.
- `Padding` memberikan jarak antar elemen agar form tidak tampak padat dan lebih nyaman dibaca.
- `SingleChildScrollView` memungkinkan pengguna menggulir halaman ketika form terlalu panjang, terutama saat keyboard muncul.
- `ListView` berguna untuk menampilkan banyak elemen form secara dinamis dengan kemampuan scroll otomatis.

Contohnya, pada aplikasi *Bola Ae*, halaman `AddProductPage` menggunakan `Padding` di setiap `TextFormField` agar tampilan rapi, dan `SingleChildScrollView` untuk memastikan seluruh form tetap dapat diakses meskipun kontennya melebihi tinggi layar.

# 4. Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?

Menyesuaikan warna tema berarti membuat seluruh tampilan aplikasi (AppBar, tombol, latar belakang, teks, ikon) mengikuti identitas visual brand toko.

__Contoh 1__:
```python
...
final List<ItemHomepage> items = [
    ItemHomepage("All Products", Icons.shopping_bag, Colors.blue),
    ItemHomepage("My Products", Icons.storefront, Colors.green),
    ItemHomepage("Create Product", Icons.add, Colors.red),
  ];
...
class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color;

  ItemHomepage(this.name, this.icon, this.color);
}
...
```
__Contoh 2__:
```python
theme: ThemeData(
         colorScheme: ColorScheme.fromSwatch(primarySwatch: Colors.blue).copyWith(secondary: Colors.blueAccent[400]),
      ),
