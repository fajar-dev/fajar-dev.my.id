---
title: "Implementasi caching  Laravel menggunakan Redis"
seoDescription: "Caching adalah salah satu teknik yang dapat digunakan untuk meningkatkan kinerja aplikasi."
datePublished: Fri Apr 07 2023 06:21:14 GMT+0000 (Coordinated Universal Time)
cuid: clg65s78r000j09l9f3ws0vpd
slug: implementasi-caching-laravel-menggunakan-redis
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680848371599/dfc130af-9ba7-4ab7-b733-419d02de17b2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1680848436072/f41db5fc-cc4b-49f9-ae7e-1c2bf2d04bf4.png
tags: laravel, redis, caching

---

Caching adalah salah satu teknik yang dapat digunakan untuk meningkatkan kinerja aplikasi. Dalam pengembangan aplikasi web, caching dapat membantu mengurangi waktu akses ke database dan mempercepat waktu loading halaman. Salah satu cara untuk menerapkan caching di aplikasi Laravel adalah dengan menggunakan Redis.

Redis adalah sebuah database in-memory yang sering digunakan untuk caching. Dalam artikel ini, kita akan membahas cara mudah untuk menerapkan caching di Laravel menggunakan Redis.

## Instal Redis dan Laravel Redis Package

Langkah pertama yang perlu dilakukan adalah menginstal Redis. Anda dapat menginstal Redis menggunakan package manager yang tersedia di sistem operasi Anda.

Setelah Redis berhasil diinstal, selanjutnya Anda perlu menginstal Laravel Redis Package. Anda dapat menginstal package ini dengan menjalankan perintah berikut pada terminal:

```bash
composer require predis/predis
```

## Konfigurasi Redis pada Laravel

Setelah Redis terkonfigurasi pada Laravel, selanjutnya kita dapat menggunakan caching di Laravel dengan mudah. Laravel menyediakan fungsi-fungsi bawaan untuk caching seperti cache(), remember(), dan banyak lagi.

Berikut adalah contoh penggunaan caching pada controller di Laravel:

```php
use Illuminate\Support\Facades\Cache;

class UserController extends Controller
{
    public function index()
    {
        $users = Cache::remember('users', 60, function () {
            return DB::table('users')->get();
        });

        return view('users', ['users' => $users]);
    }
}
```

Pada contoh di atas, kita menggunakan Cache::remember() untuk menyimpan hasil query ke dalam cache selama 60 detik. Jika data telah tersimpan di dalam cache, maka data tersebut akan diambil dari cache dan tidak perlu melakukan query ke database.

## Membersihkan Cache

Setelah Anda menggunakan caching pada aplikasi Laravel Anda, Anda perlu memastikan bahwa cache tidak mengganggu kinerja aplikasi Anda. Anda dapat membersihkan cache pada Laravel dengan menjalankan perintah berikut pada terminal:

```bash
php artisan cache:clear
```

Perintah ini akan membersihkan semua data cache pada aplikasi Laravel Anda.

## Kesimpulan

Dalam artikel ini, kita telah membahas cara mudah untuk menerapkan caching di Laravel menggunakan Redis. Redis adalah database in-memory yang dapat digunakan untuk caching pada aplikasi Laravel. Dengan menggunakan caching, kita dapat mempercepat waktu loading aplikasi dan mengurangi waktu akses ke database. Dalam penggunaannya, Laravel menyediakan fungsi-fungsi bawaan yang dapat digunakan untuk caching seperti cache() dan remember(). Dengan memahami cara menggunakan Redis untuk caching pada Laravel, kita dapat meningkatkan kinerja aplikasi dan memberikan pengalaman pengguna yang lebih baik.

subscribe untuk dapatkan tips & trick lainnya...

*See you next article !!*