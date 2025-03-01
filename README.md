# Stork Oracle Multi-Account Auto Bot

Bot otomatis untuk validasi data di jaringan Stork Oracle dengan dukungan multi akun. Bot ini membantu Anda mengotomatisasi proses verifikasi untuk mendapatkan rewards melalui sistem Stork Oracle.

## Fitur

- Mendukung banyak akun Stork Oracle sekaligus
- Secara otomatis mengambil data harga yang ditandatangani dari API Stork Oracle
- Memvalidasi data harga sesuai dengan aturan yang telah ditentukan
- Mengirimkan hasil validasi kembali ke API
- Menangani refresh token untuk operasi berkelanjutan
- Menampilkan statistik validasi dan informasi pengguna untuk setiap akun
- Interval validasi yang dapat dikonfigurasi
- Dukungan untuk server proxy untuk mendistribusikan permintaan
- Pemrosesan multi-thread untuk performa yang lebih baik

## Persyaratan

- Node.js 14.0.0 atau lebih tinggi
- Akun Stork Oracle yang valid

## Instalasi

1. Clone repository:
```
git clone https://github.com/56ix8/Stork-Oracle-Auto-Bot-Multi
```

2. Masuk ke direktori proyek:
```
cd Stork-Oracle-Auto-Bot-Multi
```

3. Instal dependensi:
```
npm install
```

4. Konfigurasi kredensial Anda (lihat bagian Konfigurasi di bawah)

## Konfigurasi

### Pengaturan Mudah dengan config.json

Bot sekarang menggunakan file config.json untuk konfigurasi. Saat Anda menjalankan bot untuk pertama kalinya, bot akan membuat file config.json default yang dapat Anda edit.

1. Jalankan bot sekali untuk menghasilkan file konfigurasi default:
```
node index.js
```

2. Edit file `config.json` yang dihasilkan dengan kredensial Anda:
```json
{
  "accounts": [
    {
      "username": "email-anda-1@example.com",
      "password": "password-anda-1"
    },
    {
      "username": "email-anda-2@example.com",
      "password": "password-anda-2"
    }
  ],
  "cognito": {
    "region": "ap-northeast-1",
    "clientId": "5msns4n49hmg3dftp2tp1t2iuh",
    "userPoolId": "ap-northeast-1_M22I44OpC"
  },
  "stork": {
    "intervalSeconds": 5
  },
  "threads": {
    "maxWorkers": 1
  }
}
```

3. Ganti `username` dan `password` dengan kredensial akun Stork Oracle Anda untuk setiap akun

### Opsional: Konfigurasi Proxy

Untuk menggunakan server proxy untuk distribusi permintaan:

1. Buat file `proxies.txt` di root proyek
2. Tambahkan satu proxy per baris dalam salah satu format berikut:
   - Proxy HTTP: `http://user:pass@host:port`
   - Proxy SOCKS: `socks5://user:pass@host:port`

## Penggunaan

Mulai bot dengan:
```
node index.js
```

Bot akan:
1. Mengautentikasi menggunakan kredensial Anda dari config.json untuk setiap akun
2. Mengambil data harga yang ditandatangani pada interval reguler
3. Memvalidasi setiap titik data
4. Mengirimkan hasil validasi ke Stork Oracle
5. Menampilkan statistik terkini Anda untuk setiap akun

## Opsi Konfigurasi Lanjutan

Dalam file `config.json` Anda, Anda dapat menyesuaikan:

- `stork.intervalSeconds`: Seberapa sering proses validasi berjalan dalam detik (default: 5)
- `threads.maxWorkers`: Jumlah pekerja validasi bersamaan (default: 1)

## Pemecahan Masalah

- Jika Anda melihat kesalahan autentikasi, periksa bahwa username dan password di config.json sudah benar
- Jika bot gagal memulai, pastikan file config.json Anda adalah JSON yang diformat dengan benar
- Jika Anda melihat kesalahan terkait token setelah autentikasi berhasil, file tokens_X.json mungkin rusak - hapus dan biarkan bot membuatnya kembali
- Untuk masalah koneksi, periksa koneksi internet Anda dan verifikasi bahwa API Stork Oracle dapat diakses
- Jika menggunakan proxy, periksa bahwa proxies.txt Anda diformat dengan benar dan proxy beroperasi

## Disclaimer

Bot ini disediakan hanya untuk tujuan pendidikan. Gunakan dengan risiko Anda sendiri. Penulis tidak bertanggung jawab atas konsekuensi apa pun yang mungkin timbul dari penggunaan bot ini, termasuk namun tidak terbatas pada penghentian akun atau kehilangan rewards.

## Lisensi

MIT License

## Kontribusi

Kontribusi dipersilakan! Silakan kirimkan Pull Request.
