---
title: "Youtube Download With Golang"
date: 2024-03-22
description: "Library for downloading videos and audios from youtube"
tags: [go, golang, youtube]
---

Hai, Saya Mempunyai Library Untuk Download Video Atau Audio Dari Link Youtube.

Saya Mendapat Source Dari y2mate.com.

Anda Bisa Melihat Source Saya Di [Sini](https://github.com/refaldyrk/ytdl-go).

## Cara Menggunakan
### 1. Install Lib

```bash
go get -u github.com/refaldyrk/ytdl-go
```

### 2. Mulai
```go
package main

import (
	"encoding/json"
	"fmt"

	"github.com/refaldyrk/ytdl-go/service"
)

func main() {
	yt := service.NewYtdl()

	result, err := yt.DetailVideo("https://www.youtube.com/watch?v=yC6e7lY8BWQ")
	if err != nil {
		fmt.Println(err)
	}

	//Handle Mp4
	for _, v := range result.Links.Mp4 {
		data := map[string]string{}

		//Marshal
		byteJson, _ := json.Marshal(v)

		//Unmarshal
		err := json.Unmarshal(byteJson, &data)
		if err != nil {
			fmt.Println(err)
		}

		//Download All Key
		downloadVid, err := yt.DownloadVid(data["k"])
		if err != nil {
			fmt.Println(err)
		}

		//Print All Link Download
		fmt.Println(downloadVid.DownloadLink)
		fmt.Println()
	}
}
```

Note: Jika Anda Ingin Menggunakan Audio Tinggal Diubah Saja.

Thanks