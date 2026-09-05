# Website Prodi S1 Teknik Informatika — UMC

Website profil untuk Program Studi S1 Teknik Informatika, Universitas Muhammadiyah Cirebon (UMC). Berisi profil singkat prodi, visi & misi, fasilitas akademik, serta dokumentasi kegiatan pengabdian, kolaborasi, dan kegiatan ilmiah.

## 1. Konsep Desain

- **Gaya visual**: modern, bersih, dan tegas — menggunakan tipografi besar berhuruf kapital untuk judul, banyak *whitespace*, dan garis aksen (`rule`) berwarna merah sebagai penanda tiap bagian.
- **Palet warna** mengikuti identitas kampus/prodi:
  - Merah `#DF1A22` — warna utama (navigasi, judul, aksen)
  - Kuning/emas `#F2A900` — aksen di banner (headline)
  - Hijau `#00853F` — aksen sekunder (garis pembatas, outline hover, shadow)
  - Putih `#FFFFFF` & hitam/abu gelap `#111111` — latar dan teks utama
- **Layout**: satu halaman panjang (*single-page scroll*) dengan navigasi yang otomatis scroll-smooth ke tiap bagian (Beranda, Visi & Misi, Fasilitas Akademik, Kegiatan & Kolaborasi).
- **Interaksi & animasi**:
  - Elemen muncul bertahap (*fade + slide up*) saat di-scroll ke area yang terlihat (*reveal on scroll*).
  - Navbar transparan di atas, berubah solid (putih + tint merah tipis) saat halaman di-scroll supaya tidak transparan menimpa foto banner.
  - Kartu (Fasilitas Akademik, galeri Dokumentasi Kegiatan) punya efek *hover*: sedikit membesar, muncul shadow, dan outline merah/hijau.
  - Galeri "Dokumentasi Kegiatan" memakai layout *bento grid* — satu foto besar dengan caption selalu tampil, dikelilingi foto-foto lain dengan caption yang muncul saat di-hover.
- **Responsif**: tersusun dalam 3 breakpoint (desktop, tablet ±601–1024px, dan mobile ≤600px) supaya navigasi, grid fasilitas, dan galeri tidak bertumpuk di layar kecil.

## 2. Teknologi yang Digunakan

Website ini dibangun **tanpa framework/library eksternal** — murni:

- **HTML5** — struktur konten
- **CSS3** (native, di dalam tag `<style>`) — semua styling, layout (Flexbox & CSS Grid), variabel warna (`:root` custom properties), animasi (`@keyframes`, `transition`), dan *responsive design* (`@media`)
- **JavaScript (Vanilla JS, tanpa library)** — untuk:
  - Animasi *reveal on scroll* (`IntersectionObserver`)
  - Efek *sticky navbar* saat di-scroll
  - *Smooth scroll* custom dengan easing saat klik menu navigasi
  - Toggle menu mobile (hamburger)
  - Efek *tilt* 3D ringan pada kartu fasilitas saat mouse hover

Tidak ada proses *build* (tidak pakai bundler seperti Webpack/Vite), tidak ada dependency npm — semua ada dalam satu file `index.html`.

## 3. Cara Menjalankan Secara Lokal

### Struktur folder yang dibutuhkan

Pastikan file dan folder berikut berada **sejajar** (satu folder yang sama):

```
project-folder/
├── index.html
├── banner.jpg                     ← foto banner/hero 
├── UMC-1.png                      ← logo 
└── FOTO KEGIATAN PRODI/           ← folder berisi semua foto dokumentasi & fasilitas
    ├── gallery-uts.jpg
    ├── gallery-lab-komputer.jpg
    ├── gallery-praktik-1.jpeg
    ├── gallery-praktik-2.jpeg
    ├── gallery-praktik-3.jpeg
    ├── gallery-jaringan-komputer.jpeg
    ├── gallery-pembelajaran.jpeg
    ├── gallery-peta-cikondang-1.jpeg
    ├── gallery-pengabdian-poster.jpeg
    ├── gallery-presentasi-peresmian.jpeg
    ├── gallery-workshop-ai-mou.jpeg
    └── gallery-seminar-banner.jpeg
```

### Cara menjalankan

**Opsi 1 — Buka langsung di browser (paling sederhana)**
1. Pastikan struktur folder di atas sudah benar.
2. Klik dua kali (atau buka) file `index.html` — akan terbuka otomatis di browser default.

> Catatan: sebagian browser membatasi pemuatan gambar lokal (`file://`) untuk halaman yang lebih kompleks. Jika ada foto yang tidak muncul, gunakan Opsi 2 di bawah.

**Opsi 2 — Menjalankan lewat local server (disarankan)**

Menjalankan lewat server lokal membuat perilaku website persis seperti saat sudah di-hosting.

- Menggunakan **Python** (biasanya sudah terpasang):
  ```bash
  cd project-folder
  python3 -m http.server 8000
  ```
  Lalu buka `http://localhost:8000` di browser.

- Menggunakan **Node.js**:
  ```bash
  cd project-folder
  npx serve .
  ```
  Lalu buka alamat yang muncul di terminal (biasanya `http://localhost:3000`).

- Menggunakan **VS Code**: install ekstensi **Live Server**, klik kanan pada `index.html` → **Open with Live Server**.

### Cara deploy ke hosting

Karena tidak ada proses build, website ini bisa langsung di-*upload* apa adanya (beserta seluruh folder `FOTO KEGIATAN PRODI`, `banner.jpg`, `UMC-1.png`) ke hosting statis apa pun, misalnya:
- GitHub Pages
- Netlify / Vercel (drag-and-drop folder)
- Hosting cPanel biasa (upload semua file lewat File Manager/FTP ke folder `public_html`)
