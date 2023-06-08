---
title: "Integrasi Cloudinary dengan Laravel"
seoDescription: "Cloudinary adalah sebuah layanan manajemen media berbasis cloud yang menyediakan berbagai fitur seperti penyimpanan, pengelolaan, dan pengiriman media (gamb"
datePublished: Thu Jun 08 2023 15:14:11 GMT+0000 (Coordinated Universal Time)
cuid: clina4dzo00030ajwb6ttfjrr
slug: integrasi-cloudinary-dengan-laravel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686237184138/f4a31892-723a-4c21-bbd9-d31225ddc4cb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686237235560/cc4c5c06-385d-443c-a18b-ddf3a38b142f.png
tags: cloud, laravel, cloudinary

---

Cloudinary adalah sebuah layanan manajemen media berbasis cloud yang menyediakan berbagai fitur seperti penyimpanan, pengelolaan, dan pengiriman media (gambar, video, dll.) secara efisien. Integrasi Cloudinary dengan Laravel memungkinkan Anda untuk mengunggah, mengelola, dan menampilkan media menggunakan layanan Cloudinary di dalam aplikasi Laravel Anda. Artikel ini akan membahas langkah-langkah untuk mengintegrasikan Cloudinary dengan Laravel.

## **Langkah 1: Instalasi**

Langkah pertama adalah menginstal paket Cloudinary Laravel yang menyediakan integrasi Laravel dengan Cloudinary. Buka terminal Anda dan arahkan ke direktori proyek Laravel, lalu jalankan perintah berikut:

```plaintext
composer require cloudinary/cloudinary-laravel
```

Paket ini akan menginstal dependensi yang diperlukan dan menambahkan Cloudinary Laravel ke proyek Anda.

## **Langkah 2: Konfigurasi**

Setelah menginstal paket Cloudinary Laravel, Anda perlu mengkonfigurasinya dengan kredensial Cloudinary Anda. Buka file `.env` dalam proyek Laravel Anda dan tambahkan informasi kredensial Cloudinary sebagai variabel lingkungan, seperti berikut:

```plaintext
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

Pastikan Anda mengganti `your_cloud_name`, `your_api_key`, dan `your_api_secret` dengan nilai yang sesuai dari akun Cloudinary Anda.

## **Langkah 3: Mengunggah Gambar ke Cloudinary**

Setelah melakukan konfigurasi, Anda dapat menggunakan Cloudinary untuk mengunggah gambar dari aplikasi Laravel. Berikut adalah contoh kode untuk mengunggah gambar ke Cloudinary menggunakan Cloudinary Laravel:

```php
use CloudinaryLabs\CloudinaryLaravel\Facades\Cloudinary;
use Illuminate\Http\Request;

public function uploadImage(Request $request)
{
    $imagePath = $request->file('image')->getRealPath();

    $result = Cloudinary::upload($imagePath);

    // Dapatkan informasi hasil unggahan
    $publicId = $result->getPublicId();
    $url = $result->getSecurePath();

    // Lakukan sesuatu dengan informasi hasil unggahan, seperti menyimpan URL atau ID gambar di database

    return response()->json([
        'message' => 'Gambar berhasil diunggah',
        'public_id' => $publicId,
        'url' => $url
    ]);
}
```

Pastikan Anda telah mengimpor namespace yang diperlukan, seperti `use CloudinaryLabs\CloudinaryLaravel\Facades\Cloudinary;` dan `use Illuminate\Http\Request;`, pada file controller Anda.

Dalam contoh di atas, kita menggunakan metode `upload()` dari facade `Cloudinary` untuk mengunggah gambar yang diberikan dalam permintaan (`Request`). Hasil unggahan berisi informasi seperti `public_id` (ID gambar di Cloudinary) dan `url` (URL gambar yang dapat diakses).

## **Langkah 4: Menampilkan Gambar dari Cloudinary**

untuk menampilkan gambar dari Cloudinary dalam aplikasi Laravel, Anda dapat menggunakan URL gambar yang diperoleh saat mengunggah gambar. Berikut adalah contoh penggunaannya dalam tag HTML `<img>`:

```xml
<img src="{{ $url }}" alt="Gambar">
```

Pastikan untuk mengganti `{{ $url }}` dengan variabel yang berisi URL gambar yang diperoleh dari hasil unggahan Cloudinary.

Anda juga dapat menambahkan atribut `width` dan `height` pada tag `<img>` untuk menentukan dimensi gambar yang ingin ditampilkan:

```xml
<img src="{{ $url }}" alt="Gambar" width="300" height="200">
```

Dalam contoh di atas, gambar akan ditampilkan dengan lebar 300 piksel dan tinggi 200 piksel. Anda dapat menyesuaikan nilai lebar dan tinggi sesuai kebutuhan Anda.

Selain itu, Anda dapat menggunakan fitur-fitur Cloudinary seperti transformasi gambar untuk mengubah ukuran, memotong, mengompres, atau menerapkan efek pada gambar yang ditampilkan. Anda dapat melihat dokumentasi Cloudinary untuk mempelajari lebih lanjut tentang transformasi gambar yang tersedia.

Dengan menggunakan langkah-langkah di atas, Anda dapat mengintegrasikan Cloudinary dengan Laravel untuk mengunggah, mengelola, dan menampilkan gambar dalam aplikasi Anda. Hal ini akan memungkinkan Anda untuk mengoptimalkan pengelolaan media dan memanfaatkan fitur-fitur yang disediakan oleh Cloudinary.