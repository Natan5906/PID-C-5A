# Topik 5A - Rak Server

Sistem pemantauan kesehatan infrastruktur data center untuk beberapa rak server, PDU, dan CRAC.

## Language

**Rak**:
Kelompok perangkat server yang diidentifikasi dengan `rack_id`.

**Perangkat**:
Entitas telemetri dengan `device_id`, `device_type`, dan lokasi yang relevan.

**Pesan telemetri**:
Pembacaan JSON satu kali dari perangkat dengan timestamp dan payload metrik.

**Hotspot**:
Rak yang memiliki rata-rata inlet 5 menit di atas 27 °C atau menyimpang jauh dari pola temperatur rak lain.

**PUE**:
Rasio total daya fasilitas terhadap daya IT, dihitung untuk periode satu jam dan satu hari.

**Data kotor**:
Pesan yang sengaja menyisihkan counter reset, satuan tidak konsisten, atau heartbeat hilang untuk diuji pipeline.
