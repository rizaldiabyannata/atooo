# Harga dengan Ruang Negosiasi untuk CV Pridata Jaya

**Tanggal:** 3 Oktober 2026 · **Dokumen internal, jangan dikirim ke Pridata.** Menggantikan angka harga di `keputusan-pemilik.md` §8. Debat lengkap: `debat-negosiasi/putaran-1.md` dan `putaran-2.md`.

## 1. Masalah

Proposal v3 menulis **Rp 30 jt + Rp 750 rb/bln** sebagai harga Mitra. Angka itu sudah sama dengan batas bawah kita, padahal Pridata pasti menawar. Ada dua akibatnya:

- **Kalau kita bertahan,** Pridata merasa tidak didengar.
- **Kalau kita turun,** kas per hari kerja jatuh di bawah Rp 452 rb, kurang dari separuh biaya internal.

Label "Rp 60 jt, potongan 50%" juga dinilai keliru oleh keempat agen, termasuk agen yang memerankan pemilik Pridata ("diskon toko baju", "kalau bisa 50%, pasti bisa 60%").

## 2. Empat perspektif

| Agen | Putaran 1 | Putaran 2 (akhir) |
|---|---|---|
| **CFO Ato-team** | Pembuka Rp 40 jt. Lantai Rp 34,5 jt (12 poin) / Rp 30 jt (6 poin) | Pembuka **Rp 38 / 32 jt** (2 paket). Lantai **Rp 34 jt (12 poin) / Rp 30 jt (6 poin)**. Escrow diterima. T3 ≤ Rp 10 jt dengan batas waktu |
| **Pemilik Pridata** | Rp 35 jt masih dipercaya; Rp 40 jt mulai dibanding Odoo; ≥ Rp 45 jt terasa digelembungkan. Tanda tangan di Rp 27,5–30 jt | Pembuka paling jujur: **Rp 30 jt + kontribusi modul yang dibayar hanya bila lulus**. Tanda tangan di **maks Rp 35 jt** (12 poin), dukungan Rp 750 rb dikunci 3 th, garansi 4 bln, escrow wajib. TCO 3 th ≤ ±Rp 57 jt |
| **Negosiator** | Paket Lengkap Rp 38 jt / Inti Rp 32 jt, potongan dirinci | Pembuka **Rp 36 jt** (Rp 24 jt + kontribusi modul Rp 12 jt). Lantai Rp 31,5 jt (8 poin) / Rp 30 jt (6 poin); 12 poin hanya bila ≥ Rp 34,5 jt |
| **Analis pasar** | Pembuka Rp 40 jt (lisensi + kontribusi modul Rp 10 jt). Lantai Rp 30 jt | Pembuka **Rp 38 / 33,5 jt** (paket + kontribusi). Lantai **Rp 34,5 / 30 jt**. Potongan dirinci tidak lolos uji kewajaran |

### Yang disepakati keempatnya

1. **Label "harga standar Rp 60 jt, potongan 50%" dibuang.** Harga standar dukungan Rp 1,5 jt juga dibuang. Tabel per fitur tetap ditampilkan sebagai *nilai lisensi*, bukan harga yang dicoret.
2. **Ruang tawar diambil dari komponen yang nyata, bukan dari angka yang dinaikkan.** Ada dua alatnya:
   - **Kontribusi Modul Penerimaan Barang** yang hanya dibayar bila modul lulus. Ini satu-satunya angka di atas Rp 35 jt yang tidak terasa digelembungkan bagi pembeli.
   - **Dua paket** (6 poin / 12 poin). Bila harga turun, isi ikut turun.
3. **12 poin penyesuaian tidak pernah dijual di bawah ±Rp 34 jt.** Pada Rp 30 jt, isinya 6 poin.
4. **Dukungan: lantai Rp 750 rb/bln.** Pembeli sendiri melepas tuntutan Rp 600 rb.
5. **Escrow kode sumber diberikan sejak awal,** bukan sebagai alat tukar. Escrow menjawab pertanyaan "kalau kalian bubar?".
6. **Termin 1 ≥ Rp 10 jt.** VPS dibeli dari termin ini.
7. **Termin 3 terikat hasil dan diberi batas waktu.** Keterlambatan karena Pridata tidak membatalkan pembayaran.
8. **Manfaat Rp 14,65 jt/th terlalu optimistis.** Klaim "dukungan lebih kecil daripada manfaat" dihapus. Pembenaran utama adalah selisih barang masuk yang diukur dalam rupiah saat trial.

### Yang diputuskan CEO dari titik yang masih berbeda

| Titik | Pilihan | Alasan |
|---|---|---|
| Angka pembuka | **Paket Lengkap Rp 37 jt** (di antara Rp 36 negosiator dan Rp 38 CFO/analis) | TCO 3 th pembuka ±Rp 64,5 jt, masih di bawah batas pergi pembeli (Rp 60–65 jt) dan di bawah Odoo (Rp 70–121 jt) |
| Letak kenaikan | Kontribusi modul **Rp 7,5 jt** di T3; sisanya di T1/T2 | Menjawab keberatan CFO bahwa kenaikan tidak boleh seluruhnya menumpuk di termin bersyarat |
| Batas waktu T3 | **6 bulan setelah go-live** (pembeli 4, analis 6, CFO/negosiator ±8 bln) | Fase 2 diperkirakan 27–48 hari kerja. Empat bulan tidak realistis; delapan bulan membuat pembeli menunggu terlalu lama |
| Garansi | **3 bln sistem + 3 bln khusus Modul Penerimaan Barang sejak lulus.** Kartu terakhir: sistem 4 bln | Usulan analis & negosiator. Risiko produk baru memang ada di modul itu |
| Prabayar dukungan | **11 × tarif bulanan** (bayar 11, dapat 12) | CFO: prabayar 10× membuat dukungan 21% di bawah biaya |

## 3. Struktur penawaran (yang ditulis di proposal)

| Komponen | Paket Inti | Paket Lengkap |
|---|---:|---:|
| **Sistem siap pakai:** lisensi selamanya 47 fitur, implementasi, pelatihan, server 24 bulan, titipan kode sumber, **6 poin** penyesuaian | Rp 25.000.000 | Rp 25.000.000 |
| **Tambahan 6 poin** penyesuaian (jadi 12 poin) | — | Rp 4.500.000 |
| **Kontribusi Modul Penerimaan Barang**, dibayar **hanya bila** keempat target tercapai | Rp 7.500.000 | Rp 7.500.000 |
| **Total** | **Rp 32.500.000** | **Rp 37.000.000** |
| Dukungan tahunan | Rp 850.000/bln, atau Rp 9.350.000/th di muka | sama |

### Termin

| Termin | Kapan | Inti | Lengkap |
|---|---|---:|---:|
| Trial 30–60 hari | — | Rp 0 | Rp 0 |
| 1 | Deal setelah trial layak; VPS dibeli dari sini | Rp 12.000.000 | Rp 12.000.000 |
| 2 | Go-live (boleh dicicil 2× bulanan) | Rp 13.000.000 | Rp 17.500.000 |
| 3 | Modul lulus T1/T3/T4/T5, paling lambat 6 bln setelah go-live | Rp 7.500.000 | Rp 7.500.000 |

**Aturan T3:**
- Bila modul belum lulus dalam 6 bulan **karena kita**, kontribusi batal dan dukungan tidak ditagih sampai modul lulus.
- Bila terlambat **karena Pridata** (sesi uji tidak dijadwalkan, data tidak diserahkan), T3 jatuh tempo di bulan ke-6.
- Lingkup modul dikunci sesuai bagian 02 proposal. Perubahan dibayar dari poin atau dengan tarif hari kerja.

## 4. Pembuka, target, lantai

| | Pembuka | Target | Lantai (walk-away) |
|---|---|---|---|
| Sistem siap pakai (6 poin) | Rp 25 jt | Rp 25 jt | **Rp 25 jt, tidak ditawar** |
| Tambahan 6 poin | Rp 4,5 jt | Rp 4 jt | Rp 4 jt |
| Kontribusi modul | Rp 7,5 jt | Rp 6 jt | Rp 5 jt |
| **Total Lengkap / Inti** | **Rp 37 / 32,5 jt** | **Rp 35 / 31 jt** | **Rp 34 / 30 jt** |
| Dukungan | Rp 850 rb (Rp 9,35 jt prabayar) | Rp 800 rb (Rp 8,8 jt) | **Rp 750 rb (Rp 8,25 jt)**, kontrak ≥ 24 bln |
| Kunci harga dukungan | 24 bln | 36 bln | 36 bln, lalu naik maks 8%/th |
| Garansi | 3 bln + 3 bln modul | sama | Sistem 4 bln (cacat saja) |
| Termin 1 | Rp 12 jt | Rp 12 jt | **Rp 10 jt** |

**Ruang tawar:**
- Paket Lengkap Rp 37 → 34 jt (8%), dengan potongan per putaran ≤ 3%. Ini jauh di bawah ambang "turun > 20% dalam satu pertemuan" yang merusak kepercayaan pembeli.
- Lewat penurunan isi (Lengkap → Inti): Rp 37 → 30 jt (19%), sebagai pilihan yang jujur dan terlihat.

### Beban Pridata dan kas kita

Asumsi: go-live bulan ke-2, garansi 3 bulan, sehingga dukungan Tahun 1 berjalan 7 bulan dan dibayar bulanan. Tahun 2–3 dibayar di muka 11×. Perpanjangan VPS ±Rp 2,8 jt di Tahun 3.

| Titik | Th1 | Th2 | Th3 | **TCO 3 th** | Kas bersih Ato Th1* |
|---|---:|---:|---:|---:|---:|
| Pembuka Lengkap (37 / 850 rb) | 42,95 | 9,35 | 12,15 | **64,45** | 39,3 |
| Pembuka Inti (32,5 / 850 rb) | 38,45 | 9,35 | 12,15 | **59,95** | 34,8 |
| Target Lengkap (35 / 800 rb) | 40,6 | 8,8 | 11,6 | **61,0** | 36,95 |
| Lantai Lengkap (34 / 750 rb) | 39,25 | 8,25 | 11,05 | **58,55** | 35,6 |
| Lantai Inti (30 / 750 rb) | 35,25 | 8,25 | 11,05 | **54,55** | 31,6 |
| *v3 lama (30 / 750 rb, prabayar 10×)* | *35,25* | *7,5* | *10,3* | *53,05* | *31,6* |

Dalam juta rupiah. *Bila kontribusi modul dibayar. Bila batal karena kita, kurangi Rp 5–7,5 jt.

**Perkiraan titik sepakat:** Paket Lengkap **Rp 34–35 jt** dengan dukungan **Rp 750–800 rb**, atau Paket Inti **Rp 30–31 jt**.
- Titik tanda tangan pembeli (±Rp 57 jt) berada sedikit di bawah lantai Lengkap kita (±Rp 58,5 jt). Selisih ±Rp 1,5 jt ini ditutup di putaran penutup lewat tambahan isi, bukan potongan.
- Bila tidak tertutup, Paket Inti di Rp 30 jt (±Rp 54,5 jt) masih aman bagi kas, karena sama dengan v3.

## 5. Tangga konsesi (Paket Lengkap)

| Putaran | Kita beri | Kita minta |
|---|---|---|
| 1. Setelah trial layak | Kontribusi Rp 7,5 → 6,5 jt (total **Rp 36 jt**) | Dukungan Tahun 2 dibayar di muka + T1 Rp 12 jt |
| 2 | Kontribusi → Rp 6 jt (total **Rp 35 jt**) + kunci harga dukungan 36 bln | Kontrak dukungan 24 bln + jadwal 20 sesi uji + PIC gudang tertulis |
| 3 | Dukungan Rp 850 → 800 rb | Tanda tangan ≤ 14 hari setelah trial dinyatakan layak |
| Penutup (pilih satu) | Tambahan poin Rp 4,5 → 4 jt dan kontribusi → Rp 5 jt (total **Rp 34 jt**), **atau** dukungan → Rp 750 rb, **atau** +1 hari pendampingan di lokasi | Referensi tertutup untuk calon pembeli di luar pasar Pridata |

**Aturan main:**
- Hanya satu konsesi per pertemuan, dan nilainya selalu mengecil (Rp 1 jt → Rp 0,5 jt → …).
- Pridata minta di bawah Rp 34 jt → tawarkan **Paket Inti** (Rp 30–31 jt). Pembeli sendiri berkata ia berhenti menawar bila jawabannya adalah pengurangan isi.
- Pridata minta di bawah Rp 30 jt → tolak dengan sopan dan tawarkan skema sewa-milik (`hasil-debat-harga.md` §3.2).
- Tawar-menawar harga dilakukan **sesudah trial**. Saat itu posisi kita terkuat, karena salah catat barang masuk sudah terukur dalam rupiah.

**Tiga kalimat saat Pridata bilang "terlalu mahal":**
1. "Mahal dibanding apa, Pak: anggaran tahun ini, atau sistem lain yang Bapak lihat?"
2. "Bapak baru membayar setelah trial terbukti, dan Rp 7,5 juta terakhir hanya dibayar kalau salah catat barang masuk benar-benar tertangkap di gudang Bapak."
3. "Kalau angkanya harus turun, ada dua jalan: Paket Inti dengan 6 poin, atau dukungan dibayar setahun di muka. Mana yang lebih cocok?"

## 6. Yang tidak boleh ditawar

- **Kas dan isi paket:**
  - Sistem siap pakai Rp 25 jt.
  - Termin 1 ≥ Rp 10 jt, dibayar saat deal. Ato-team tidak menalangi server.
  - 12 poin di bawah Rp 34 jt.
  - Dukungan efektif di bawah Rp 750 rb/bln.
  - Poin di atas 12, garansi sistem di atas 4 bln.
- **Lingkup dan aturan pakai:**
  - Lingkup Modul Penerimaan Barang dikunci (±35 hari kerja). Perubahan dibayar dari poin atau tarif.
  - Poin hangus 6 bulan dan tidak dialihkan ke dukungan.
- **Hak dan kerahasiaan:**
  - Lisensi non-eksklusif, IP milik Ato-team, tanpa fork.
  - Firewall data. Tidak menyangkal bila ditanya apakah sistem dijual ke pihak lain.
- **Janji dan cara bernegosiasi:**
  - Tidak menjanjikan angka penurunan selisih opname.
  - Tidak memakai potongan persen, "harga akhir", promo, atau tenggat buatan.
  - Testimoni bernama bukan alat tukar (bertentangan dengan keputusan #3).

## 7. Perubahan pada proposal (`proposal-pridata.html`)

1. **Ringkasan atas:** Paket Lengkap Rp 37 jt, dengan catatan Rp 7,5 jt dibayar hanya bila modul lulus. Paket Inti Rp 32,5 jt. Dukungan Rp 850 rb.
2. **Bagian 02:** judul modul diganti, dari "sudah termasuk harga" menjadi "kontribusi dibayar hanya bila berhasil".
3. **Bagian 04:**
   - Penyesuaian 6 atau 12 poin.
   - Garansi 3 bln + 3 bln modul.
   - Dukungan Rp 850 rb, dikunci 24 bln, prabayar 11×.
4. **Bagian 05:**
   - Manfaat dihitung ulang dengan upah ±Rp 20 rb/jam (±Rp 11 jt/th), dipisah antara uang langsung dan waktu kerja.
   - Klaim "dukungan lebih kecil daripada manfaat" dihapus.
   - Tabel "harga standar vs Mitra" diganti tabel dua paket.
   - Tabel per fitur menjadi "nilai lisensi" tanpa kolom 50%.
   - Pembanding Accurate ditulis jujur.
5. **Bagian 06:** termin per paket dan perkiraan 3 tahun per paket.
6. **Bagian 07:**
   - Klausul baru: titipan kode sumber.
   - T3 diberi batas waktu dan aturan "karena siapa".
   - Dukungan dikunci 24 bln.
   - Masa berlaku penawaran diubah: dari "30 hari" menjadi "sampai 30 hari setelah trial dinyatakan layak".

## 8. Yang perlu dijawab pemilik

1. **Status pajak Ato-team (PKP atau bukan).** Pembeli menilai "belum termasuk pajak" tanpa angka sebagai biaya tersembunyi. Proposal memakai placeholder `[status pajak]`.
2. **Pihak penitip kode sumber** (notaris atau pihak ketiga lain) dan biayanya. Belum dicek. Perkiraan dokumen pemasangan ±2 hari kerja, dibuat sekali untuk semua pelanggan.
3. **Risiko yang diterima:**
   - Bila Fase 2 membengkak ke 48 hari kerja dan modul tidak lulus dalam 6 bulan karena kita, kontribusi Rp 5–7,5 jt hilang dan dukungan tertunda.
   - Paket Lengkap lalu efektif Rp 29,5 jt untuk 12 poin, di bawah lantai CFO.
   - Ini harga dari permintaan pembeli yang paling ia pertahankan. Pengendaliannya: lingkup dikunci, dan keterlambatan karena Pridata tidak dihitung.
4. **Harga pekerjaan di luar paket belum diputuskan** (tarif hari kerja, kunjungan lokasi, pelatihan tambahan, migrasi data historis, integrasi, aplikasi mobile, perangkat keras). Atas permintaan pemilik, bagian "Di luar harga" dan semua sebutan tarif Rp 1.750.000 dihapus dari proposal. Proposal kini hanya menyebut pekerjaan di luar lingkup "dibahas terpisah" dan baru dikerjakan setelah disetujui tertulis. Batas "di luar paket" untuk poin penyesuaian tetap tercantum.
