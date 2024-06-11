---
title: "Ownership Rust Dalam Relationship (Percintaan)"
date: 2024-06-11
description: "Kalau Variable Aja Setia, Masa Kamu Nggak?"
tags: [rust, ownership, memory]
---

### "Ownership di Rust vs. Percintaan: Kalau Variable Aja Setia, Masa Kamu Nggak?"

---


#### Pengantar: Ownership Itu Apa Sih?
Pernah nggak sih, kamu denger soal Rust? Bukan karat yang bikin besi rusak, tapi bahasa pemrograman yang lagi ngehits karena manajemen memorinya yang kece abiz. Salah satu konsep keren di Rust adalah *ownership*. Nah, ownership ini bisa kita samain sama konsep percintaan. Kok bisa? Yuk, simak!

#### Satu Owner Satu Waktu
Di Rust, setiap nilai (data) cuma boleh punya satu owner (pemilik) dalam satu waktu. Nah, ini mirip banget sama pacaran. Ketika kamu pacaran, cuma ada satu orang yang bisa disebut pacar. Kalau ada dua? Wah, itu namanya bukan pacaran, tapi PDKT berjamaah, sasimo!

#### Borrowing: Meminjam Tapi Nggak Mengambil
Di Rust, kamu bisa "meminjam" nilai dari owner tanpa mengambil alih kepemilikan, namanya *borrowing*. Ada dua jenis borrowing:

-<b> Immutable Borrowing </b> : Kamu bisa pinjem tapi nggak bisa ubah data. Mirip kayak pacar kamu pinjem jaketmu, dia nggak akan merubah jaketmu jadi hoodie.
  ```rust
    let s = String::from("hello");
    let r1 = &s;  // pinjem tapi ga ubah
  ```


-<b> Mutable Borrowing </b> : Kamu bisa pinjem dan ubah data, tapi cuma satu orang yang boleh pinjem sekaligus. Kayak pacarmu pinjem motor, boleh dibawa kemana-mana, tapi nggak boleh ada orang lain yang pinjem saat itu juga.
  ```rust
    let mut s = String::from("hello");
    let r1 = &mut s;  // pinjem dan bisa ubah
  ```


#### Ownership Transfer: Putus dan Move On
Ketika kamu menyerahkan ownership ke variabel lain, variabel pertama "putus" dan nggak bisa akses data lagi. Misalnya:
```rust
  let s1 = String::from("hello");
  let s2 = s1;  // s1 putus, s2 jadian
```
Bayangin, kamu punya pacar (s1), tapi sekarang dia jadi pacar orang lain (s2). Kamu nggak bisa lagi chat mesra sama dia. Move on!

#### Referensi: Jangan Campur Aduk
Di Rust, kamu nggak bisa campur aduk referensi immutable dan mutable. Ini biar nggak ada data race, atau dalam bahasa percintaan, biar nggak ada drama. Misalnya:
```rust
  let mut s = String::from("hello");
  let r1 = &s;       // referensi immutable
  let r2 = &mut s;   // ini akan menyebabkan error
```
Kayak kamu nggak bisa ngedeketin orang lain saat masih punya pacar. Dramas be gone!

#### Drop: Akhir Hubungan
Di Rust, ketika owner keluar dari scope, nilai akan di-drop (dihapus dari memori). Kalau di dunia nyata, ini kayak kamu move on dari mantan. Udah nggak ada lagi rasa yang tertinggal, semua memori udah hilang.
```rust
  {
    let s = String::from("hello");
  }  // s di-drop di sini

```
#### Kesimpulan: Belajar Setia dari Rust
Kalau Rust aja bisa mengelola memori dengan setia dan aman, masa kita nggak bisa setia sama pasangan? Ownership di Rust ngajarin kita buat jaga hubungan biar nggak ada yang tersakiti. Satu hati, satu owner. Simple but deep.

---

Begitu deh cerita tentang persamaan konsep ownership di Rust dan Relationship (Pacaran Ala Gen Z). Semoga bisa bantu kamu memahami Rust dengan cara yang lebih asik dan relate. Jangan lupa share ke teman-teman biar mereka juga ikutan ngerti!