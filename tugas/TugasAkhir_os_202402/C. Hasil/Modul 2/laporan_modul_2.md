# 📝 Laporan Tugas Akhir

* **Mata Kuliah**: Sistem Operasi
* **Semester**: Genap / Tahun Ajaran 2024–2025
* **Nama**: Anindiya Larasati
* **NIM**: 240202829
* **Modul yang Dikerjakan**:
 Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive
---

## 📌 Deskripsi Singkat Tugas

* **Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive**:
  Pada sistem operasi xv6, algoritma penjadwalan default (Round Robin) diubah menjadi Non-Preemptive Priority Scheduling. Proses dengan prioritas lebih tinggi (angka lebih kecil) dijalankan lebih dulu dan terus berjalan hingga selesai atau statusnya berubah.
---

## 🛠️ Rincian Implementasi

* Menambahkan field priority pada setiap proses.
* Menambahkan syscall set_priority(int) untuk mengatur prioritas proses.
* Memodifikasi scheduler agar selalu menjalankan proses RUNNABLE dengan prioritas tertinggi.

---

### Contoh untuk Modul 1:

* Menambahkan dua system call baru di file `sysproc.c` dan `syscall.c`
* Mengedit `user.h`, `usys.S`, dan `syscall.h` untuk mendaftarkan syscall
* Menambahkan struktur `struct pinfo` di `proc.h`
* Menambahkan counter `readcount` di kernel
* Membuat dua program uji: `ptest.c` dan `rtest.c`
---

## ✅ Uji Fungsionalitas

Program uji yang digunakan:
- `ptest`: untuk menguji urutan eksekusi proses berdasarkan prioritas

---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. Contoh:

### 📍 Contoh Output `ptest`:

```
Child 2 selesai
Child 1 selesai
Parent selesai

---

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Muncul error proc undeclared karena masih memakai variabel global proc, seharusnya menggunakan c->proc di dalam fungsi scheduler().
* Error p undeclared saat menulis c->proc = p; karena p belum dideklarasikan.
* Urutan deklarasi pointer p yang salah (dideklarasikan setelah loop) menyebabkan error saat kompilasi.
* Solusinya: pindahkan deklarasi struct proc *p; ke bagian atas sebelum digunakan.
---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

