# Database Spasial - PostGIS

## Well Known Text (WKT)

### Definisi
Representasi tekstual dari data spasial

Contoh :
```sql
-- Primitive
POINT(0 0)
LINESTRING (30 10, 10 30, 40 40)
POLYGON ((30 10, 40 40, 20 40, 10 20, 30 10))

-- Multipart (lebih dari satu objek spasial)
MULTIPOINT ((10 40), (40 30), (20 20), (30 10))
MULTILINESTRING ((10 10, 20 20, 10 40), (40 40, 30 30, 40 20, 30 10))
MULTIPOLYGON (((30 20, 45 40, 10 40, 30 20)), ((15 5, 40 10, 10 20, 5 10, 15 5)))
GEOMETRYCOLLECTION (POINT (40 10), LINESTRING (10 10, 20 20, 10 40), POLYGON ((40 40, 20 45, 45 30, 40 40)))
```

### Dimensi

- Jika satu bagian dari objek spasial memiliki dimensi X, maka keseluruhan bagian harus berdimensi X

X, Y : Default 2 dimensi
Z : Opsional 3 dimensi, biasanya digunakan untuk mewadahi data ketinggian
M : Opsional 4 dimensi, biasanya mewadahi data yang nilai yang berubah seiring lokasi, seperti waktu

### Materi
- [WKT](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry)
- [PostGIS - DB MAnagement](https://postgis.net/docs/using_postgis_dbmanagement.html)


## Pengantar PostGIS

- Ekstensi nya PostgreSQL untuk mengelola data spasial
- Struktur databasenya sama dengan PostgreSQL, dimana hirarkinya :
  1. Database server : 1 instalasi PostGIS, 1 Docker container PostGIS
  2. Database : Pariwisata
  3. Schema : Aplikasi V1, Data Warehouse, Data Lake, Data Mart
  4A. Tables : wilayah, user, tempat
    - Kolom
      - Constraint
      - Foreign Keys
      - **Indexes**
      - Partitions
      - Triggers
    - Data
  4B. Views
  4C. Indexes
  4D. Functions
