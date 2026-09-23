# Portfolio Ares Suhendar — paket unggah

Folder ini siap diunggah apa adanya ke hosting statis (Netlify, Vercel, GitHub Pages,
Cloudflare Pages, atau hosting cPanel biasa).

## Cara mengunggah

**Netlify / Cloudflare Pages** — seret seluruh folder ini ke halaman deploy. Selesai.

**GitHub Pages** — unggah isi folder ini ke repo, aktifkan Pages di Settings → Pages,
pilih branch dan folder root.

**cPanel / FTP** — unggah semua isi folder ini ke `public_html`.

`index.html` otomatis mengalihkan ke halaman portfolio, jadi domain root langsung jalan.

## Isi

```
index.html                        pengalih ke halaman utama
Portfolio Ares Suhendar.dc.html   halaman utama
Project Detail.dc.html            detail proyek (?p=1..6) dan daftar proyek (?list=1)
Post Detail.dc.html               detail tulisan (?a=1..9)
projects-data.js                  teks 6 proyek, ID + EN
posts-data.js                     teks 9 tulisan, ID + EN
support.js, image-slot.js         runtime dan komponen gambar
assets/                           gambar, favicon, kartu berbagi, CV
```

## Mengubah isi nanti

Teks proyek dan tulisan ada di `projects-data.js` dan `posts-data.js` — satu file untuk
kedua bahasa, dan halaman utama maupun halaman detail membaca file yang sama. Tambah satu
entri di sana, kartunya langsung muncul.

Gambar ada di `assets/`. Mengganti gambar proyek atau tulisan cukup dengan menimpa
file dengan nama yang sama.

## Setelah domain aktif

Tiga baris berikut sengaja belum diisi karena domainnya belum ditentukan. Tambahkan di
`<helmet>` pada `Portfolio Ares Suhendar.dc.html` setelah kamu tahu alamat aslinya:

```html
<link rel="canonical" href="https://DOMAIN-KAMU/" />
<meta property="og:url" content="https://DOMAIN-KAMU/" />
```

Lalu di blok `application/ld+json`, tambahkan `"url": "https://DOMAIN-KAMU/"` dan ubah
`"image"` menjadi alamat penuh. Sebelum itu jangan diisi dengan domain tebakan — canonical
yang salah bisa membuat situsmu tidak terindeks.

## Yang belum selesai

- Form kontak belum punya backend, jadi tombol kirim belum mengirim apa pun.
  Cara tercepat: daftar di Formspree, lalu bungkus field-nya dalam `<form action="...">`.
- Slot foto profil di hero masih kosong — taruh `assets/profile.jpg` dan pasang
  sebagai `src` pada slot foto hero.
- Lima gambar proyek dan sembilan banner tulisan masih sketsa buatan, bukan
  screenshot atau foto asli.

## Catatan teknis

Halaman harus diakses lewat server (http/https), bukan dibuka langsung dari
`file://`, karena data proyek dan tulisan dimuat sebagai modul JavaScript.
Untuk mengetes di komputer sendiri: jalankan `python3 -m http.server` di folder ini,
lalu buka `http://localhost:8000`.
