# Toko POS — Microservice E-Commerce & Kasir

Aplikasi kasir/toko sederhana berbasis **microservice**, dibangun untuk mensimulasikan proses transaksi penjualan dari input produk hingga pembayaran dan cetak struk.

## Fitur

- **Manajemen Produk** — CRUD produk (tambah, lihat, ubah, hapus)
- **Manajemen Layanan** — CRUD service/layanan tambahan
- **Keranjang Belanja** — menambahkan produk/layanan ke keranjang sebelum checkout
- **Checkout & Invoice** — membuat invoice otomatis dari isi keranjang sebelum proses pembayaran
- **Pembayaran** — input nominal uang yang dibayarkan, sistem otomatis menghitung kembalian
- **Cetak Struk (PDF)** — menghasilkan struk transaksi dalam format PDF setelah pembayaran selesai

## Tech Stack

| Layer        | Teknologi              |
|--------------|-------------------------|
| Frontend     | React.js                |
| Backend      | Express.js (Node.js)    |
| Database     | PostgreSQL               |
| Containerization | Docker & Docker Compose |

## Arsitektur

Aplikasi dipecah menjadi beberapa service independen (microservice), antara lain:

- `user-service` — autentikasi & manajemen pengguna (kasir/admin)
- `product-service` — manajemen data produk
- `service-service` — manajemen data layanan tambahan
- `transaction-service` — pengelolaan keranjang, checkout, invoice, dan pembayaran
- `pdf-service` — generate struk dalam format PDF

Setiap service memiliki database PostgreSQL masing-masing dan dijalankan dalam container Docker terpisah, dihubungkan melalui Docker Compose.

## Cara Menjalankan (Lokal)

```bash
# Clone repository
git clone <url-repo-anda>
cd nama-folder-project

# Jalankan seluruh service dengan Docker Compose
docker-compose up -d

# Cek status container
docker ps
```

Setelah seluruh container berjalan, aplikasi dapat diakses melalui:
- Frontend: `http://localhost:<port-frontend>`
- API Gateway/Service: `http://localhost:<port-backend>`

> Sesuaikan port di atas dengan konfigurasi pada `docker-compose.yml`.

## Status

🚧 Saat ini masih berjalan di lingkungan lokal dan belum di-deploy ke environment publik.

## Catatan

Project ini dibuat sebagai latihan penerapan arsitektur microservice pada studi kasus aplikasi kasir/toko sederhana, mencakup komunikasi antar service, manajemen database terpisah, serta proses bisnis transaksi dari awal hingga akhir (keranjang → invoice → pembayaran → struk).
