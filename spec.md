# Spec - Topik 5A Rak Server

## Problem Statement

Kelompok perlu membangun pipeline data end-to-end untuk memantau kesehatan data center rak server secara real-time dan historis, memenuhi kriteria milestone, demonstrasi, serta rubrik individual.

## Solution

Bangun proyek Docker Compose terpisah yang mensimulasikan 16 server, 4 PDU, dan 2 CRAC. Simulator mengirim telemetri MQTT ke bridge/Kafka, diproses oleh Spark Structured Streaming, disimpan mentah ke MongoDB, diproses batch oleh Airflow dengan Pandas dan MySQL master data, dimuat ke data warehouse, serta ditampilkan pada dashboard real-time dan historis.

## User Stories

1. Sebagai operator data center, saya ingin melihat telemetri server, PDU, dan CRAC secara real-time.
2. Sebagai operator, saya ingin menerima alert ketika window inlet 5 menit melampaui 27 °C.
3. Sebagai operator, saya ingin membandingkan outlet minus inlet antar-rak untuk menemukan hotspot.
4. Sebagai operator, saya ingin melihat PUE berjalan per jam dan per hari.
5. Sebagai operator, saya ingin mengetahui apakah device kehilangan heartbeat lebih dari 2 menit.
6. Sebagai operator, saya ingin melihat metrik window 1 menit dan 5 menit per rak.
7. Sebagai operator, saya ingin melihat korelasi beban CPU, suhu, dan daya secara historis.
8. Sebagai engineer, saya ingin simulator menghasilkan 22 perangkat dengan beban realistis.
9. Sebagai engineer, saya ingin satu hotspot disimulasikan secara terkontrol dan dapat diulang.
10. Sebagai engineer, saya ingin menyisipkan counter reset, satuan tidak konsisten, dan heartbeat hilang secara terkontrol.
11. Sebagai engineer, saya ingin laporan menyebut jumlah setiap jenis kotor yang disisipkan dan tertangkap.
12. Sebagai engineer, saya ingin backfill 7 hari tersedia dengan laju yang dapat diturunkan untuk pengujian.
13. Sebagai engineer, saya ingin menjalankan seluruh stack dari README lewat `docker compose up`.
14. Sebagai engineer, saya ingin mySQL menyimpan master device, lokasi/rak, dan ambang batas.
15. Sebagai engineer, saya ingin Airflow menjalankan ETL terjadwal dengan pemeriksaan data quality.
16. Sebagai analyst, saya ingin warehouse menjawab rak paling bermasalah selama 7 hari.
17. Sebagai analyst, saya ingin warehouse menampilkan tren PUE harian.
18. Sebagai dosen, saya ingin demo mengikuti alur simulator, MQTT, Kafka, Spark, MongoDB, warehouse, dan dashboard.
19. Sebagai anggota kelompok, saya ingin memiliki komponen yang terbukti dari riwayat commit dan dapat dijelaskan.
20. Sebagai mahasiswa, saya ingin laporan dan demo mencakup pernyataan penggunaan AI.

## Implementation Decisions

- Topik: 5A, Varian A — Rak Server.
- Komposisi simulasi minimum: 16 server, 4 PDU, dan 2 CRAC.
- Pesan wajib memiliki `device_id`, `device_type`, `timestamp`, `data`, dan `rack_id`.
- Ingestion mengikuti MQTT → bridge → Kafka.
- Streaming menghasilkan agregat 1 dan 5 menit serta alert hotspot dan heartbeat.
- PUE dihitung sebagai total daya fasilitas dibagi daya IT untuk agregat per jam dan per hari.
- Raw message disimpan ke MongoDB; master data disimpan MySQL.
- Airflow menjadwalkan ETL Pandas; hasil batch dimuat ke warehouse.
- Engine warehouse adalah MySQL untuk menyederhanakan integrasi dan reprodusibilitas awal.
- Data kotor wajib: counter reset, satuan tidak konsisten, dan heartbeat hilang.
- Setiap jenis kotor harus memiliki jumlah inserted dan captured.
- Backfill 7 hari didukung oleh parameter laju simulator sehingga pengujian dapat dipercepat.
- Dashboard dapat dipilih setelah integrasi Spark berjalan; dashboard harus menampilkan real-time dan historis.
- Kontribusi dibagi sebagai tiket independen namun beberapa komponen tetap memiliki blocking edge teknis.
- Nama folder final mengikuti PID-C-XX setelah dosen memberikan pemetaan.
- Repository final harus tidak mencantumkan volume database, virtual environment, atau credential pribadi.

## Testing Decisions

- Tes external behavior diwajibkan untuk simulator, bridge, alert, data quality, dan start-compose.
- Smoke test wajib membuktikan 22 perangkat terkirim, agregat muncul, pesan mentah tersimpan, warehouse terisi, dan dashboard aktif.
- W3 wajib membuktikan alur publish simulator → MQTT → Kafka → Spark → MongoDB.
- W5 wajib membuktikan DAG Airflow, star schema, dashboard real-time/historis, dan signature PUE/hotspot.
- W6 wajib membuktikan demo penuh, laporan, slide, video maksimal 5 menit, dan refleksi individual.
- Reproduksi dinilai dari README dan `docker compose up` tanpa perbaikan manual.

## Out of Scope

- Perangkat fisik dan layanan cloud berbayar.
- Machine learning sebagai syarat utama; model ML hanya bonus.
- Dua varian topik yang sama sekaligus.
- Perbaikan modul lama yang tidak diperlukan oleh proyek Topik 5A.

## Further Notes

- Fork baru/di folder terpisah agar modul lama dan perubahan lokal yang belum selesai tidak terganggu.
- Milestone W1/W3/W5/W6 adalah acceptance gate, bukan sekadar dokumen progres.
- Kontribusi individu dinilai dari commit, komponen, refleksi, dan kemampuan tanya jawab.
