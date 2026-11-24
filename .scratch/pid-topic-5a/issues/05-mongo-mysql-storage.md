# 05: Raw storage dan MySQL master data

**What to build:** Pesan mentah tetap tersimpan di MongoDB sementara MySQL menyimpan device, rack, dan ambang batas sebagai sumber referensi.

**Blocked by:** 03-mqtt-kafka-ingestion

**Status:** ready-for-agent

- [ ] MongoDB menyimpan pesan mentah beserta waktu ingestion.
- [ ] MySQL berisi master device, rack, dan ambang batas untuk 22 perangkat.
- [ ] Master data dapat diubah tanpa mengubah simulator.
- [ ] Integrasi ETL dapat membaca master data MySQL.
