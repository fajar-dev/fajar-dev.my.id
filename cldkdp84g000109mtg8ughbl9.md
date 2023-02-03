# JWT (JSON Web Token) :  Kenalan yuk dengan teknologi yang satu ini

JSON Web Token (JWT) adalah standar industri yang digunakan untuk mengatasi masalah autentikasi dan pengenalan dalam aplikasi web. JWT mengandung informasi yang dapat digunakan untuk memverifikasi identitas pengguna atau aplikasi pihak ketiga. Informasi tersebut tersimpan sebagai string JSON yang dikodekan dengan Base64 dan ditandatangani menggunakan algoritma enkripsi seperti HMAC atau RSA.

Ketika pengguna melakukan autentikasi dengan aplikasi, aplikasi mengirimkan JWT ke pengguna yang dapat digunakan untuk memverifikasi identitas pengguna pada permintaan berikutnya. JWT biasanya disimpan di cookie atau header HTTP, dan dapat diteruskan antar aplikasi pihak ketiga untuk memverifikasi identitas pengguna.

Keuntungan menggunakan JWT adalah mudah digunakan dan tidak memerlukan database untuk menyimpan informasi sesi. JWT juga dapat diteruskan antar aplikasi dan platform sehingga mempermudah integrasi aplikasi. Namun, JWT tidak memberikan solusi keamanan yang kuat terhadap serangan seperti injeksi SQL, XSS, atau CSRF, sehingga harus diterapkan dengan benar dan diimplementasikan dengan bijak.

Token JWT terdiri dari tiga bagian: header, payload, dan signature.

```json
//Header
{
  "alg": "HS256",
  "typ": "JWT"
}
```

```json
//Payload
{
  "uid": "123",
  "name": "fajar-dev",
  "role": "admin"
}
```

```javascript
//Signature
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
)
```

```javascript
//Output Result
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1aWQiOiIxMjMiLCJuYW1lIjoiZmFqYXItZGV2Iiwicm9sZSI6ImFkbWluIn0.SGDTjyEBt_GlDgav1OASGo-M_T7jjNpW4jPGD7Cxef8
```

Header menyimpan informasi tentang enkripsi yang digunakan, sementara payload menyimpan informasi yang dapat diteruskan seperti ID pengguna, nama pengguna, dan role pengguna. Signature adalah string hasil dari proses enkripsi header dan payload.

**Terus... apa bedanya jwt dengan php session?**

PHP Session dan JSON Web Token (JWT) adalah dua teknologi yang digunakan untuk mengatasi masalah autentikasi dan pengenalan dalam aplikasi web. Kedua teknologi ini memiliki kelebihan dan kekurangan yang berbeda. Berikut adalah perbedaan antara PHP Session dan JWT.

1. Penyimpanan: PHP Session menyimpan informasi sesi dalam server, sementara JWT menyimpan informasi sebagai string JSON yang dikodekan dan ditandatangani secara enkripsi.
    
2. Keamanan: PHP Session biasanya tidak aman karena informasi sesi dapat dicuri dengan mudah jika tidak diterapkan dengan benar. JWT memiliki keamanan yang lebih baik karena informasi disimpan secara terproteksi oleh enkripsi, tetapi masih dapat dicuri jika implementasi JWT tidak benar.
    
3. Integrasi: PHP Session hanya dapat digunakan dalam aplikasi PHP, sementara JWT dapat digunakan dalam berbagai aplikasi dan platform karena informasi disimpan sebagai string yang dapat diteruskan.
    
4. Performa: PHP Session memiliki performa yang lebih rendah karena harus mengakses informasi sesi dalam server setiap kali pengguna melakukan permintaan, sementara JWT memiliki performa yang lebih baik karena tidak memerlukan akses ke server.
    
5. Ukuran: PHP Session biasanya memiliki ukuran yang lebih besar karena menyimpan informasi sesi dalam server, sementara JWT memiliki ukuran yang lebih kecil karena informasi disimpan sebagai string.
    

Secara umum, PHP Session dan JWT memiliki kelebihan dan kekurangan yang berbeda. PHP Session lebih baik untuk aplikasi yang memerlukan penyimpanan informasi sesi yang aman, tetapi memiliki performa yang lebih rendah. JWT lebih baik untuk aplikasi yang memerlukan integrasi dengan aplikasi lain dan memiliki performa yang lebih baik, tetapi memiliki keamanan yang kurang baik. Aplikasi harus mempertimbangkan kebutuhan mereka dan memilih teknologi yang sesuai untuk memastikan aplikasi mereka berfungsi dengan baik.