# IG Feed Studio

> Tools desain konten Instagram berbasis browser — layer system, gradient overlay, teks bebas, remove background AI, dan export PNG/JPG. Tanpa install, tanpa login, tanpa server.

**Prompt engine by [@dhikiteguh](https://instagram.com/dhikiteguh)**

---

## Daftar Isi

- [Fitur Utama](#fitur-utama)
- [Cara Pakai](#cara-pakai)
- [Layer System](#layer-system)
- [Paste Gambar](#paste-gambar)
- [Remove Background AI](#remove-background-ai)
- [Export](#export)
- [Deploy ke Vercel](#deploy-ke-vercel)
- [Struktur File](#struktur-file)
- [Catatan Teknis](#catatan-teknis)
- [Dukung Kreator](#dukung-kreator)

---

## Fitur Utama

| Fitur | Keterangan |
|---|---|
| **Layer System** | Susun foto, overlay PNG transparan, dan teks dalam urutan bebas seperti Canva |
| **PNG Transparan** | Upload template PNG dengan area transparan — ditimpa dengan benar di atas foto |
| **Free Transform** | Klik layer → muncul selection box dengan 8 handle untuk resize dan drag bebas |
| **Paste Gambar** | Tekan `Ctrl+V` / `⌘+V` untuk paste gambar langsung dari clipboard |
| **Gradient Overlay** | Gradient tipis di atas gambar dengan kontrol arah, opacity, dan fade |
| **Teks Multi-layer** | Tambah banyak layer teks, drag bebas, resize, auto-wrap |
| **Remove BG AI** | Hapus background foto otomatis pakai AI — berjalan penuh di browser |
| **Export PNG/JPG** | Export resolusi penuh, transparan terjaga di PNG |
| **Ukuran IG Lengkap** | Feed 4:5, Square, Landscape, Story/Reels, 16:9, Reel Cover |
| **Mobile Friendly** | Responsive untuk layar HP — panel bawah saat layar sempit |
| **Tanpa Server** | Semua proses di browser, tidak ada data dikirim ke server |

---

## Cara Pakai

### 1. Buka Aplikasi

Buka file `index.html` langsung di browser, atau akses via URL Vercel setelah deploy.

### 2. Tambah Foto Utama

Ada 3 cara:
- **Klik area upload** di tengah kanvas
- **Drag & drop** file gambar ke kanvas
- **Tekan `Ctrl+V`** setelah copy gambar dari mana saja

> Foto pertama yang diupload otomatis menjadi layer paling bawah dan menyesuaikan ukuran kanvas.

### 3. Tambah Overlay PNG (Template Transparan)

- Klik tombol **🖼 OVERLAY PNG** di panel Layers
- Atau **drag & drop file PNG** ke atas kanvas (jika sudah ada foto, PNG otomatis jadi overlay)
- PNG dengan area transparan akan ditimpa di atas foto dengan benar

### 4. Susun Layer

Di panel **Layers** (tab pertama):
- **↑ ↓** — pindah urutan layer (atas = tampil di depan)
- **👁** — sembunyikan/tampilkan layer
- **×** — hapus layer
- Slider **OP** — atur opacity per layer
- **Klik layer** di kanvas untuk memilih dan mengaktifkan selection box

### 5. Free Transform

Setelah klik layer di kanvas:
- Muncul **selection box kuning** dengan 8 handle
- **Drag dalam kotak** → pindah posisi
- **Drag handle sudut** → resize proporsional
- **Drag handle tengah** → resize satu arah
- Teks layer → resize otomatis menyesuaikan ukuran font

### 6. Edit Teks

- Klik tab **Teks** di panel kanan
- Pilih layer teks yang ingin diedit
- Atur font, ukuran, gaya (bold/italic), warna, opacity, spasi baris, lebar maksimal
- Tekan `Enter` di textarea untuk baris baru
- Teks otomatis wrap jika terlalu panjang

### 7. Gradient Overlay

Di tab **Gradient**:
- Pilih warna dari palet atau custom color picker
- Atur arah (dari bawah, atas, kanan, kiri, atau OFF)
- Slider Opacity, Jangkauan, dan Fade untuk kontrol halus

### 8. Ukuran Kanvas

Di tab **Kanvas**, pilih preset ukuran:

| Preset | Ukuran | Kegunaan |
|---|---|---|
| Feed 4:5 | 1080 × 1350 px | Feed Instagram portrait |
| Square | 1080 × 1080 px | Feed Instagram kotak |
| Landscape | 1080 × 608 px | Feed Instagram landscape |
| Story | 1080 × 1920 px | Instagram Story & Reels |
| 16:9 | 1080 × 566 px | Wide landscape |
| Reel Cover | 420 × 654 px | Cover thumbnail Reels |

---

## Layer System

Layer bekerja dari **bawah ke atas**. Urutan di panel Layers menentukan apa yang tampil di depan.

```
[ TEKS 1          ]  ← paling depan (atas)
[ OVERLAY PNG     ]  ← template transparan di atas foto
[ FOTO UTAMA      ]  ← paling belakang (bawah)
```

**Tipe layer:**

- **📷 FOTO** — gambar dasar, mengisi seluruh kanvas
- **🖼 OVERLAY PNG** — gambar PNG dengan transparansi, bisa di atas atau bawah foto
- **T TEKS** — layer teks dengan kontrol font lengkap

> Layer overlay PNG bisa diletakkan di **bawah** foto untuk efek tertentu — gunakan tombol ↑↓ untuk mengatur urutan.

---

## Paste Gambar

Fitur paste memungkinkan workflow lebih cepat:

1. **Screenshot** apapun di komputer
2. Atau **copy gambar** dari browser / aplikasi lain
3. Klik di area kanvas lalu tekan **`Ctrl+V`** (Windows/Linux) atau **`⌘+V`** (Mac)
4. Gambar langsung masuk sebagai layer baru

> **PNG transparan yang dipaste** otomatis menjadi layer overlay.
> **Foto biasa** menjadi layer foto utama.

Ada juga tombol **📋 PASTE** di panel Layers untuk trigger manual jika shortcut tidak berjalan.

---

## Remove Background AI

Fitur hapus background menggunakan library open source [`@imgly/background-removal-js`](https://github.com/imgly/background-removal-js).

**Cara pakai:**
1. Pilih layer **foto** atau **overlay** di panel Layers
2. Pergi ke tab **Export**
3. Klik tombol **✂ HAPUS BACKGROUND (AI)**
4. Tunggu proses (pertama kali download model ~30 detik)
5. Background terhapus, layer berubah menjadi PNG transparan

**Catatan penting:**
- Semua proses berjalan **100% di browser** — tidak ada gambar dikirim ke server
- Model AI didownload sekali dan di-cache browser
- Cocok untuk deployment di **Vercel free tier** (tidak butuh server-side)
- Kualitas terbaik untuk foto dengan subjek jelas (orang, produk)
- Ukuran gambar besar akan butuh lebih lama

---

## Export

Di tab **Export**:

| Tombol | Format | Keterangan |
|---|---|---|
| **Export PNG** | `.png` | Lossless, transparansi terjaga, file lebih besar |
| **Export JPG** | `.jpg` | Kompresi 93%, background putih, file lebih kecil |

Setelah export, preview thumbnail muncul di bawah dengan link download cadangan jika browser memblokir auto-download.

> **PNG direkomendasikan** jika hasil akhir masih akan diedit ulang atau mengandung area transparan.

---

## Deploy ke Vercel

### Cara 1 — Via GitHub (Direkomendasikan)

```bash
# 1. Buat repo GitHub baru
# 2. Upload file index.html ke repo
# 3. Buka vercel.com → Add New Project
# 4. Import repo → Deploy
```

Setiap update file di GitHub → Vercel auto-deploy otomatis.

### Cara 2 — Drag & Drop (Tanpa GitHub)

1. Buka [vercel.com](https://vercel.com)
2. Klik **Add New → Deploy**
3. Drag & drop **folder** yang berisi `index.html`
4. Dapat URL langsung

### Konfigurasi Vercel (Opsional)

Buat file `vercel.json` di folder yang sama:

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cross-Origin-Embedder-Policy",
          "value": "require-corp"
        },
        {
          "key": "Cross-Origin-Opener-Policy",
          "value": "same-origin"
        }
      ]
    }
  ]
}
```

> Header COEP/COOP diperlukan agar fitur Remove Background AI berjalan optimal (SharedArrayBuffer untuk WebAssembly).

---

## Struktur File

```
ig-feed-studio/
│
├── index.html          ← Satu file aplikasi lengkap (self-contained)
├── vercel.json         ← Konfigurasi header Vercel (opsional)
└── README.md           ← Dokumentasi ini
```

Seluruh aplikasi ada dalam **satu file HTML** — tidak ada dependency eksternal selain font Google (B612) yang di-load online dan library remove-bg yang di-load on-demand saat pertama kali digunakan.

---

## Catatan Teknis

### Kenapa satu file HTML?

Agar mudah dibagikan, dibuka offline, dan di-deploy ke platform apapun tanpa konfigurasi build.

### Kenapa PNG tidak bisa diakses lintas domain?

Browser memblokir akses canvas ke gambar dari domain lain (CORS). Semua gambar diload via `FileReader.readAsDataURL()` yang menghasilkan data URL — cara ini **tidak pernah tainted** dan selalu bisa di-export.

### Kenapa export kadang tidak jalan di dalam iframe?

File harus dibuka **langsung di browser** (bukan di dalam iframe/embed). Untuk embed, gunakan `<iframe>` dengan atribut `allow="clipboard-read; clipboard-write"`.

### Performa di mobile

Gambar besar (>2000px) di-clamp otomatis ke maksimal 1920px untuk performa. Fitur Remove BG mungkin lambat di HP karena keterbatasan memori.

### Browser yang didukung

| Browser | Desktop | Mobile |
|---|---|---|
| Chrome / Edge | ✅ Penuh | ✅ Penuh |
| Firefox | ✅ Penuh | ✅ Penuh |
| Safari | ✅ Penuh | ⚠️ Paste clipboard terbatas |
| Samsung Internet | ✅ Penuh | ✅ Penuh |

---

## Dukung Kreator

Aplikasi ini dibuat dan dikembangkan oleh **@dhikiteguh**.

Jika tools ini bermanfaat, dukung kreator di:

**[☕ saweria.co/dhiki](https://saweria.co/dhiki)**

Atau follow di Instagram: **[@dhikiteguh](https://instagram.com/dhikiteguh)**

---

## Lisensi

Free to use. Silakan modifikasi sesuai kebutuhan.
Credit ke [@dhikiteguh](https://instagram.com/dhikiteguh) sangat diapresiasi.

---

*Dibuat dengan ❤️ — Prompt engine by @dhikiteguh*
