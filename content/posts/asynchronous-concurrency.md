---
title: "Asynchronous != Concurrency"
date: 2024-03-24
description: "Membedah Perbedaan Asynchronous dan Concurrency"
tags: [go, golang]
---
**Asynchronous != Concurrency**

Hi Gophers,
Sebagai seorang developer backend dengan bahasa pemrograman Go, Anda terus berhadapan dengan kebutuhan untuk mengelola operasi-operasi yang membutuhkan waktu dan menangani banyak permintaan secara bersamaan. Dalam dunia pemrograman modern, terdapat dua konsep yang sering kali menjadi pusat perhatian: Asynchronous dan Concurrency. Dalam artikel ini, kita akan menjelajahi perbedaan mendasar antara keduanya serta menggali bagaimana kedua konsep ini berperan dalam pengembangan aplikasi backend menggunakan Go.

### Apa itu Asynchronous Programming?

Asynchronous programming adalah teknik di mana beberapa tugas dapat dieksekusi secara bersamaan tanpa harus menunggu satu sama lain. Dalam konteks Go, ini biasanya dicapai melalui fitur-fitur seperti goroutines dan channels. Dengan menggunakan asynchronous programming, aplikasi dapat terus menjalankan operasi-operasi yang membutuhkan waktu seperti I/O tanpa harus menghentikan eksekusi program. Ini sangat penting dalam menjaga responsifitas aplikasi, terutama ketika ada tugas-tugas yang memerlukan waktu seperti mengambil data dari database atau melakukan permintaan ke server eksternal.

### Apa itu Concurrency?

Concurrency adalah kemampuan sebuah program untuk menangani banyak tugas secara bersamaan. Dalam Go, concurrency sering kali diimplementasikan menggunakan goroutines, yang merupakan lightweight thread yang dikelola oleh runtime Go. Melalui penggunaan goroutines dan fitur-fitur lain seperti mutex dan waitgroups, Anda dapat membuat aplikasi Anda mampu menangani banyak permintaan secara bersamaan dengan cara yang efisien. Concurrency penting dalam memastikan aplikasi backend Anda dapat bersifat responsif dan dapat menangani beban yang tinggi tanpa mengorbankan performa.

### Perbedaan Utama

Perbedaan mendasar antara asynchronous programming dan concurrency terletak pada fokus utamanya. Asynchronous programming berkaitan dengan cara menangani tugas-tugas yang membutuhkan waktu, sementara concurrency berkaitan dengan kemampuan program untuk menangani banyak tugas secara bersamaan, yang mungkin tidak selalu terkait dengan waktu eksekusi.

**Concurrency:**

- Menjalankan multiple tasks secara bersamaan.
- Tasks dapat dieksekusi secara paralel, bergantian, atau kombinasi keduanya.
- Thread utama dapat diblokir saat menunggu tasks selesai.

**Asynchronous:**
- Menjalankan tasks tanpa memblokir thread utama.
- Thread utama dapat terus berjalan saat menunggu tasks selesai.
- Tasks dapat dijalankan secara paralel, bergantian, atau kombinasi keduanya.

### Contoh Implementasi dalam Go

Dalam Go, asynchronous programming dan concurrency dapat diimplementasikan dengan cara yang berbeda tergantung pada kebutuhan aplikasi Anda. Contoh implementasi asynchronous programming dalam Go termasuk penggunaan goroutines untuk melakukan operasi I/O tanpa memblokir eksekusi program. Sementara itu, contoh implementasi concurrency dapat mencakup penggunaan goroutines dan channel untuk menangani banyak permintaan HTTP secara bersamaan.

**Concurrency**
```go
func main() {
  // Menjalankan dua goroutines secara bersamaan
  go func() {
    // ...
  }()
  go func() {
    // ...
  }()

  // Menunggu kedua goroutines selesai
  time.Sleep(time.Second)
}
```

**Asynchronous**
```go
func main() {
  // Membuat channel untuk menampung hasil
  results := make(chan int)

  // Menjalankan goroutine untuk menghitung nilai
  go func() {
    results <- calculate()
  }()

  // Mendapatkan hasil dari channel
  result := <-results

  // ...
}
```

### Pentingnya Memahami Perbedaan Ini


### Manfaat Concurrency:

- Meningkatkan performa program dengan menjalankan multiple tasks secara bersamaan.
- Meningkatkan scalability program dengan memungkinkan program untuk menangani lebih banyak requests.
- Memanfaatkan resources hardware secara maksimal.

### Kekurangan Concurrency:

- Kompleksitas code meningkat karena perlu mengelola multiple tasks secara bersamaan.
- Potensi terjadinya race conditions dan data inconsistency.
- Membutuhkan debugging yang lebih kompleks.

### Manfaat Asynchronous:

- Meningkatkan responsiveness program karena thread utama tidak diblokir saat menunggu tasks selesai.
- Meningkatkan user experience karena program tetap responsif saat melakukan operasi yang memakan waktu lama.
- Memudahkan implementasi event-driven programming.

### Kekurangan Asynchronous:

- Kompleksitas code meningkat karena perlu mengelola channels, callbacks, dan constructs lainnya.
- Potensi terjadinya memory leaks jika channels tidak di manage dengan benar.
- Membutuhkan debugging yang lebih kompleks.

### Libraries dan Tools untuk Asynchronous dan Concurrency:

1. Goroutines: Lightweight threads yang disediakan oleh Golang untuk menjalankan tasks secara bersamaan.
2. Channels: Digunakan untuk komunikasi antar goroutines.
3. Sync package: Menyediakan berbagai constructs untuk synchronizing goroutines.
4. Context package: Digunakan untuk membatalkan operasi asynchronous.

### Contoh Kode yang Lebih Kompleks:

- Implementasi web server asynchronous dengan Golang.
- Implementasi worker pool untuk menjalankan tasks secara asynchronous.
- Implementasi event-driven programming dengan Golang.

### Kesimpulan

Dalam dunia pemrograman modern, asynchronous programming dan concurrency adalah dua konsep yang sangat penting, terutama dalam pengembangan aplikasi backend menggunakan Go. Meskipun sering kali dianggap sama atau saling tergantikan, kedua konsep ini memiliki perbedaan yang signifikan dan mempengaruhi bagaimana kita merancang dan mengembangkan aplikasi. Dengan memahami perbedaan dan peran masing-masing konsep ini, Anda dapat membuat keputusan yang lebih baik dalam merancang arsitektur aplikasi backend Anda dan meningkatkan kualitas serta performa aplikasi yang Anda kembangkan.

