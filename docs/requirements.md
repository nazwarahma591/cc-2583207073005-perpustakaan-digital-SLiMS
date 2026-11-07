# Requirements

## Problem Statement
Pengelolaan koleksi dan sirkulasi perpustakaan secara manual (buku catatan
atau spreadsheet) sulit dicari, rawan salah, dan tidak bisa diakses dari
jauh. Proyek ini menyediakan Perpustakaan Digital berbasis SLiMS yang
berjalan di VPS, sehingga katalog bisa dicari secara online dan pustakawan
mengelola koleksi lewat satu sistem.

## Target Users
- Pengunjung: mencari dan melihat katalog buku (OPAC)
- Pustakawan/admin: mengelola koleksi, anggota, dan sirkulasi

## User Need
- Sebagai pengunjung, saya ingin mencari buku lewat katalog online,
  sehingga saya tahu buku tersedia tanpa datang ke perpustakaan.
- Sebagai pustakawan, saya ingin menambah dan mengubah data buku,
  sehingga katalog selalu mutakhir.
- Sebagai pustakawan, saya ingin mencatat peminjaman dan pengembalian,
  sehingga status buku jelas.

## Functional Requirements
- FR-01 Sistem menampilkan katalog publik (OPAC) yang bisa dicari.
- FR-02 Pustakawan dapat login ke panel admin.
- FR-03 Pustakawan dapat mengelola data bibliografi (tambah, ubah, hapus).
- FR-04 Pustakawan dapat mengelola data anggota.
- FR-05 Pustakawan dapat mencatat peminjaman dan pengembalian.
- FR-06 Sistem dapat diakses publik lewat alamat IP/domain VPS.

## Non-Functional Requirements
- NFR-01 Database MariaDB hanya listen di loopback (127.0.0.1).
- NFR-02 Request publik masuk lewat reverse proxy (Caddy).
- NFR-03 Password admin bawaan SLiMS diganti sebelum dipakai.
- NFR-04 Secret (password database) tidak disimpan di repository.
- NFR-05 Folder instalasi (install) dihapus setelah setup selesai.
- NFR-06 Arsitektur sesuai kapasitas VPS (RAM sekitar 1 GB).
- NFR-07 Prosedur deployment terdokumentasi dan dapat diulang.

## Scope
In scope: instalasi SLiMS (PHP-FPM, MariaDB, Caddy), konfigurasi dasar,
dokumentasi.
Out of scope: HTTPS/domain, backup otomatis, Docker, IaC, CI/CD,
monitoring penuh.

## Constraints
- Ubuntu Server 24.04 LTS, VPS Azure, public IPv4
- 2 vCPU, sekitar 1 GB RAM, disk 61 GB
- SLiMS membutuhkan PHP dan MySQL/MariaDB

## Acceptance Criteria
- [ ] SLiMS terpasang di VPS
- [ ] Katalog publik dapat dibuka lewat IP VPS
- [ ] Login admin berfungsi dan password bawaan sudah diganti
- [ ] Satu data buku berhasil ditambahkan dan muncul di katalog
