# SignSafe-jwt – Simulasi API E-Wallet


Aplikasi Pembanding untuk SignSafe yang menggunakan digital signature sebelumnya.

## Fitur Utama

- Login Pengguna: Pengguna dapat masuk dengan mengirimkan username dan password.
- Otentikasi JWT: Setiap permintaan (kecuali registrasi) harus mengirimkan header Authorization agar dapat diproses oleh server
- Middleware JWT: Middleware ini memeriksa header khusus (Autorization)).
- Transaksi E-Wallet: Endpoint untuk melakukan top-up (penambahan saldo) dan transfer antar pengguna.
- Riwayat Transaksi: Endpoint untuk melihat daftar transaksi (top-up/transfer) milik pengguna.
- Routing dengan Gorilla Mux: Menggunakan paket gorilla/mux yang populer sebagai HTTP router di Go.

## Endpoint

Seluruh endpoint diakses dengan prefix /api. Semua request (kecuali register) harus melalui SignSafeMiddleware.

- POST /api/auth/login: masuk pengguna sudah ada yang digenerate melalui api SignSafe digital signature.

- GET /api/user: Mendapatkan informasi pengguna saat ini (berdasarkan userID di header).

- GET /api/users/{id}: Mendapatkan informasi pengguna berdasarkan path parameter {id}.

- POST /api/topup: Menambahkan saldo kepada pengguna sendiri.

- POST /api/transfer: Mengirim saldo dari pengguna saat ini ke pengguna lain.

- GET /api/history: Menampilkan riwayat transaksi pengguna saat ini (top-up dan transfer).

## Instalasi dan Penggunaan

```bash
docker build -t signsafe-backend .

docker run -p 8080:8080 --env-file .env signsafe-backend
```

pastikan api Signsafe digital signature, Redis dan postgresql sudah berjalan
