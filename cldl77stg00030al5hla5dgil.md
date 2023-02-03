# YUK, Pahami Konsep  Asynchronous pada JavaScript

sebelum kita masuk ke pembahasan, yuk kita cari tahu dulu perbedaan syncronus dengan asyncronus

Synchronous adalah metode yang menunggu tugas selesai sebelum melanjutkan ke tugas berikutnya. Dalam hal ini, tugas-tugas harus dijalankan dalam urutan yang ditentukan. Jika tugas tergantung pada tugas lain, maka tugas tergantung harus menunggu tugas yang dibutuhkan selesai terlebih dahulu.

```javascript
//Synchronous Example
console.log("Starting function");

function printMessage() {
  console.log("This is a synchronous message");
}

printMessage();

console.log("Ending function");
```

Dalam contoh ini, console.log() dipanggil secara berurutan dan printMessage() dipanggil setelah console.log() pertama dipanggil dan selesai dieksekusi. Setelah printMessage() selesai dieksekusi, console.log() berikutnya dipanggil. Proses ini dilakukan secara berurutan dan menunggu setiap tugas selesai sebelum melanjutkan ke tugas berikutnya.

Synchronous biasanya lebih mudah dipahami dan digunakan karena memiliki aliran kode yang jelas dan mudah diprediksi. Namun, synchronous juga memiliki kelemahan karena menunggu tugas selesai sebelum melanjutkan ke tugas berikutnya, sehingga aplikasi menjadi tidak responsif selama tugas sedang berlangsung.

Asynchronous adalah metode yang tidak menunggu tugas selesai sebelum melanjutkan ke tugas berikutnya. Dalam hal ini, tugas-tugas dapat dijalankan pada saat yang sama tanpa tergantung pada tugas lain. Jika tugas membutuhkan hasil dari tugas lain, maka tugas tersebut dapat meminta hasil setelah tugas yang dibutuhkan selesai.

JavaScript memiliki beberapa cara untuk melakukan operasi asynchronous, di antaranya adalah:

* Callbacks: fungsi yang didefinisikan dan disediakan sebagai argumen untuk operasi asynchronous. Fungsi ini akan dipanggil setelah operasi selesai.
    
    ```javascript
    // Callback Example
    function fetchData(callback) {
      setTimeout(() => {
        callback({ data: "Data fetched!" });
      }, 2000);
    }
    
    fetchData((response) => {
      console.log(response.data);
    });
    
    console.log("After fetching data");
    ```
    
* Promises: objek yang mewakili operasi asynchronous yang sedang berlangsung atau yang telah selesai. Anda dapat mengonfigurasi pengobatan yang akan dilakukan saat operasi selesai.
    
    ```javascript
    // Promise Example
    function fetchData() {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve({ data: "Data fetched!" });
        }, 2000);
      });
    }
    
    fetchData()
      .then((response) => {
        console.log(response.data);
      })
      .catch((error) => {
        console.error(error);
      });
    
    console.log("After fetching data");
    ```
    
* Async/await: fitur baru dalam JavaScript yang membuat penulisan kode asynchronous menjadi lebih mudah dibaca dan dipahami. Kode menjadi mirip dengan kode sincron.
    
    ```javascript
    // Async/await Example
    async function fetchData() {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          resolve({ data: "Data fetched!" });
        }, 2000);
      });
    }
    
    async function main() {
      const response = await fetchData();
      console.log(response.data);
    }
    
    main();
    console.log("After fetching data");
    ```
    

Menggunakan asynchronous JavaScript sangat penting untuk membuat aplikasi yang responsif dan memiliki performa yang baik, karena ini memungkinkan aplikasi untuk melanjutkan tugas lain selama operasi yang memakan waktu lama sedang berlangsung. Asynchronous lebih cocok untuk tugas yang memakan waktu lama seperti memuat data dari server, memproses data, atau membuat animasi. Karena tugas-tugas dapat dijalankan pada saat yang sama, aplikasi dapat terus responsif dan memiliki performa yang baik.