# Landing Page Rak Minimarket (HTML + Tailwind CSS v4)

Static site satu halaman, tanpa framework JS. Total HTML sekitar 17 KB, CSS hasil build sekitar 14 KB.

## 1. Jalankan di lokal

Syarat: Node.js 18 atau lebih baru.

```bash
cd lp-rak
npm install
npm run build      # hasil: dist/output.css (sudah ada di zip ini)
```

Saat mengedit `index.html`, jalankan mode watch di satu terminal:

```bash
npm run dev
```

Lalu buka `index.html` langsung di browser, atau pakai server lokal:

```bash
npx serve .
```

## 2. Ganti placeholder (wajib sebelum tayang)

Gunakan Find & Replace di seluruh `index.html` dan `robots.txt`:

| Cari                     | Ganti dengan                                             |
|--------------------------|----------------------------------------------------------|
| `6281234567890`          | Nomor WhatsApp, format 62 tanpa + dan tanpa 0 di depan   |
| `+6281234567890`         | Nomor yang sama dengan awalan + (untuk JSON-LD)          |
| `www.domainanda.com`     | Domain asli (canonical, OG, robots)                      |
| `NamaBrand`              | Nama perusahaan                                          |
| `Alamat pabrik: isi di sini.` | Alamat asli di footer                               |

Teks pesan WhatsApp yang terisi otomatis ada di variabel `msg` pada `<script>` di akhir `index.html`.

## 3. Open Graph image

Buat gambar `og-image.jpg` ukuran 1200 x 630 px (foto rak/pabrik + nama brand), taruh di root
project, di sebelah `index.html`. Cek hasil preview link di
https://developers.facebook.com/tools/debug/ setelah online.

## 4. Pasang Google Ads tracking

1. Tempel snippet gtag.js dari Google Ads ke `<head>`, tepat di bawah komentar `Google Ads`.
2. Di bagian `<script>` akhir, hapus tanda `//` pada baris `gtag("event", "conversion", ...)` dan isi
   `send_to` dengan ID konversi dari akun Anda.
3. Setiap tombol WA punya atribut `data-wa` (hero, header, sticky, dst.) yang terkirim sebagai
   `button_position`, jadi Anda bisa melihat tombol mana yang paling sering diklik.

## 5. Deploy

Pilih salah satu. Yang di-upload: `index.html`, folder `dist/`, `robots.txt`, `og-image.jpg`.

- **Netlify / Cloudflare Pages**: Build command `npm run build`, publish directory `.`
  (atau drag and drop folder hasil di Netlify Drop).
- **Vercel**: Framework preset "Other", build command `npm run build`, output directory `.`
- **Hosting biasa (cPanel)**: jalankan `npm run build` di lokal, lalu upload file di atas ke `public_html`.

## 6. Checklist sebelum iklan jalan

- [ ] Nomor WA, domain, dan nama brand sudah diganti
- [ ] `og-image.jpg` sudah ada
- [ ] Tes klik semua tombol WA di HP asli
- [ ] Jalankan PageSpeed Insights, targetkan hijau di mobile
- [ ] Tag konversi Google Ads terpasang dan terdeteksi di Tag Assistant
- [ ] Buat `sitemap.xml` (cukup satu URL) kalau ingin diindeks organik

## Struktur

```
index.html        konten + SEO (title, meta, OG, JSON-LD, heading h1/h2/h3)
src/input.css     tema Tailwind (warna, font) + komponen tombol
dist/output.css   CSS hasil build
robots.txt
```
