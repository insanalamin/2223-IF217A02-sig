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
  3. Schema : Koleksi sekumpulan Table, contoh: Aplikasi V1, Data Warehouse, Data Lake, Data Mart
  4A. Tables : wilayah, user, tempat
    - Kolom
      - Constraint : Kombinasi satu kolom atau lebih yang menjadikan row unik
      - Foreign Keys : Tautan ke Primary Key dari kolom di tabel A ke kolom di tabel B
      - **Indexes** : Menambahkan struktur data untuk mempercepat query
      - Partitions : Mengoptimasi penyimpanan dengan membagi data berdasarkan kolom tertentu, misal partitioned by province
      - Triggers : Respon otomatis dari event tertentu di database
    - Data
  4B. Views : Tabel virtual yang dibuat dari query yang disimpan, biasanya digunakan untuk simpan statistik dari query yang kompleks
  4C. Materialized View : View yang dibuat strukturnya secara fisik di storage
  4C. Indexes
  4D. Functions
  
## Pendefinisian Data - Create Table
  
### Buat Schema
 ```sql
CREATE SCHEMA jabar;
```

### Buat Table
```sql
CREATE TABLE jabar.pariwisata(
  id_tempat SERIAL PRIMARY KEY, 
  nama_tempat VARCHAR, 
  kategori INT, 
  koordinat GEOMETRY(POINT, 4326), 
  lahan GEOMETRY(POLYGON, 4326)
);
```

## Manipulasi Data - Insert Query

### Menambahkan Data
```sql
INSERT INTO jabar.pariwisata(nama_tempat, kategori, koordinat)
VALUES('Trans Studio Mall', 3, ST_GeomFromText('POINT(107.238943844 -6.324324322)', 4326));
```

### Operasi Spasial
- Teks dan Geometry
  - ST_GeomFromText : buat geometry dari teks WKT
  - ST_AsText : buat teks WKT dari geometry
  - [ST_AsGeoJSON](https://postgis.net/docs/ST_AsGeoJSON.html) : membuat GeoJSON dari koleksi fitur
- Hitung Properti Geometry
  - ST_Length : ngukur panjang
  - ST_Area : ngukur luas
- Hubungan Antar Geometry
  - ST_Contains : keseluruhan A ada di dalem B
  - ST_Equals : geometry persis sama
  - ST_Overlaps : geometry sama, saling kait
  - ST_Distance : jarak terdekat dari dua geometry
  - ST_Centroid : hitung titik tengah geometry

### Materi
- [Referensi PostGIS](https://postgis.net/docs/reference.html)
