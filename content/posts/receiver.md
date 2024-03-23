---
title: "Value Receiver Vs Pointer Receiver"
date: 2024-03-23
description: "Apa Bedanya Value Receiver dan Pointer Receiver?"
tags: [go, golang]
---

Hi Gophers, Di kesempatan kali ini saya akan membahas apa itu Value Receiver Dan Pointer Receiver.

Saat kita membuat method di golang pasti kita akan membuat receiver namun, seringkali tidak tau ingin menggunakan

```go
func (r receiver) name() {}
```
Atau 
```go
func (r *receiver) name() {}
```
- Ada yang tau bedanya apa?

Nah disini kita akan bahas apa bedanya value receiver dan pointer receiver.

## Value Receiver
Pertama kita bakal kenalan dulu sama *Value Receiver*.

- Contoh code value receiver
```go
type Data struct {
    name string
}
func (r receiver) name() {
    r.name = "Jane Doe"
    fmt.Println(r.name) // Jane Doe
}

func main() {
    data := Data{
        name: "John",
    }
    
    data.name() // Jane Doe
    fmt.Println(data.name) // John
}
```

Ketika sebuah method memiliki receiver dengan tipe nilai, maka saat method tersebut dipanggil, nilai tersebut akan disalin. Ini berarti bahwa method tersebut tidak dapat mengubah nilai dari struktur data asli yang diterima sebagai receiver. Perubahan yang terjadi pada struktur data tersebut hanya berlaku di dalam lingkup method dan tidak memengaruhi struktur data asli.

## Pointer Receiver
Selanjutnya kita kenalan dengan *Pointer Receiver*.

- Contoh code pointer receiver
```go
type Data struct {
    name string
}
func (r *receiver) name() {
    r.name = "Jane Doe"
    fmt.Println(r.name) // Jane Doe
}

func main() {
    data := Data{
        name: "John",
    }
    
    data.name() // Jane Doe
    fmt.Println(data.name) // Jane Doe
}
```
etika sebuah method memiliki receiver dengan tipe pointer, method tersebut dapat mengubah nilai dari struktur data asli yang diterima sebagai receiver. Dalam hal ini, method memiliki akses langsung ke lokasi memori dari struktur data asli, sehingga perubahan yang dilakukan akan mempengaruhi struktur data tersebut secara global.

## Gunakan Yang Mana Dong?
Disaat kita harus mengubah value receiver secara global kita gunakan *Pointer Receiver* 
Jika Tidak Gunakan *Value Receiver*

Thanks 🍺