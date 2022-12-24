# SIG_TEORI_TGS_18
 Nearest Neighbor Analysiss
 
 1. Temukan file ne_10m_populated_places_simple.zip yang diunduh di panel Browser dan luaskan. Seret file ne_10m_populated_places_simple.shp ke kanvas.

2. Anda akan melihat layer baru ne_10m_populated_places_simple dimuat di panel Layers. Lapisan ini berisi titik-titik yang mewakili tempat berpenduduk. Sekarang kita akan memuat lapisan gempa bumi. Lapisan ini hadir sebagai file teks Tab Serepated Values (TSV). Untuk memuat file ini, klik tombol Open Data Source Manager pada Data Source Toolbar. Anda juga dapat menggunakan pintasan keyboard Ctrl + L.

3. Di kotak dialog Manajer Sumber Data, pilih Teks yang Dibatasi.

4. Klik tombol … di sebelah Nama file dan telusuri file gempa bumi-2021-11-25_13-39-30_+0530.tsv yang diunduh. Bergantung pada sistem operasi, Anda mungkin tidak melihat file di direktori yang diunduh. Jika demikian, alihkan ke Semua file (*; .) dalam dialog Pilih File Teks yang Dibatasi untuk Dibuka. Setelah dibuka, pilih Pembatas khusus di bagian Format file, dan centang Tab. Di bagian Definisi geometri, pilih Koordinat titik. Secara default nilai bidang X dan bidang Y akan diisi secara otomatis dengan bidang yang sesuai di input. Dalam kasus kami, mereka adalah Bujur dan Lintang. Anda dapat membiarkan CRS Geometri ke default EPSG:4326 - WGS 84 CRS. Jika file Anda berisi koordinat dalam CRS yang berbeda, Anda dapat memilih CRS yang sesuai di sini. Klik Tambahkan diikuti oleh Tutup.

5. Perbesar dan jelajahi kedua set data. Setiap titik merah mewakili lokasi kejadian gempa bumi, dan setiap titik hijau mewakili lokasi tempat berpenduduk. Tujuan kita adalah menemukan titik terdekat dari lapisan tempat berpenduduk untuk setiap titik di lapisan gempa. Mari kita periksa tabel Atribut lapisan gempa bumi. Pilih layer dan klik ikon Open Attribute Table di Toolbar.

6. Ada 2586 fitur, tetapi data berisi sedikit entri tanpa informasi lintang atau bujur. Kami harus menghapusnya sebelum melanjutkan lebih jauh. Tutup Tabel Atribut.

7. Pergi ke Pemrosesan ‣ Kotak Alat ‣ Geometri vektor ‣ Hapus alat geometri nol. Klik dua kali untuk membukanya.

8. Di kotak dialog Hapus Geometri Null, pilih gempa bumi-2021-11-25_13-39-30_+0530 sebagai lapisan Input dan centang kotak Juga hapus geometri kosong. Klik Jalankan. Setelah pemrosesan selesai, klik Tutup.

9. Sebuah layer baru Non null geometries akan ditambahkan ke panel Layers. Untuk analisis kita akan menggunakan layer ini sebagai pengganti layer aslinya. Hapus centang pada layer gempa bumi-2021-11-25_13-39-30_+0530 di panel Layers untuk menyembunyikannya. Pilih layer Non null geometries dan klik tombol Open Attribute Table dari Attributes Toolbar.

10. Anda akan melihat jumlah fitur total yang lebih rendah karena semua baris dengan nilai lintang dan bujur kosong telah dihapus. Tutup tabel atribut.

11. Sekarang saatnya untuk melakukan analisis tetangga terdekat. Cari dan temukan Pemrosesan ‣ Toolbox ‣ Analisis vektor ‣ Jarak ke alat hub (baris ke hub) terdekat. Klik dua kali untuk meluncurkannya.

Catatan

Kita juga dapat menambahkan lapisan titik sebagai keluaran, gunakan alat Jarak ke hub (titik) terdekat untuk itu.

12. Dalam kotak dialog Distance to Nearest Hub (Line to Hub), pilih Non null geometries sebagai layer Source points. Pilih ne_10m_populated_places_simple sebagai layer Destination hubs. Pilih nama sebagai atribut nama lapisan Hub. Alat ini juga akan menghitung jarak garis lurus antara tempat berpenduduk dan gempa terdekat. Tetapkan Kilometer sebagai unit Pengukuran. Klik ... di Jarak Hub dan klik Simpan ke Berkas… untuk menyimpan berkas sebagai gempa bumi_dengan_kota terdekat.gpkg . Klik Jalankan. Setelah pemrosesan selesai, klik Tutup.


13. Kembali ke jendela utama QGIS, Anda akan melihat lapisan garis baru bernama gempa bumi_dengan_kota terdekat dimuat di panel Lapisan. Lapisan ini memiliki ciri-ciri garis yang menghubungkan setiap titik gempa dengan tempat berpenduduk terdekat. Pilih layer gempa bumi_dengan_terdekat_kota dan klik ikon Buka Tabel Atribut di Bilah Alat.


14. Gulir ke kanan ke kolom terakhir, dan Anda akan melihat 2 atribut baru bernama HubName dan HubDist ditambahkan ke fitur gempa asli. Ini adalah nama jarak ke tetangga terdekat dari layer tempat berpenduduk.
