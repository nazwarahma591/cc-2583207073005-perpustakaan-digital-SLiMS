# Perpustakaan Digital SLiMS di VPS

Komputasi Awan, PTI 2802 | Pertemuan 3, Permulaan Proyek

## Deskripsi
Proyek ini memasang dan mengelola Perpustakaan Digital berbasis SLiMS
(Senayan Library Management System) di server VPS Azure. SLiMS adalah
aplikasi open source untuk katalog dan sirkulasi perpustakaan, dibangun
dengan PHP dan database MySQL/MariaDB.

## Status
- Selesai: repository, dokumentasi awal, aplikasi Flask baseline (M03)
- Direncanakan: instalasi SLiMS di VPS
- Belum: HTTPS/domain, backup, container, CI/CD

## Rencana Arsitektur
Pengguna -> Caddy (reverse proxy) -> PHP-FPM + SLiMS -> MariaDB

## Spesifikasi Server
- Ubuntu Server 24.04 LTS, VPS Azure
- 2 vCPU, sekitar 1 GB RAM, disk 61 GB

## Struktur Repository
- arsip-m03/ : baseline Flask M03 (arsip, tidak dipakai lagi)
- docs/ : requirements, architecture, deployment, adr
- .env.example : contoh variabel lingkungan (tanpa secret)

## Catatan Keamanan
Password database dan secret lain tidak disimpan di repository.
Gunakan file .env di server (sudah masuk .gitignore).

## Pengarang
Nazwa / 2583207073005 / 2A
