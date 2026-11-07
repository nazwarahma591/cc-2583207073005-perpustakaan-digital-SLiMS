# ADR-0002: Arsitektur untuk Perpustakaan Digital SLiMS

## Status
Accepted (menggantikan ADR-0001)

## Context
Proyek berganti dari Ringkasan Materi (Flask) menjadi Perpustakaan Digital
berbasis SLiMS. SLiMS adalah aplikasi PHP yang membutuhkan database
MySQL/MariaDB. VPS tetap sama: Azure Ubuntu Server 24.04, 2 vCPU,
sekitar 1 GB RAM, disk 61 GB.

## Decision
Caddy sebagai web server dan reverse proxy, PHP-FPM untuk menjalankan
SLiMS, MariaDB sebagai database (hanya listen di 127.0.0.1), UFW, dan
GitHub untuk dokumentasi. Baseline Flask M03 diarsipkan di arsip-m03/.

## Alternatives
1. NGINX + PHP-FPM
2. Apache + mod_php
3. Docker (SLiMS dalam container)
4. Tetap Flask dan membuat sistem perpustakaan sendiri

## Rationale
SLiMS sudah menyediakan katalog, anggota, dan sirkulasi, sehingga tidak
perlu membangun dari nol. SLiMS berjalan di PHP, jadi Flask/Gunicorn
tidak lagi relevan. Caddy dipertahankan karena sudah terpasang dan
terkonfigurasi sejak M03, serta mudah ditingkatkan ke HTTPS otomatis
pada M04. PHP-FPM lebih hemat RAM daripada Apache dengan mod_php.
MariaDB dipilih karena kompatibel dengan SLiMS dan lebih ringan.
Docker belum dipakai karena containerization adalah materi M06.

## Consequences
### Positive
- Fitur perpustakaan lengkap tanpa membangun dari nol
- Caddy dan UFW dari M03 dapat dipakai ulang
### Negative
- RAM 1 GB ketat untuk PHP-FPM dan MariaDB sekaligus, perlu tuning
- Satu server tanpa redundansi, belum ada backup database
- HTTP belum terenkripsi pada tahap ini
- Perlu pembaruan keamanan SLiMS secara berkala

## Review Trigger
Review pada M04 (HTTPS) dan M06 (container).
