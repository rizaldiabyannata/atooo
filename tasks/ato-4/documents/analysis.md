# Skema Penjualan & Syarat Kemitraan 2 Arah — CV Pridata Jaya

**Tugas:** [ATO-4](/ATO/issues/ATO-4) · **Tanggal:** 29 September 2026 · **Dokumen internal — tidak untuk dikirim ke Pridata**

**Input:** [ATO-2](/ATO/issues/ATO-2) Revisi 3 (biaya & harga), [ATO-3](/ATO/issues/ATO-3) (diagnosis & Fase 2), Daftar Harga **NTB-PL-2026-09** (terbit), keputusan user di [ATO-6](/ATO/issues/ATO-6): omzet Pridata ± **Rp 2 miliar per tahun**.

**Catatan penyusunan.** Rani berhenti di tengah tugas ini (run gagal: *terminal access failure*). Dokumen ini disusun dari export Paperclip `ato-team` tanggal 29 September 2026, memakai angka ATO-2/ATO-3 apa adanya. Setiap angka bisa ditelusuri ke sumbernya (kolom "Asal"). Semua angka dalam Rupiah (Rp), belum termasuk PPN.

---

## 0. Kesimpulan

| | |
|---|---|
| **Model yang direkomendasikan** | **(a) Lisensi perpetual + ASC, dijalankan lewat Program Mitra Riset** — Opsi A NTB-PL-2026-09 dengan varian ASC tanpa hosting terkelola |
| **Harga sistem untuk Pridata** | Harga list Rp 175.000.000 − Potongan Mitra Riset Rp 87.500.000 = **Rp 87.500.000** |
| **ASC** | **Rp 27.500.000/tahun**, potongan **Rp 0**, mulai bulan ke-7 setelah go-live |
| **Termin** | 4 termin terikat milestone (§3), atas nilai setelah potongan: Rp 26.250.000 / 21.875.000 / 21.875.000 / 17.500.000 |
| **Berubah dari ATO-2** | **K4 (komitmen ASC minimum 3 tahun) dicabut.** Alasannya skala Rp 2 miliar/tahun (§1) |
| **Risiko terbesar** | **Pridata tidak sanggup menanggung biaya berjalan**, lalu menghentikan ASC di Tahun 2. Bukan penolakan harga. |

**Temuan yang harus dibaca lebih dulu, dan ini bukan kabar baik:**

> **Pada omzet Rp 2 miliar/tahun, tidak ada satu pun struktur di NTB-PL-2026-09 yang bisa dibenarkan oleh penghematan yang bisa dihitung.** Nilai tahunan sistem yang bisa dikuantifikasi hanya **Rp 14.650.000** (ATO-2 §3.4, pembacaan 2, keyakinan Rendah). Biaya berjalan struktur *termurah* saja sudah **Rp 47.900.000/tahun** — 3,3 kali nilainya. Payback pada struktur termurah ±**14,5 tahun**.

Ini bukan alasan untuk membatalkan penawaran, tapi ia mengubah **apa yang boleh diklaim** di penawaran dan **kapan penawaran boleh dikirim** (§8):

1. Penawaran **tidak boleh** memuat klaim hemat, payback, atau ROI. Nilai yang bisa dijual jujur adalah **kendali dan keterlacakan**, bukan penghematan.
2. Sebelum dikirim, angka skala Pridata (omzet, marjin, kas) sebaiknya **diverifikasi dengan Pridata sendiri** oleh Ace. Seluruh uji kemampuan bayar di §1 memakai marjin generik (asumsi), bukan data Pridata.
3. Ini keputusan komersial user. Saya merekomendasikan struktur termurah dan menyatakan batasnya. Saya tidak memutuskan mengirim atau tidak.

---

## 1. Uji kemampuan bayar pada omzet Rp 2 miliar/tahun

**Asumsi (bukan data Pridata):** marjin kotor distributor 10–15% → laba kotor **Rp 200–300 juta/tahun** (angka Ace di ATO-4); marjin bersih 3–5% → laba bersih **Rp 60–100 juta/tahun** (asumsi ATO-2 §3.4). Omzet bulanan = Rp 166.700.000.

| Asal | Nilai |
|---|---:|
| Nilai tahunan sistem yang bisa dikuantifikasi (ATO-2 §3.4, omzet Rp 2 miliar/tahun) | **Rp 14.650.000** |
| Biaya berjalan struktur termurah: ASC Rp 27.500.000 + VPS ± Rp 20.400.000 (ATO-2 §2, §4) | **Rp 47.900.000** |
| Nilai tahunan ÷ biaya berjalan | **31%** |
| Payback total biaya kepemilikan 3 tahun (Rp 212.350.000) ÷ nilai tahunan | **±14,5 tahun** |

Model nilai hanya menghitung manfaat yang bisa dikuantifikasi (selisih stok, piutang macet, waktu staf, kesalahan harga). Kendali, jejak audit, dan pemisahan peran tidak masuk hitungan, jadi Rp 14.650.000 adalah **batas bawah manfaat**, bukan taksiran manfaat. Tetapi ia juga tidak boleh dipakai sebagai alasan menaikkan klaim di penawaran.

---

## 2. Perbandingan tiga model penjualan

Semua angka untuk Pridata. "Dibayar ke Ato-team" adalah penerimaan Ato-team. "Total biaya Pridata" menambah infrastruktur yang dibayar Pridata langsung.

**Konvensi kolom tahun:** Tahun 1 = 12 bulan sejak tanda tangan. Pada Model A, ASC baru berjalan bulan ke-7 (konsesi C1), jadi Tahun 1 memuat 6 bulan ASC. VPS Tahun 1 dihitung 9 bulan (Rp 15.300.000), sama dengan konvensi ATO-2 §4 untuk pembeli baru.

### (a) Lisensi perpetual + ASC — Opsi A dengan Potongan Mitra Riset

| | Tahun 1 | Tahun 2 | Tahun 3 | **3 tahun** | Asal |
|---|---:|---:|---:|---:|---|
| Harga list sistem | Rp 175.000.000 | — | — | Rp 175.000.000 | NTB-PL-2026-09 §1.1 |
| Potongan Mitra Riset | −Rp 87.500.000 | — | — | −Rp 87.500.000 | ATO-2 §6.3 |
| ASC Dasar tanpa hosting terkelola | Rp 13.750.000 | Rp 27.500.000 | Rp 27.500.000 | Rp 68.750.000 | §4.1; C1 dan C3 |
| **Dibayar ke Ato-team** | **Rp 101.250.000** | **Rp 27.500.000** | **Rp 27.500.000** | **Rp 156.250.000** | |
| VPS milik Pridata | Rp 15.300.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 56.100.000 | ATO-2 A4 |
| **Total biaya Pridata** | **Rp 116.550.000** | **Rp 47.900.000** | **Rp 47.900.000** | **Rp 212.350.000** | |

### (b) Langganan — Opsi B NTB-PL-2026-09

Opsi B terbit memakai **hosting terkelola** (Rp 9.250.000/bulan), jadi tidak ada VPS terpisah. Varian Rp 7.000.000/bulan tanpa hosting di ATO-2 §4 **tidak terbit**, dan Ace melarang struktur baru di luar daftar harga, jadi tidak dipakai.

Potongan Mitra Riset atas Opsi B: **Rp 87.500.000** (nilai rupiah yang sama dengan Model A, didukung nilai kewajiban K1–K3 dan K5 senilai Rp 124.250.000), dikreditkan merata 36 bulan = Rp 2.430.556/bulan. Komponen hosting Rp 26.500.000/tahun tidak dipotong (Program §7 butir 3). Potongan tetap ≤ komponen non-hosting (Rp 298.500.000 selama 3 tahun).

| | Tahun 1 | Tahun 2 | Tahun 3 | **3 tahun** |
|---|---:|---:|---:|---:|
| Aktivasi & implementasi | Rp 45.000.000 | — | — | Rp 45.000.000 |
| Langganan 12 bulan × Rp 9.250.000 | Rp 111.000.000 | Rp 111.000.000 | Rp 111.000.000 | Rp 333.000.000 |
| Potongan Mitra Riset (kredit merata) | −Rp 29.166.667 | −Rp 29.166.667 | −Rp 29.166.667 | −Rp 87.500.000 |
| **Dibayar ke Ato-team = total biaya Pridata** | **Rp 126.833.333** | **Rp 81.833.333** | **Rp 81.833.333** | **Rp 290.500.000** |
| Setara per bulan setelah potongan | | Rp 6.819.444 | | |

Tidak ada lisensi milik Pridata di akhir Tahun 3. Kontrak minimum 3 tahun.

### (c) Kemitraan jangka panjang — harga masuk rendah + komitmen multi-tahun

Ini "Opsi C" ATO-2 §4. **Ia tidak ada di NTB-PL-2026-09** dan menerbitkannya butuh revisi daftar harga. Dipakai di sini hanya sebagai pembanding. Tidak ditumpuk dengan Potongan Mitra Riset karena akan menghitung komitmen multi-tahun dua kali.

| | Tahun 1 | Tahun 2 | Tahun 3 | **3 tahun** | 5 tahun |
|---|---:|---:|---:|---:|---:|
| Lisensi (potongan Rp 35.000.000 dari list) | Rp 70.000.000 | — | — | Rp 70.000.000 | Rp 70.000.000 |
| Implementasi | Rp 70.000.000 | — | — | Rp 70.000.000 | Rp 70.000.000 |
| ASC **Standar** tanpa hosting, wajib 5 tahun, terkunci | Rp 38.625.000 | Rp 51.500.000 | Rp 51.500.000 | Rp 141.625.000 | Rp 244.625.000 |
| **Dibayar ke Ato-team** | **Rp 178.625.000** | **Rp 51.500.000** | **Rp 51.500.000** | **Rp 281.625.000** | Rp 384.625.000 |
| VPS milik Pridata | Rp 15.300.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 56.100.000 | |
| **Total biaya Pridata** | **Rp 193.925.000** | **Rp 71.900.000** | **Rp 71.900.000** | **Rp 337.725.000** | Rp 481.525.000 |

### Ringkasan dan beban terhadap omzet Pridata

| | (a) A + Mitra | (b) B + Mitra | (c) Kemitraan 5 th |
|---|---:|---:|---:|
| Total biaya Pridata Tahun 1 | **Rp 116.550.000** | Rp 126.833.333 | Rp 193.925.000 |
| — % omzet Rp 2 miliar | 5,8% | 6,3% | 9,7% |
| — % laba bersih Rp 60–100 juta (asumsi) | 117–194% | 127–211% | 194–323% |
| Total biaya Pridata Tahun 2 dan 3, per tahun | **Rp 47.900.000** | Rp 81.833.333 | Rp 71.900.000 |
| — % omzet | 2,4% | 4,1% | 3,6% |
| — % laba bersih (asumsi) | 48–80% | 82–136% | 72–120% |
| — per bulan | Rp 3.991.667 | **Rp 6.819.444** | Rp 5.991.667 |
| Total biaya Pridata 3 tahun | **Rp 212.350.000** | Rp 290.500.000 | Rp 337.725.000 |
| Dibayar ke Ato-team 3 tahun | Rp 156.250.000 | Rp 290.500.000 | Rp 281.625.000 |
| Payback (nilai tahunan Rp 14.650.000) | ±14,5 th | ±19,8 th | ±23,1 th |
| Kepemilikan di akhir Tahun 3 | Lisensi perpetual | Tidak ada | Lisensi perpetual |
| Komitmen minimum | Tidak ada (K4 dicabut) | 3 tahun | 5 tahun |

**Uji yang diminta Ace: apakah Opsi B + potongan bisa dibayar pada skala ini, per bulan.** Jawabannya **tidak**. Rp 6.819.444 per bulan adalah 4,1% dari omzet bulanan, dan sama dengan atau lebih besar dari **seluruh laba bersih bulanan** (Rp 5–8,3 juta) pada marjin 3–5%. Opsi B juga **lebih mahal di semua horizon** daripada Opsi A yang dipotong. Itu konsisten dengan aturan ATO-2 §3.4: pembeli kecil dijawab dengan struktur yang lebih ringan atau paket ruang lingkup lebih kecil, bukan potongan tambahan. Opsi B tidak melakukannya.

---

## 3. Rekomendasi: (a), dan kenapa (b) serta (c) kalah

**Rekomendasi: Model (a), lewat Program Mitra Riset.** Ia sekaligus menjadi bentuk nyata "kemitraan jangka panjang" (c) yang boleh terbit di daftar harga, karena Program Mitra Riset sudah menukar potongan dengan kewajiban timbal balik, tanpa perlu Opsi C.

- **(b) kalah.** Lebih mahal Rp 78.150.000 selama 3 tahun (Rp 290.500.000 vs Rp 212.350.000), lebih mahal juga di Tahun 1 (Rp 126.833.333 vs Rp 116.550.000), dan Pridata tidak memiliki apa pun di akhir. Alasan "kas Tahun 1 lebih ringan" tidak berlaku di sini: setelah potongan, Opsi A malah lebih ringan di Tahun 1.
- **(c) kalah.** Membayar Rp 125.375.000 lebih banyak selama 3 tahun. Mengunci Pridata ke ASC **Standar 5 tahun** (Rp 244.625.000) padahal SLA Dasar cukup, dan pada omzet Rp 2 miliar komitmen itu sulit ditegakkan. ATO-2 §4 sudah menilai risiko wanprestasinya lebih besar daripada nilainya. Skala Pridata membuat penilaian itu makin kuat. Ia juga tidak terbit di daftar harga.
- **(a) menang** karena biayanya terendah di setiap horizon, recurring-nya terendah (Rp 47.900.000/tahun), Pridata memiliki lisensinya, dan tidak ada komitmen yang perlu ditegakkan lewat pengadilan.

**Batas rekomendasi ini, dinyatakan terbuka.** (a) adalah struktur *paling murah*, bukan struktur yang *terbukti terjangkau*. Lihat §1 dan §8.

---

## 4. Termin pembayaran

Terikat ke milestone yang bisa diverifikasi (bukan tanggal kalender), memakai **empat termin NTB-PL-2026-09 §6** dan potongan dikreditkan proporsional di tiap termin. Persentase potongan tidak ditulis di dokumen yang keluar.

| Termin | Milestone (bukti verifikasinya) | Harga list | Potongan Mitra Riset | **Dibayar** |
|---|---|---:|---:|---:|
| 1 | Tanda tangan kontrak | Rp 52.500.000 | −Rp 26.250.000 | **Rp 26.250.000** |
| 2 | Environment siap + data master dimigrasi dan diverifikasi (kriteria data master tertulis terpenuhi) | Rp 43.750.000 | −Rp 21.875.000 | **Rp 21.875.000** |
| 3 | Berita acara UAT diterima | Rp 43.750.000 | −Rp 21.875.000 | **Rp 21.875.000** |
| 4 | 30 hari setelah go-live tanpa insiden kritis | Rp 35.000.000 | −Rp 17.500.000 | **Rp 17.500.000** |
| | **Jumlah** | **Rp 175.000.000** | **−Rp 87.500.000** | **Rp 87.500.000** |

**ASC:** Rp 27.500.000, ditagih **tahunan di muka**, jatuh pada **awal bulan ke-7 setelah go-live** (garansi diperpanjang jadi 6 bulan, C1). Kuartalan +5%.

**⚠ Koreksi terhadap ATO-2 §6.8 dan §6.4.** ATO-2 menyusun termin Pridata 40/30/30 dengan asumsi "sistem sudah terpasang dan berjalan, milestone teknis sudah lewat", dan menghitung VPS 12 bulan penuh di Tahun 1. **Asumsi itu tidak punya sumber** di plan ATO-1, di brief ATO-5 (yang memuat migrasi, pelatihan, dan onboarding setelah tanda tangan), maupun di ATO-3 (Pridata masih "calon pembeli"). Saya memakai milestone implementasi standar dan VPS 9 bulan. **Bila sistem memang sudah hidup di Pridata, §4 dan angka VPS Tahun 1 perlu diubah, dan Ace perlu memastikannya.**

**Cara termin menegakkan timbal balik.** Termin tidak diikat ke K1/K3 (seperti usulan lama ATO-2 §6.8) karena empat termin itu terbit di daftar harga dan tidak boleh ditambah. Penegakannya lewat **clawback per butir** (§6).

---

## 5. Penempatan Fase 2

Fase 2 (modul penerimaan barang tahap lanjut) **tidak masuk harga dasar, tidak dijanjikan gratis, dan tidak didiskon**, karena kontribusi Pridata (K5) sudah dihargai di dalam potongan sistem. Memberi diskon lagi berarti membayar K5 dua kali (ATO-2 §6.7).

| Aspek | Ketentuan |
|---|---|
| **Harga** | Terpisah, dijual pada harga list penuh: `orang-hari terkalibrasi × Rp 1.750.000`, minimum 5 orang-hari (ATO-2 §1.2). **Angka rupiah tidak dicantumkan di sini** sesuai batasan Ace di ATO-4 dan Daftar Harga §3 (belum diterbitkan). |
| **Effort (Bayu, ATO-3 §4)** | Paket inti (F2-6, F2-1, F2-2, F2-3, F2-4, F2-5): **27–48 orang-hari**. Plus barcode (F2-9): 35–62. Semua item termasuk UOM dan batch: 58–101 — **tidak dianjurkan dijual satu fase** |
| **Kriteria penerimaan (terpisah)** | Diukur di data produksi, tidak ada janji "human error hilang": **T3** `supplierId` non-null 100% pada penerimaan baru · **T4** 100% pengubahan record stok punya entri audit · **T5** nol penerimaan terposting sebagian dan nol dokumen ganda per surat jalan · **T1** selisih terhadap PO terdeteksi pada hari penerimaan. **T2** (≥70% baris lewat scan) hanya jadi kriteria bila F2-9 masuk dan survei barcode mendukung. **T6** (selisih opname turun) **tidak dijanjikan**, hanya dilaporkan. |
| **Jadwal (terpisah)** | Ditetapkan setelah spesifikasi disetujui. Kerja bersih paket inti ±3–5 minggu dengan 2 orang penuh waktu (27–48 od ÷ 2 orang ÷ 5 hari; turunan saya, bukan estimasi Bayu), **ditambah** migrasi data F2-1, UAT, pelatihan, dan 20 sesi uji coba K5. |
| **Termin usulan (belum terbit)** | Mengikuti pola daftar harga, terikat milestone: persetujuan spesifikasi · serah ke lingkungan uji dan UAT dimulai · berita acara UAT · 30 hari setelah go-live tanpa insiden kritis. Persentasenya ditetapkan bersama harga Fase 2. |
| **Bergantung pada jawaban Pridata** | **Q1 (PO ke supplier ada atau tidak) mengubah rancangan.** Bila tidak ada PO, F2-2 gugur (hemat 6–10 od) dan pencocokan menjadi 2 arah. Q2–Q7 di ATO-3 §8 juga perlu dijawab. **Harga Fase 2 tidak bisa final sebelum itu.** |

**Konsekuensi jadwal yang harus dinyatakan:** rekomendasi Bayu, bila anggaran memaksa, adalah mempertahankan F2-6 → F2-1 → F2-3 → F2-4, dan **jangan menjalankan F2-4/F2-5 tanpa F2-1**. Menjual blind count tanpa barcode menjual kemunduran yang terasa (ATO-3 §6).

---

## 6. Syarat kemitraan 2 arah

### 6.1 Kewajiban Pridata — dan akibatnya bila tidak dipenuhi

Nilai tiap butir dari ATO-2 §6.5 (keyakinan Rendah–Sedang, asumsi A10). **Dokumen ini internal.** Nilai per butir tidak masuk penawaran (lihat §8).

| # | Klausul (bisa masuk kontrak) | Nilai | **Bila tidak dipenuhi** |
|---|---|---:|---|
| **K1** | **Studi kasus & referensi penjualan NTB.** Ato-team boleh menyebut nama CV Pridata Jaya dan memakainya sebagai referensi; naskah studi kasus disetujui tertulis oleh Pridata sebelum terbit (angka disamarkan sesuai K2). Pridata menyediakan 1 narahubung, maks 4 kontak calon pembeli per tahun. | Rp 28.000.000 | Pridata menolak atau mencabut izin tanpa alasan sah selama 36 bulan pertama: **clawback Rp 28.000.000 pro rata sisa bulan dari 36**, ditagih dalam 30 hari sejak pemberitahuan tertulis. Bila ditolak sebelum tanda tangan: konsesi C1–C3 (Rp 26.575.000) ditarik, harga sistem tetap. |
| **K2** | **Akses data operasional untuk riset, 3 tahun.** Akses baca data transaksi (order, invoice, pergerakan stok, piutang), NDA dua arah, hanya dalam bentuk teragregasi atau teranonimkan, tidak dipindahkan ke pihak ketiga, nama Pridata tidak pernah dipublikasikan. | Rp 43.750.000 | Akses ditarik atau dibatasi sehingga riset tidak mungkin: **clawback Rp 43.750.000 pro rata sisa bulan**, dan Ato-team boleh mengakhiri status mitra. **Bila ditolak sebelum tanda tangan: Program batal**, bukan negosiasi harga. Kembali ke list dikurangi maks 10% (Rp 157.500.000) bila Ato-team setuju melanjutkan. |
| **K3** | **Testimoni + lokasi demo.** Testimoni tertulis dan video dalam 6 bulan sejak tanda tangan. Kunjungan demo maks 6× per tahun, 2 jam, dijadwalkan ≥ 5 hari kerja sebelumnya. | Rp 26.250.000 | Testimoni belum diserahkan 60 hari setelah pemberitahuan tertulis, atau 3 permintaan demo sah berturut-turut ditolak: **clawback Rp 26.250.000 pro rata bagian yang belum dipenuhi**. |
| **K5** | **Co-development Fase 2.** Min 20 sesi uji coba, ±3 jam, 1 operator gudang + 1 supervisor, umpan balik terdokumentasi 5 hari kerja per sesi. | Rp 26.250.000 | Per sesi yang tidak dipenuhi setelah pemberitahuan 10 hari: **Rp 1.312.500 per sesi** (Rp 26.250.000 ÷ 20). Bila Pridata menolak seluruh K5: uji lapangan pindah ke harga Fase 2, di mana ia memang seharusnya berada (ATO-2 §6.6). |
| ~~K4~~ | ~~Komitmen ASC minimum 3 tahun~~ **DICABUT** | ~~Rp 10.312.500~~ | Lihat §6.3. |
| | **Total K1, K2, K3, K5** | **Rp 124.250.000** | |

**Prinsip clawback:** proporsional terhadap nilai butir yang dilanggar, bukan hukuman. Klausul yang melebihi nilai kerugian riil cenderung tidak dapat ditegakkan. **Penasihat hukum wajib meninjau rumusan kontraknya**; dokumen ini menyusun substansi komersial, bukan kontrak.

### 6.2 Kewajiban Ato-team — supaya benar-benar dua arah

| # | Kewajiban Ato-team | Nilai bagi Pridata |
|---|---|---:|
| Potongan | Potongan Mitra Riset atas harga sistem, sebagai baris rupiah terpisah | Rp 87.500.000 |
| **C1** | Garansi cacat diperpanjang **3 → 6 bulan**; ASC mulai bulan ke-7 | Rp 6.875.000 |
| **C2** | **Bank 10 orang-hari** permintaan perubahan, berlaku 3 tahun, tidak dapat dialihkan atau diuangkan, hangus bila tidak terpakai | Rp 17.500.000 |
| **C3** | ASC **terkunci tanpa indeksasi** selama 3 tahun | Rp 2.200.000 |
| Kerahasiaan | NDA dua arah; nama dan angka Pridata tidak dipublikasikan tanpa persetujuan tertulis naskahnya; data riset hanya dalam bentuk teragregasi | — |
| Program | Harga list NTB-PL-2026-09 tetap satu-satunya angka yang boleh disebut publik oleh kedua pihak | — |
| Transparansi biaya | Spesifikasi minimum VPS dan biaya perkiraan dinyatakan tertulis **sebelum tanda tangan** | — |
| | **Total diberikan** | **Rp 114.075.000** |

### 6.3 Neraca setelah K4 dicabut

| | Nilai |
|---|---:|
| Total konsiderasi diterima (K1, K2, K3, K5) | Rp 124.250.000 |
| Total diberikan (potongan + C1–C3) | Rp 114.075.000 |
| **Cadangan negosiasi (di pihak Ato-team)** | **Rp 10.175.000** |

Ini bukan kelebihan yang harus dihabiskan. Cadangannya turun dari Rp 20.487.500 (ATO-2 §6.5) karena K4 dicabut, dan **ia menyerap** galat estimasi nilai konsiderasi (keyakinan Rendah–Sedang). Alasan pencabutan K4: meminta komitmen 3 tahun senilai Rp 47.900.000/tahun (2,4% omzet, 48–80% laba bersih) pada perusahaan sekecil ini menghasilkan wanprestasi, bukan pendapatan (ATO-2 A12).

**Akibat pencabutan yang harus diterima:** Pridata **boleh berhenti ASC kapan saja setelah masa ASC berjalan tahun berjalan berakhir**, dan sistem tetap jalan di VPS-nya tanpa patch dan dukungan. ASC Pridata sudah rugi Rp 1.000.000/tahun selama satu pelanggan (ATO-2 §2.4). Kehilangannya tidak membuat Ato-team lebih miskin, tetapi hilang pula referensi hidup yang menjadi dasar potongan. K1–K3 tetap mengikat dan tidak bergantung pada ASC.

---

## 7. Ring-fencing diskon

Sembilan klausul ATO-2 §6.9, status per tanggal ini. Klausul-klausul ini **wajib** masuk kontrak Pridata.

| # | Klausul | Status |
|---|---|---|
| 1 | Harga list terbit lebih dulu dan bertanggal | ✅ **Selesai.** NTB-PL-2026-09, 29 September 2026 |
| 2 | Potongan sebagai baris rupiah terpisah, tidak pernah harga tunggal | Masuk kontrak dan invoice. **Persentase tidak pernah ditulis** di dokumen yang keluar |
| 3 | Baris ASC menampilkan `Potongan Program Mitra Riset — Rp 0` secara eksplisit | Masuk invoice ASC |
| 4 | Kerahasiaan harga dua arah; hanya harga list yang boleh disebut publik | Masuk kontrak |
| 5 | Program tertutup: 1 mitra per kategori per pasar, berakhir **31 Desember 2027** | Dinyatakan di kontrak Pridata sendiri |
| 6 | Non-precedent: bukan acuan untuk perpanjangan, perluasan, Fase 2, pembeli lain, maupun afiliasi/satu grup | Masuk kontrak |
| 7 | Varian tanpa hosting = perubahan ruang lingkup, bukan diskon | Masuk kontrak |
| 8 | Perpanjangan setelah Tahun 3: list berlaku dikurangi **maks 10%**. C1–C3 tidak diperpanjang, bank C2 hangus | Masuk kontrak |
| 9 | Clawback pro rata untuk K1, K2, K3, K5, berlaku selama masa kewajiban masing-masing (§6.1). ATO-2 menulis 12 bulan; diperluas ke 36 bulan untuk K1 dan K2 karena keduanya berjalan 3 tahun | Masuk kontrak |

**Tambahan dari analisis ini:** pada skala Rp 2 miliar/tahun, risiko kebocoran harga justru **rendah**, karena Pridata tidak mungkin menjadi acuan distributor besar. Yang lebih berbahaya adalah pembeli NTB berikutnya yang **lebih besar** membaca harga Pridata sebagai harga pasar. Klausul 4 dan 6 adalah yang paling perlu ditegakkan.

---

## 8. Skenario negosiasi

### Penolakan 1 (hampir pasti): *"Sistem ini tidak menyelesaikan human error kami."*

**Jawaban** (berdiri di atas ATO-3, bukan di atas diskon):

> "Benar untuk kondisi sekarang, dan kami tidak akan membantahnya. Tidak ada software yang menghilangkan salah hitung manusia. Yang bisa dilakukan software hanya tiga hal: mengurangi peluang salah input, menangkap salah lebih awal, dan membuat salah terlacak. **Sistem ini sudah kuat di yang ketiga**: setiap perubahan stok punya sebab yang bisa ditelusuri, ada jejak audit, dan ada stock opname. **Yang belum ada adalah dua yang pertama** di alur barang masuk, yaitu angka ekspektasi dari PO atau surat jalan yang dibandingkan dengan hitungan fisik. Itu **Fase 2**, dan kami tulis terpisah, dengan harga terpisah dan kriteria penerimaan yang bisa Anda ukur. Anda juga menjadi mitra ujinya. Fase 2 pun tidak menghilangkan salah hitung; ia memindahkan waktu ketahuannya dari saat opname ke saat barang masih di depan gudang dan sopir supplier masih ada."

Bila mereka menuntut harga dasar turun karena celah ini: **tidak ada respons harga.** Jawabannya jadwal dan harga Fase 2 (ATO-2 §6.7). Klaim yang dijanjikan hanya T1, T3, T4, T5. **T6 tidak dijanjikan.**

### Penolakan 2: *"Biaya berjalannya terlalu berat untuk usaha sebesar kami."*

Ini penolakan yang **paling mungkin benar** pada skala Rp 2 miliar/tahun (§1). **Jangan dijawab dengan potongan tambahan.**

> "Biaya berjalannya memang nyata: ASC Rp 27.500.000 ditambah server Anda sendiri, sekitar Rp 47.900.000 per tahun (perkiraan server dari kami, bukan harga Ato-team). Kami tidak akan menurunkan harga list, dan kami tidak akan menjanjikan bahwa ini menghemat sebesar itu. Yang kami tawarkan: termin pembayaran diikat ke milestone sehingga pembayaran tersebar sepanjang implementasi, ASC tidak diindeksasi selama tiga tahun, dan Anda **tidak terikat komitmen ASC minimum**."

Bila Pridata tetap merasa tidak sanggup: **menunda adalah jawaban yang sah.** Ato-team tidak menjual di bawah harga yang membuat pembeli menghentikan ASC di Tahun 2. Jangan beralih ke Opsi B karena alasan kas: setelah potongan, ia lebih mahal di Tahun 1 (§2).

### Penolakan 3: *"Kami tidak mau membuka data operasional / dijadikan referensi, tapi tetap minta potongan."*

Diselesaikan dengan **tangga negosiasi** ATO-2 §6.6, tanpa kembali ke Rani:

| Kalau Pridata menolak… | Nilai hilang | Respons harga yang benar |
|---|---:|---|
| **K1** referensi | Rp 28.000.000 | Tarik C1 + C2 + C3 (Rp 26.575.000). Harga sistem **tetap**. Kurang Rp 1.425.000, di dalam cadangan |
| **K2** data riset | Rp 43.750.000 | **Program batal.** Tanpa akses data ini bukan kemitraan riset, hanya potongan biasa. List dikurangi maks 10% = **Rp 157.500.000**. Bukan negosiasi, melainkan keputusan apakah program ada |
| **K3** testimoni & demo | Rp 26.250.000 | Tarik C1 + C2 + C3. Surplus Rp 325.000. Seimbang |
| **K5** co-development | Rp 26.250.000 | Tarik C1 + C2 + C3 **dan** uji lapangan pindah ke harga Fase 2 |

**Aturan penegakan:** potongan adalah harga paket K1, K2, K3, K5 **utuh**, bukan titik awal tawar-menawar.

### Catatan: Pridata pernah melihat SAP B1 / Odoo (Q4 = d)

Jangkar harga di kepala Pridata tinggi, jadi Rp 175.000.000 tidak akan terdengar mahal. **Risikonya ekspektasi ruang lingkup** (multi-mata-uang, manufaktur, konsolidasi, e-faktur, akuntansi penuh). Tabel "tidak termasuk" harus tampil sama menonjol dengan "termasuk". **Tidak ada angka pembanding SAP/Odoo di dokumen ini** karena tidak ada data terverifikasi; jangan dipakai untuk menutupi hasil hitungan §1.

---

## 9. Konsekuensi untuk ATO-5 (penawaran final)

1. **Tidak ada klaim hemat, payback, atau ROI.** Nilai yang dijual: kendali dan keterlacakan. Biaya berjalan ditampilkan **apa adanya dalam rupiah**, termasuk perkiraan VPS milik Pridata.
2. **Opsi A + Program Mitra Riset, tanpa K4.** Opsi B tidak ditawarkan sebagai jalan keluar kas, karena lebih mahal setelah potongan.
3. **Bagian human error di depan**, jujur: sudah kuat di keterlacakan, belum di pencegahan; Fase 2 terpisah.
4. **Fase 2 tanpa angka rupiah**, tanpa janji gratis, dengan target terukur T1, T3, T4, T5 dan syarat jawaban Q1–Q7.
5. **Persentase potongan dan nilai per butir K tidak ditulis.** Nilai per butir (dan cadangan Rp 10.175.000) hanya di dokumen ini.
6. **Gerbang keputusan sebelum kirim:** angka skala Pridata diverifikasi oleh Ace, karena semua uji kemampuan bayar di §1 memakai marjin generik.

---

## 10. Asumsi dan pertanyaan terbuka

| ID | Hal | Status | Bila salah |
|---|---|---|---|
| **A12** | Omzet Pridata ± Rp 2 miliar **per tahun** | Keputusan user di ATO-6 (via Ace). **Semua kesimpulan §1–§3 bergantung padanya** | Bila ternyata per bulan (Rp 24 miliar/tahun): biaya berjalan 0,20% omzet, payback 3,2 tahun, K4 boleh diminta lagi, §1 gugur |
| **M1** | Marjin kotor 10–15%, marjin bersih 3–5% | **Generik, bukan data Pridata** | Uji kemampuan bayar §1 dan §2 bergeser proporsional. Tanya Pridata langsung |
| **S1** | Sistem belum terpasang di Pridata; implementasi 40 od dijalankan setelah tanda tangan | Saya asumsikan; ATO-2 §6.8 mengasumsikan sebaliknya tanpa sumber | Termin §4 dan VPS Tahun 1 berubah |
| **A4** | VPS ± Rp 1.700.000/bulan (Rp 20.400.000/tahun) | Asumsi ATO-2, belum diverifikasi ke penyedia VPS | Total biaya Pridata bergeser; angka di penawaran harus label "perkiraan" |
| **A10** | Nilai K1–K5 | Estimasi, keyakinan Rendah–Sedang | Cadangan Rp 10.175.000 menyerapnya sampai batas itu |
| **F2** | Harga Fase 2 | **Tidak dicantumkan.** Effort Bayu ada; kalibrasi bobot dan persetujuan Ace belum | Lihat §5 |
| **Q1 (ATO-3)** | Pridata memakai PO resmi atau memesan lewat telepon/WhatsApp | **Belum dijawab, paling kritis untuk Fase 2** | F2-2 gugur, pencocokan 2 arah |
| **A3** | Rate biaya internal Rp 950.000/od | Masih asumsi (ATO-2 Q6) | Pada Rp 1.200.000/od, Rp 87.500.000 tinggal Rp 3.500.000 di atas lantai teknis absolut |

**Yang sengaja tidak ada di dokumen ini:** harga Fase 2 dalam rupiah, pembanding harga SAP/Odoo, naskah kontrak, dan penawaran siap kirim (itu [ATO-5](/ATO/issues/ATO-5)).
