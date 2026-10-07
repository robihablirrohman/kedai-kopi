# Database Sistem Manajemen Kedai Kopi

This document describes the database schema of Kedai Kopi and every Eloquent relationship used in the project.

## 1. Entity Relationship Diagram

```mermaid
erDiagram
    PELANGGAN {
        bigint id PK
        string nama
        string no_telepon
        string alamat
    }

    KARYAWAN {
        bigint id PK
        string nama
        string jabatan
        string no_telepon
    }

    KATEGORI {
        bigint id PK
        string nama_kategori UK
    }

    MENU {
        bigint id PK
        bigint kategori_id FK
        string nama_menu
        decimal harga
        int stok
        string status
    }

    PESANAN {
        bigint id PK
        bigint pelanggan_id FK
        bigint karyawan_id FK
        date tanggal
        decimal total
        string metode_pembayaran
    }

    DETAIL_PESANAN {
        bigint id PK
        bigint pesanan_id FK
        bigint menu_id FK
        int jumlah
        decimal harga
        decimal subtotal
    }

    KATEGORI ||--o{ MENU : memiliki
    PELANGGAN ||--o{ PESANAN : melakukan
    KARYAWAN ||--o{ PESANAN : menangani
    PESANAN ||--|{ DETAIL_PESANAN : memiliki
    MENU ||--o{ DETAIL_PESANAN : dipesan
