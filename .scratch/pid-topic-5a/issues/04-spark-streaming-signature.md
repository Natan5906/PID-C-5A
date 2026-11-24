# 04: Spark streaming dan signature

**What to build:** Spark menghasilkan agregat real-time 1 menit dan 5 menit, mendeteksi hotspot/heartbeat, serta menghitung PUE per jam dan per hari.

**Blocked by:** 03-mqtt-kafka-ingestion

**Status:** ready-for-agent

- [ ] Agregat per rak tersedia untuk window 1 menit dan 5 menit.
- [ ] Hotspot terdeteksi untuk inlet rata-rata 5 menit di atas 27 °C.
- [ ] Perangkat tanpa heartbeat lebih dari 2 menit menghasilkan alert.
- [ ] PUE dihitung sebagai daya fasilitas dibagi daya IT per jam dan per hari.
- [ ] Hasil streaming dapat dilihat/didemonstrasikan oleh komponen downstream.
