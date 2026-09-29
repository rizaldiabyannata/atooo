# Ringkasan untuk Ditinjau Sebelum Dikirim ke Pridata

**29 September 2026.** ATO-4 dan ATO-5 diselesaikan dari export Paperclip `ato-team` (Rani berhenti di ATO-4 karena *terminal access failure*).

**Dokumen:** [ATO-4 analysis](/ATO/issues/ATO-4#document-analysis) (internal) · [ATO-5 proposal](/ATO/issues/ATO-5#document-proposal) (untuk Pridata).

## Yang harus Anda putuskan sebelum mengirim

1. **Apakah omzet Pridata benar ± Rp 2 miliar per tahun?** Kalau ya, penawaran ini tidak bisa dibenarkan dengan penghematan: nilai yang bisa dihitung Rp 14.650.000/tahun vs biaya berjalan ± Rp 47.900.000/tahun (payback ±14,5 tahun). Struktur termurah tetap Opsi A + Program Mitra Riset (Tahun 1 Rp 116.550.000 termasuk server Pridata). Penawaran ditulis tanpa klaim hemat dan menampilkan biaya berjalan apa adanya. Sarankan Ace memverifikasi omzet, marjin, dan kas Pridata sebelum kirim.
2. **Apakah sistem sudah terpasang di Pridata?** ATO-2 §6.8 mengasumsikannya tanpa sumber; ATO-5 memakai implementasi standar 40 orang-hari setelah tanda tangan. Kalau sudah terpasang, termin dan biaya server Tahun 1 berubah.
3. **Fase 2 tanpa harga di penawaran** (aturan template dan batasan Ace). Effort Bayu: paket inti 27–48 orang-hari. Menurut formula ATO-2 (× Rp 1.750.000) itu ± Rp 47–84 juta. Belum divalidasi kalibrasinya, sehingga tidak dicantumkan.

## Perubahan dari rencana sebelumnya

- **K4 (komitmen ASC minimum 3 tahun) dicabut** karena skala Rp 2 miliar/tahun. Cadangan negosiasi turun Rp 20.487.500 → Rp 10.175.000.
- Persentase potongan tidak ditulis di penawaran (aturan template A.3). Potongan tampil sebagai baris **−Rp 87.500.000**, potongan ASC **Rp 0**.
- **Penambahan di luar template yang perlu persetujuan tertulis (aturan A.6):** §1A (bagian human error, diletakkan di depan sesuai brief ATO-5), konsesi C1–C3 (garansi 6 bulan, bank 10 orang-hari, ASC terkunci 3 tahun), §3.3 kewajiban timbal balik, §3.5 biaya berjalan.

## Yang harus diisi sebelum dikirim

`{{NOMOR_PENAWARAN}}`, `{{TANGGAL_PENAWARAN}}`, `{{JUMLAH_GUDANG}}`, `{{JUMLAH_PENGGUNA}}`. Lampirkan NTB-PL-2026-09 utuh sebagai Lampiran 2 dan susun Lampiran 3 (nilai K1–K3, K5; kriteria data master; spesifikasi server). Kontrak perlu ditinjau penasihat hukum, terutama klausul clawback.

## Temuan ATO-3 yang sebaiknya diperbaiki sebelum go-live

Pengubahan record stok tidak tercatat di audit, penulisan audit log bersifat best-effort di luar transaksi, dan kegagalan parse dapat menyembunyikan penerimaan dari riwayat (ATO-3 §10). Ketiganya cacat pada produk yang dijual, bukan hanya Fase 2. §1A menyebut yang pertama secara terbuka.
