# Landing Page Rak Minimarket (HTML + Tailwind CSS v4)

Static site satu halaman, tanpa framework JS. Total HTML sekitar 17 KB, CSS hasil build sekitar 14 KB.

## Jalankan di lokal

Syarat: Node.js 18 atau lebih baru.

```bash
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

## Struktur

```
index.html        konten + SEO (title, meta, OG, JSON-LD, heading h1/h2/h3)
src/input.css     tema Tailwind (warna, font) + komponen tombol
dist/output.css   CSS hasil build
robots.txt
```
