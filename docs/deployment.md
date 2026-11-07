# Deployment SLiMS (Rencana)

Status: direncanakan. Belum dijalankan di VPS. Perintah di bawah akan
diverifikasi dan diperbarui setelah instalasi.

- Server: Ubuntu Server 24.04 LTS, VPS Azure
- Alamat publik: `http://20.194.24.209/`
- Lokasi aplikasi (rencana): `/var/www/slims`
- Web server: Caddy (port 80)
- PHP: PHP-FPM (socket lokal)
- Database: MariaDB (hanya 127.0.0.1)

## Rencana Langkah
1. Pasang paket: Caddy (sudah ada dari M03), PHP-FPM beserta ekstensi
   yang dibutuhkan SLiMS, dan MariaDB.
2. Amankan MariaDB: `sudo mysql_secure_installation`.
3. Buat database dan user khusus SLiMS (bukan root).
4. Unduh rilis SLiMS
