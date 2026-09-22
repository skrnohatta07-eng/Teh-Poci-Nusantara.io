# Es Teh Poci

Website warung Es Teh Poci: peracik es teh interaktif (teko poci yang menuang teh), menu, galeri, pesanan lewat WhatsApp,
lokasi, dan halaman admin. Tema kuning, oranye, dan putih. Dibuat hanya dengan HTML, CSS, dan JavaScript,
tanpa server atau framework.

## Struktur folder

```
es-teh-poci/
├─ index.html      Halaman utama (hasil gabungan bagian/). Buka file ini di browser.
├─ style.css       Semua tampilan: warna, font, tata letak, animasi.
├─ script.js       Semua interaksi: peracik, menu, keranjang, galeri, admin.
├─ gabung.js       Alat kecil untuk membuat ulang index.html dari bagian/ (opsional).
├─ gambar/         logo.png (logo Es Teh Poci, latar transparan) dan favicon.png
└─ bagian/         index.html dipecah per tampilan:
   ├─ _kepala.html                   <head>: judul, ikon, font, tautan style.css
   ├─ _kerangka.html                 urutan semua bagian
   ├─ 01-header.html                 logo dan menu navigasi atas
   ├─ 02-peracik.html                bagian utama: logo, peracik, gelas, teko poci
   ├─ 03-menu.html                   daftar menu dan filter
   ├─ 04-galeri.html                 galeri foto
   ├─ 05-pesanan.html                keranjang, promo, dan kirim WhatsApp
   ├─ 06-lokasi.html                 alamat, jam buka, dan peta ilustrasi
   ├─ 07-admin.html                  halaman admin (alamat #admin)
   ├─ 08-footer.html                 footer
   └─ 09-lightbox-dan-notifikasi.html  jendela perbesar foto dan pesan singkat
```

## Dua cara bekerja

**Cara 1, langsung.** Edit `index.html`, `style.css`, dan `script.js`, lalu buka `index.html` di browser.

**Cara 2, per bagian.** Edit berkas di folder `bagian/` (misalnya `03-menu.html` untuk mengubah menu),
lalu jalankan `node gabung.js` untuk membuat ulang `index.html`. Perlu Node.js terpasang.
Jangan mengedit `index.html` langsung kalau kamu memakai cara ini, karena akan tertimpa saat digabung ulang.

Mengubah urutan tampilan: pindahkan baris `<!-- @include ... -->` di `bagian/_kerangka.html`, lalu gabung ulang.

## Mengubah warna

Semua warna ada di bagian **Warna dan dasar** di paling atas `style.css`
(`--yellow`, `--orange`, `--accent`, `--bg-2`, dan seterusnya). Ubah di sana, seluruh halaman ikut berubah.

## Rasa dan harga

Daftar rasa (Original, Lemon Honey, Lychee, Blackcurrant, Mango, Orange, Guava, Apple,
Chocolate, Milk Tea, Cappuccino, Thai Tea) ada di `script.js`, bagian **Data**, variabel `FLAVORS`.
Hanya Original yang punya dua ukuran (Kecil dan Besar); rasa lain satu ukuran (Besar).
Warna gelas di peracik dan galeri mengikuti warna (`color`) yang diisi di situ, dan rasa dengan
`milky: true` akan tampil creamy dengan butiran boba di gelas.

Untuk menambah rasa baru: tambahkan satu baris di `FLAVORS`, lalu tulis deskripsinya di `MENU_DESC`
(bagian **Data**, tepat di bawah `FLAVORS`). Menu, galeri contoh, dan form harga di Admin akan
menyesuaikan sendiri.

## Yang perlu kamu ganti

Pengaturan awal ada di `script.js`, bagian **Pengaturan bawaan** (cari dengan Ctrl+F):
nama toko, nomor WhatsApp, alamat, patokan, jam buka, ongkos antar, dan kode promo.
Harga tiap rasa mengikuti angka di `FLAVORS` (lihat bagian **Rasa dan harga** di atas).

## Logo

Logo ada di `gambar/logo.png` (sudah dibuat transparan agar menyatu dengan latar kuning).
Untuk menggantinya, timpa file itu dengan logo baru berukuran lebar sekitar 600 px.
Pastikan kamu berhak memakai logo merek tersebut di websitemu.

## Memasang foto sendiri

1. Buat folder `foto/` di samping `index.html`, lalu taruh fotomu di sana.
2. Di `script.js`, pada `DEFAULTS.gallery`, tambahkan baris seperti:
   `{ id: "f1", caption: "Es teh andalan kami", src: "foto/es-teh-1.jpg" }`

Cara lain: unggah lewat halaman admin. Tapi foto dari admin hanya tersimpan di browser admin.

## Halaman admin

Buka `index.html#admin`, atau klik "Admin" di footer. PIN awal adalah `1234`, ganti di tab Data.

- Data admin disimpan di browser yang dipakai (localStorage), bukan di server.
  Pengunjung lain tetap melihat pengaturan awal dari `script.js`.
- PIN hanya pembatas ringan di sisi browser, bukan keamanan sungguhan.
- Agar perubahan berlaku untuk semua pengunjung, salin data dari tab Data > Ekspor
  ke `DEFAULTS` di `script.js`, atau sambungkan ke database (misalnya Firebase atau Supabase).

## Catatan

- Font (Bagel Fat One dan Figtree) dimuat dari Google Fonts. Tanpa internet, browser memakai font cadangan.
- Peta di halaman lokasi berupa ilustrasi. Tombol "Buka di Google Maps" membuka peta sebenarnya.
- Situs ini hanya memakai tema terang (kuning, oranye, putih).
