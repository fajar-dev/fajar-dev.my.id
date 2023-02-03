# #2 SQL  Injection : bahaya dan cara pencegahannya

Selain XSS, SQL Injection juga merupakan salah satu celah keamanan yang sering di jumpai. Terutama pada website yang masih menggunakan bahasa PHP.

apa sih sql injection itu? mari kita bahas...

SQL Injection adalah sebuah metode keamanan yang memanfaatkan celah dalam pembuatan aplikasi web untuk memasukkan perintah SQL melalui inputan user yang tidak tervalidasi dengan benar. Ini memungkinkan penyerang untuk mengakses dan memanipulasi data dalam database dan bahkan mengambil alih kendali seluruh sistem.

SQL Injection bekerja dengan memasukkan perintah SQL yang tidak diinginkan ke dalam input yang tidak tervalidasi pada aplikasi web. Perintah tersebut akan dieksekusi oleh database sebagai bagian dari perintah SQL yang normal, yang mengakibatkan manipulasi data dan informasi yang tidak diinginkan.

ada beberapa jenis serangan sql injection, yaitu :

1. **Union-based SQL Injection**
    
    Menggunakan UNION SQL untuk menggabungkan hasil dari dua atau lebih query. Ini digunakan untuk mengambil data dari tabel lain yang tidak terlihat.
    
2. **Error-based SQL Injection**
    
    Mencoba membuat query yang salah dan menganalisis respons dari server untuk mengumpulkan informasi tentang database.
    
3. **Blind SQL Injection**
    
    Mirip dengan error-based SQL Injection, tetapi tanpa menampilkan pesan kesalahan. Ini dilakukan dengan menggunakan perintah yang membuat perubahan pada database dan mengukur waktu respon untuk mengumpulkan informasi.
    
4. **Stacked Query SQL Injection**
    
    Menggunakan perintah SQL ganda untuk membuat perubahan pada database. Ini dilakukan dengan menambahkan perintah SQL lain setelah perintah SQL yang ada.
    
5. **Inferential SQL Injection**
    
    Mencoba memperoleh informasi dari database tanpa memanfaatkan pesan kesalahan atau membuat perubahan pada database. Ini dilakukan dengan mengirimkan permintaan yang membuat query merespons dengan cara yang berbeda tergantung pada data yang ada.
    
6. **Second-order SQL Injection**
    
    Mencoba memasukkan data yang memiliki perintah SQL ke dalam database dan memanfaatkan data tersebut setelah diterima oleh aplikasi.
    

sini aku kasih contoh penyerangan sql injection pada form login.  
disini aplikasi web meminta pengguna untuk masukkan username dan password. Jika aplikasi tersebut tidak memvalidasi input dengan benar, penyerang dapat memasukkan perintah SQL.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675445916269/0771bc54-e82d-430c-b98a-fd2234200d77.png align="center")

Perintah ini akan membuat query SQL seperti:

```sql
SELECT * FROM users WHERE username = '' OR 1=1; --' AND password ='anything';
```

pada contoh diatas query akan mengambil semua baris dari tabel "users" karena kondisi "1=1" selalu benar, dan komentar "--" memastikan bahwa bagian dari perintah yang mengecek password tidak dieksekusi. nah... gimana cara mencegahnya?

salah satu cara untuk dapat mencegah terhadap serangan sql injection pada form login adalah melakukan prepared statements

```php
<?php
$username = $_POST['username'];
$password = $_POST['password'];

// Buat prepared statement
$stmt = $koneksi->prepare("SELECT id, username, password FROM users WHERE username = ? AND password = ?");

// Bind parameter ke prepared statement
$stmt->bind_param("ss", $username, $password);

// Eksekusi prepared statement
$stmt->execute();

// Ambil hasil
$result = $stmt->get_result();

// Cek apakah ada data yang cocok
if ($result->num_rows > 0) {
    // Login berhasil
} else {
    // Login gagal
}
?>
```

Dengan menggunakan prepared statements, input dari pengguna akan divalidasi dan dibersihkan sebelum digunakan dalam query SQL. Ini akan memastikan bahwa perintah SQL tidak dapat dimasukkan melalui input dan mengurangi risiko serangan SQL Injection.

**ingat !!** **Ini hanya satu contoh contoh sederhana**. banyak teknik sql injection lainnya yang bisa saja dapat mengakibatkan kerusakan yang lebih besar pada sistem, seperti membaca informasi rahasia, menghapus data, atau bahkan mengambil alih kendali seluruh sistem. Oleh karena itu, sangat penting untuk memastikan bahwa aplikasi web dilindungi terhadap SQL Injection.

berikut beberapa tips yang aku kasih untuk mencegah serangan sql injection:

1. Validasi input, Pastikan bahwa semua input dari pengguna divalidasi dengan benar sebelum digunakan dalam query SQL. Hindari memasukkan input langsung ke dalam query, sebaliknya gunakan parameterized queries atau prepared statements.
    
2. Escape Sequences, Gunakan escape sequences untuk memastikan bahwa input yang mungkin berisi perintah SQL tidak dieksekusi sebagai bagian dari query.
    
3. Least Privilege, Konfigurasikan akun database dengan hak akses minimum yang diperlukan untuk melakukan tugas tertentu. Ini akan membatasi kerusakan yang dapat diterima jika terjadi serangan SQL Injection.
    
4. Patches dan Update, Pastikan bahwa semua sistem dan aplikasi terus-menerus diperbarui dengan patch dan pembaruan keamanan terbaru.
    
5. Monitoring dan Logging, Monitoring aktivitas database secara teratur dan melakukan logging aktivitas untuk membantu mengidentifikasi serangan SQL Injection.
    
6. Pendidikan dan Sensitisasi, Sensitisasi dan pendidikan tentang SQL Injection dan teknik-teknik keamanan lainnya sangat penting bagi semua pengembang dan administrator sistem.
    

Implementasi beberapa atau semua dari cara-cara ini akan membantu mencegah serangan SQL Injection dan memastikan keamanan aplikasi dan sistem kamu.

*Semoga membantu :)  
Subscribe untuk dapatkan informasi menarik lainnya...*