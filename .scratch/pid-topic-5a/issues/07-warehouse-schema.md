# 07: Warehouse star schema

**What to build:** Warehouse MySQL memuat model star yang menjawab rak paling bermasalah, tren PUE, dan hasil alert 7 hari.

**Blocked by:** 05-mongo-mysql-storage, 06-airflow-etl-data-quality

**Status:** ready-for-agent

- [ ] Minimal terdapat satu tabel fakta dan tiga dimensi, termasuk waktu dan device/rack.
- [ ] Faktual PUE per jam dan per hari dapat ditanyakan.
- [ ] Fakta alert dapat memberi rentang 7 hari dan jenis alert.
- [ ] Query contoh menjawab rak paling bermasalah selama 7 hari.
- [ ] Query contoh menampilkan tren PUE harian.
