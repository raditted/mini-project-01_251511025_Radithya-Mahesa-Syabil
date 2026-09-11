# Mini Project - Radithya Mahesa Syabil / 251511025

**URL Publik:**  
**Source Code:** 

## Ringkasan halaman
Telah dibuat landing page untuk UMKM "Roti Lieur" dengan struktur semantik (header, nav, main, section, footer). Halaman ini menampilkan informasi pengenalan brand, testimoni, alasan memilih produk, katalog roti, dan kontak UMKM. Layout dirancang responsif menggunakan Flexbox dengan pendekatan *mobile-first* (layout kolom pada layar kecil, lalu berubah menjadi baris pada layar besar)

## Tiga keputusan teknis
1. **Custom properties di `:root`**. Digunakan untuk menyimpan variabel warna (`--color-primary`, `--color-bg`, dll.), *spacing*, dan *radius* agar gaya desain konsisten dan mudah diubah secara global dari satu tempat.

2. **Flexbox dengan mobile-first**. CSS dasar menggunakan `flex-direction: column` untuk layar kecil. Kemudian, media query `min-width: 768px` digunakan untuk mengubah `.site-header` dan `.hero-content` menjadi baris (`row`) karena di atas 768px ruang layar cukup lebar. Untuk daftar produk, digunakan `flex-wrap: wrap` dengan `flex-basis: 260px` sehingga jumlah kolom otomatis menyesuaikan layar tanpa media query tambahan.

3. **Semantic HTML yang spesifik**: Menggunakan `section` untuk membagi area utama, `article` untuk konten yang bisa berdiri sendiri (kartu produk dan blok hero), `figure` untuk membungkus gambar, `blockquote` untuk testimoni, serta `dl/dt/dd` (description list) untuk bagian kontak alamat dan telepon karena datanya berbentuk pasangan istilah-deskripsi.

## Masalah, diagnosis, dan perbaikan
* **Masalah:** Elemen *flex item* (seperti `.hero-left`, `.hero-right`, dan `.product-card`) berpotensi *overflow* atau tumpah dari *container*-nya pada layar yang sangat sempit, menyebabkan *horizontal scroll*.
* **Diagnosis:** Secara default, *flex item* memiliki properti `min-width: auto`. Hal ini mencegah elemen menyempit di bawah ukuran lebar konten di dalamnya (misalnya gambar atau teks panjang tanpa spasi).
* **Perbaikan:** Menambahkan `min-width: 0` pada elemen *flex item* (`.hero-left`, `.hero-right`, dan `.product-card`) sehingga elemen diizinkan untuk mengecil (*shrink*) mengikuti ukuran *container*, yang memastikan layout tetap rapi di viewport sempit.

## Hasil pengujian empat viewport
* **Lebar: 320px.** Susunan: Satu kolom (navigasi wrap, hero bertumpuk vertikal). Overflow: Tidak
* **Lebar: 375px.** Susunan: Satu kolom. Overflow: Tidak
* **Lebar: 768px.** Susunan: Dua kolom (untuk area hero), dan produk membungkus (*wrap*) menjadi multi-kolom otomatis. Overflow: Tidak
* **Lebar: 1024px.** Susunan: Dua kolom (area hero proporsional), daftar produk berjejer rapi. Overflow: Tidak

## Refleksi belajar
Melalui pengerjaan tugas ini, saya mendalami cara kerja Flexbox yang lebih *advanced*—seperti pemahaman properti shorthand `flex: 1 1 260px` (kombinasi *grow*, *shrink*, dan *basis*) yang memungkinkan elemen *card* produk menyesuaikan ruang layar secara otomatis tanpa harus menulis banyak *media query*. Saya juga belajar pentingnya mengecek *Computed tab* di *DevTools* untuk membaca *box model* (width, padding, border) secara akurat, serta bagaimana elemen semantik (seperti `dl`, `dt`, `dd`) dapat memperkaya makna struktur HTML dibandingkan hanya menggunakan `div`.
