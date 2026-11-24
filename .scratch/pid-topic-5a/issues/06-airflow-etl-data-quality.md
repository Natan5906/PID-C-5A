# 06: Airflow ETL dan data quality

**What to build:** DAG terjadwal Airflow menggunakan Pandas dan MySQL untuk membersihkan, melaporkan, serta memuat 7 hari data historis ke warehouse.

**Blocked by:** 02-simulator, 05-mongo-mysql-storage

**Status:** ready-for-agent

- [ ] DAG Airflow terjadwal dapat dijalankan manual untuk checkpoint.
- [ ] Pandas menangani/melaporkan counter reset, satuan tidak konsisten, dan heartbeat hilang.
- [ ] Setiap jenis kotor memiliki jumlah disisipkan dan tertangkap.
- [ ] Data quality report dapat diakses atau disimpan bersama hasil ETL.
- [ ] 7 hari historis tersedia dengan parameter laju yang dapat diturunkan.
