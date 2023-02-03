# Apa itu "Clean Code"?

Clean code adalah konsep dalam pengembangan perangkat lunak yang mengacu pada kode yang mudah dibaca, dipahami, dan dipertahankan. Hal ini ditandai dengan kode yang terorganisir dengan baik, dapat dibaca, dan dapat dijelaskan sendiri yang mengikuti konvensi pemrograman yang ditetapkan dan praktik terbaik.

Clean code sering dibandingkan dengan kode yang berantakan atau kode yang sulit dibaca dan dipahami. Kode yang bersih akan membuat proses pengembangan lebih efisien karena lebih mudah untuk dikembangkan, diperbaiki, dan dikelola.

Secara umum, Clean code dapat diidentifikasi dengan beberapa ciri seperti :

* Memiliki nama yang sesuai dengan fungsinya
    
* Memiliki fungsi yang singkat dan fokus pada satu tugas saja
    
* Memiliki indentasi dan pengaturan yang baik
    
* Memiliki komentar yang sesuai dan tidak berlebihan
    
* Memiliki struktur yang mudah diikuti dan dipahami
    

Secara keseluruhan, Clean code sangat penting untuk memastikan kode yang dikembangkan dapat digunakan dengan baik dan efisien selama jangka waktu yang lama. Hal ini akan membuat proses pengembangan lebih efisien dan mengurangi biaya pemeliharaan dalam jangka panjang.

Salah satu contoh dari clean code adalah fungsi untuk menghitung rata-rata dari sekumpulan angka:

```javascript
function calculateAverage(numbers) {
    let sum = 0;
    for (const number of numbers) {
        sum += number;
    }
    return sum / numbers.length;
}
```

Pada contoh diatas, fungsi `calculateAverage` memiliki nama yang sesuai dengan fungsinya, memiliki fungsi yang singkat dan fokus pada satu tugas saja, memiliki indentasi dan pengaturan yang baik, dan tidak memiliki komentar yang berlebihan. Selain itu, variabel yang digunakan juga memiliki nama yang jelas dan mudah dipahami.

Contoh lain yaitu sebuah class untuk mewakili sebuah produk:

```javascript
class Product {
    constructor(name, price) {
        this._name = name;
        this._price = price;
    }
    getName() {
        return this._name;
    }
    setName(name) {
        this._name = name;
    }
    getPrice() {
        return this._price;
    }
    setPrice(price) {
        this._price = price;
    }
}
```

Pada contoh diatas, class `Product` memiliki nama yang sesuai dengan fungsinya, fungsi setter dan getter yang singkat dan fokus pada satu tugas saja, memiliki indentasi dan pengaturan yang baik, dan tidak memiliki komentar yang berlebihan. Selain itu, variabel yang digunakan juga memiliki nama yang jelas dan mudah dipahami.