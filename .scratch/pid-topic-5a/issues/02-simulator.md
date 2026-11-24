# 02: Simulator dan pola beban

**What to build:** Simulator Python menghasilkan 22 perangkat realistic dan dapat menyisipkan tiga jenis data kotor Topik 5A secara terukur serta mendokumentasikan jumlah injeksi.

**Blocked by:** 01-foundation-compose

**Status:** ready-for-agent

- [ ] 16 server, 4 PDU, dan 2 CRAC memiliki `device_id`, `device_type`, `timestamp`, `rack_id`, dan data field yang tepat.
- [ ] Laju default mendekati satu pesan/detik/perangkat.
- [ ] Terdapat pola beban dan minimal satu kejadian hotspot yang dapat direproduksi.
- [ ] Counter reset, satuan tidak konsisten, dan heartbeat hilang dapat dinyalakan melalui konfigurasi.
- [ ] Simulator melaporkan jumlah pesan dan jumlah injeksi per jenis kotor.
