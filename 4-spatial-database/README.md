# Database Spasial - PostGIS

## Well Known Text (WKT)

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

Materi :
- [WKT](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry)
- [PostGIS - DB MAnagement](https://postgis.net/docs/using_postgis_dbmanagement.html)
