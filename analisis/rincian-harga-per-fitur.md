# Rincian Harga per Fitur: 47 Fitur Terbangun

**Tanggal:** 29 September 2026 · **Dokumen internal** · Sumber level: *Peta Fitur dan Tingkat Kesulitan ERP Pridata* (2026-09-28). Bobot: kalibrasi ATO-2 §1.2.

## 1. Metode

1. **Effort per fitur** memakai bobot terkalibrasi ATO-2 (Ringan 0,5 · Menengah 2,0 · Tinggi 4,0 · Inti 6,0 hari kerja), ditambah overhead non-fitur 55,5% (discovery, arsitektur, QA/UAT, deployment, manajemen proyek). Hasilnya **252 hari kerja**, sama dengan kalender pembangunan terkonfirmasi (2 orang × 6 bulan).
2. **Nilai pengembangan** = effort × rate. Dua rate ditampilkan: biaya internal Rp 950.000/od (asumsi A3, belum diverifikasi penggajian) dan tarif tagih Rp 1.750.000/od (tarif yang kita pakai untuk pekerjaan baru).
3. **Harga lisensi standar** membagi Rp 60.000.000 (harga standar di proposal) dengan rasio mendekati bobot 1 : 4 : 8 : 12, dibulatkan ke angka rapi: **Rp 175.000 / Rp 750.000 / Rp 1.500.000 / Rp 2.200.000** per fitur. Pembulatan ini membuat rasio sedikit bergeser (1 : 4,3 : 8,6 : 12,6) supaya totalnya tepat Rp 60.000.000.
4. **Harga Pridata** = 50% harga standar (potongan Mitra Pengguna Pertama) = Rp 30.000.000. Modul Penerimaan Barang, 12 poin penyesuaian, implementasi, dan VPS 24 bulan tidak dialokasikan ke fitur karena termasuk tanpa tambahan biaya.
5. **Batasan:** effort seragam dalam satu tingkat. Tidak ada catatan waktu per fitur, jadi perbedaan antar-fitur di tingkat yang sama (misalnya analitik pemilik yang memakai kueri terbesar dibanding observability) tidak dimodelkan. Rincian ini adalah alokasi, bukan pengukuran.

## 2. Ringkasan per tingkat

| Tingkat | Fitur | Hari kerja / fitur | Nilai bangun / fitur (Rp 950 rb) | Nilai bangun / fitur (Rp 1,75 jt) | Harga standar / fitur | Pridata / fitur | Subtotal standar | Subtotal Pridata |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Ringan | 8 | 0,8 | Rp 738.889 | Rp 1.361.111 | Rp 175.000 | Rp 87.500 | Rp 1.400.000 | Rp 700.000 |
| Menengah | 12 | 3,1 | Rp 2.955.556 | Rp 5.444.444 | Rp 750.000 | Rp 375.000 | Rp 9.000.000 | Rp 4.500.000 |
| Tinggi | 14 | 6,2 | Rp 5.911.111 | Rp 10.888.889 | Rp 1.500.000 | Rp 750.000 | Rp 21.000.000 | Rp 10.500.000 |
| Inti | 13 | 9,3 | Rp 8.866.667 | Rp 16.333.333 | Rp 2.200.000 | Rp 1.100.000 | Rp 28.600.000 | Rp 14.300.000 |
| **Jumlah** | **47** | **252,0** | **Rp 239.400.000** | **Rp 441.000.000** | | | **Rp 60.000.000** | **Rp 30.000.000** |

- **Harga standar = 25,1% dari nilai bangun internal** dan **13,6% dari nilai di tarif tagih.** Harga Pridata separuhnya.

## 3. Rincian 47 fitur

| Kelompok | Fitur | Tingkat | Hari kerja | Nilai bangun (Rp 950 rb/od) | Harga standar | Pridata |
|---|---|---|---:|---:|---:|---:|
| Data induk | Brand, kategori, kota | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Data induk | Divisi & sub-divisi | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Data induk | Supplier | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Data induk | Gudang | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Data induk | Produk | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Data induk | Impor produk dari Excel | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Penjualan & pelanggan | Toko & registrasi toko | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Penjualan & pelanggan | Grade toko (harga & diskon otomatis) | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Penjualan & pelanggan | Penugasan sales ke toko | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Penjualan & pelanggan | Katalog digital | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Penjualan & pelanggan | Pesanan | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penjualan & pelanggan | Pesanan dari toko | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Penjualan & pelanggan | Target & KPI sales | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Draf invoice → invoice | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Invoice tunai | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Invoice PDF | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Pembayaran | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Bukti transfer dari toko | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Umur piutang | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Penagihan, piutang & kas | Buku invoice & saldo kredit toko | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Gudang & persediaan | Delivery Order | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Gudang & persediaan | Driver | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Gudang & persediaan | Pengguna per gudang | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Gudang & persediaan | Transfer antar gudang | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Gudang & persediaan | Penyesuaian stok | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Gudang & persediaan | Stock opname | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Gudang & persediaan | Retur barang | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Gudang & persediaan | Buku besar stok | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Laporan & analitik | Dasbor per peran | Tinggi | 6,2 | Rp 5.911.111 | Rp 1.500.000 | Rp 750.000 |
| Laporan & analitik | Analitik pemilik & akuntan | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Laporan & analitik | Laporan & ekspor CSV/Excel/PDF | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Laporan & analitik | Template laporan | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Laporan & analitik | Laporan bulanan otomatis | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Laporan & analitik | Riwayat ekspor | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Pengguna & keamanan | Login & hak akses berlapis | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Pengguna & keamanan | Kelola pengguna | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Pengguna & keamanan | Daftar peran | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Pengguna & keamanan | Profil pengguna | Ringan | 0,8 | Rp 738.889 | Rp 175.000 | Rp 87.500 |
| Pengguna & keamanan | Pembatasan toko per pengguna | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Pengguna & keamanan | Jejak audit | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Otomasi & integrasi | Notifikasi | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Otomasi & integrasi | Layar diperbarui seketika | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Otomasi & integrasi | Pekerjaan berat di latar | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Otomasi & integrasi | Kunci API | Menengah | 3,1 | Rp 2.955.556 | Rp 750.000 | Rp 375.000 |
| Keandalan | Perlindungan akses | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Keandalan | Log untuk menelusuri gangguan | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| Keandalan | Uji otomatis setiap pembaruan | Inti | 9,3 | Rp 8.866.667 | Rp 2.200.000 | Rp 1.100.000 |
| | **Jumlah** | | **252,0** | **Rp 239.400.000** | **Rp 60.000.000** | **Rp 30.000.000** |

## 4. Subtotal per kelompok bisnis

| Kelompok | Fitur | Hari kerja | Harga standar | Pridata |
|---|---:|---:|---:|---:|
| Data induk | 6 | 15,6 | Rp 3.650.000 | Rp 1.825.000 |
| Penjualan & pelanggan | 7 | 28,0 | Rp 6.750.000 | Rp 3.375.000 |
| Penagihan, piutang & kas | 7 | 46,7 | Rp 11.200.000 | Rp 5.600.000 |
| Gudang & persediaan | 8 | 44,3 | Rp 10.625.000 | Rp 5.312.500 |
| Laporan & analitik | 6 | 38,1 | Rp 9.025.000 | Rp 4.512.500 |
| Pengguna & keamanan | 6 | 26,4 | Rp 6.250.000 | Rp 3.125.000 |
| Otomasi & integrasi | 4 | 24,9 | Rp 5.900.000 | Rp 2.950.000 |
| Keandalan | 3 | 28,0 | Rp 6.600.000 | Rp 3.300.000 |
| **Jumlah** | **47** | **252,0** | **Rp 60.000.000** | **Rp 30.000.000** |

## 5. Pemakaian untuk penyesuaian dan pekerjaan baru

Bobot yang sama dipakai untuk menilai pekerjaan baru. Karena itu kuota 12 poin di proposal konsisten dengan tabel ini: **ringan = 1 poin ≈ 0,8 hari kerja**, **menengah = 4 poin ≈ 3,1 hari kerja**. Fitur baru tingkat Tinggi atau Inti tidak masuk kuota. Harganya dihitung dengan hari kerja × Rp 1.750.000, dan perkiraannya: Tinggi ±6,2 hari (±Rp 10,9 jt), Inti ±9,3 hari (±Rp 16,3 jt) per fitur.
