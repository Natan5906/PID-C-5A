# 03: MQTT dan Kafka ingestion

**What to build:** Telemetri dari simulator melewati MQTT dan bridge ke Kafka sebagai aliran JSON yang dapat diverifikasi.

**Blocked by:** 01-foundation-compose, 02-simulator

**Status:** ready-for-agent

- [ ] Simulator publish ke MQTT dan bridge mengirimnya ke Kafka tanpa kehilangan schema wajib.
- [ ] Pesan yang tidak valid dapat ditandai tanpa menghentikan seluruh pipeline.
- [ ] Topic dan schema pesan terdokumentasi.
- [ ] Smoke test membuktikan perangkat dan payload terlihat di Kafka.
