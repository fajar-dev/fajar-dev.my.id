# XSS  (Cross-Site Scripting): bahaya dan cara pencegahannya

hmm.. berbicara mengenai security, XSS (Cross-Site Scripting) merupakan salah satu celah keamanan yang paling banyak di temui pada website <s>pemerintahan</s> indonesia.  
awas ada kang bakso...mwhehe

XSS atau Cross-Site Scripting... (loh bukannya disingkat jadi CSS).  
CSS itu Cascading Style Sheet (singkatnnya udah kepake)

oke.. kembali ke topik.

XSS (Cross-Site Scripting) adalah jenis serangan yang mengeksploitasi kerentanan pada aplikasi web. Serangan ini memungkinkan penyerang untuk memasukkan kode berbahaya ke dalam halaman web yang dikunjungi oleh pengguna. Kode ini bisa melakukan berbagai hal, seperti:

1. Mencuri informasi pribadi: Penyerang dapat mencuri informasi pribadi seperti nama pengguna, kata sandi, alamat email, dan informasi pembayaran.
    
2. Memanipulasi halaman web: Penyerang dapat memanipulasi halaman web untuk menampilkan pesan palsu atau memanipulasi konten.
    
3. Menginject malware: Penyerang dapat menginject malware ke komputer pengguna melalui halaman web yang dikunjungi.
    
4. Menyebar virus: Serangan XSS bisa menyebar virus ke banyak pengguna dengan cepat.
    
5. Menurunkan kepercayaan pengguna: Serangan XSS bisa menurunkan kepercayaan pengguna pada aplikasi web dan mempengaruhi reputasi bisnis.
    

Serangan XSS sangat berbahaya karena memanfaatkan kepercayaan pengguna pada halaman web yang mereka kunjungi. Oleh karena itu, penting bagi Developer web untuk melakukan pencegahan serangan XSS dan memastikan bahwa aplikasi mereka aman dari serangan ini. ada dua jenis serangan XSS:

## Stored XSS

Serangan ini terjadi ketika kode berbahaya disimpan pada server dan diteruskan ke setiap pengguna yang mengakses halaman web yang terkena serangan. Serangan ini sangat berbahaya karena kode berbahaya akan terus beredar selama kode tersebut tidak dihapus.

## Reflected XSS

Serangan ini terjadi ketika kode berbahaya diteruskan melalui URL dan mempengaruhi halaman web yang sedang dikunjungi oleh pengguna. Serangan ini tidak memiliki efek jangka panjang seperti Stored XSS, tetapi masih memiliki potensi bahaya.

nahh.. bagaimana sih cara mencegah website kita dari serangan xss?  
sini aku kasih tau tips nya, ada beberapa poin yang harus kamu perhatikan dalam development website :

1. Validasi input: Pastikan untuk memvalidasi semua input dari pengguna sebelum disimpan atau diteruskan ke sistem.
    
2. Sanitisasi input: Sanitisasi input adalah proses membersihkan input dari karakter berbahaya seperti tag HTML, script, atau karakter escape.
    
3. Escape output: Escape output adalah proses mengubah input yang tidak aman menjadi string aman yang tidak dapat diinterpretasikan oleh browser sebagai kode.
    
4. Input dalam bentuk kode: Jika memungkinkan, pastikan untuk menyimpan data dalam bentuk kode, bukan teks biasa.
    
5. Menonaktifkan eval(): Jangan menggunakan eval() karena itu membuat aplikasi Anda rentan terhadap serangan XSS.
    
6. Filter input: Filter input untuk menghapus karakter yang tidak aman.
    
7. Gunakan HTTP-only cookies: Gunakan HTTP-only cookies untuk menghindari serangan XSS.
    
8. Gunakan Content Security Policy (CSP): Gunakan CSP untuk membatasi skrip yang bisa dijalankan oleh browser.
    
9. Gunakan sandi box: Gunakan sandi box untuk membatasi kode yang bisa dijalankan oleh browser.
    
10. Periksa keamanan secara berkala: Periksa keamanan aplikasi Anda secara berkala untuk memastikan bahwa tidak ada kerentanan baru.
    

Dengan mengikuti langkah-langkah ini, kamu dapat memproteksi aplikasi web kamu dari serangan XSS dan memberikan pengalaman yang aman bagi pengguna.

*semoga membantu :)*  
*Subscribe untuk dapet informasi menarik lainnya....*