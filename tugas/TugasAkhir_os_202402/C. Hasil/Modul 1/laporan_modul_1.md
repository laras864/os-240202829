# 📝 Laporan Tugas Akhir

* **Mata Kuliah**: Sistem Operasi
* **Semester**: Genap / Tahun Ajaran 2024–2025
* **Nama**: `Anindiya Larasati`
* **NIM**: `240202829'
**Modul yang Dikerjakan**:'Modul 1 – System Call dan Instrumentasi Kernel)`

---

## 📌 Deskripsi Singkat Tugas

**Modul 1 – System Call dan Instrumentasi Kernel**:
 Menambahkan dua system call
* getpinfo() — untuk melihat informasi proses-proses yang aktif di sistem.
* getReadCount() — untuk menghitung berapa kali fungsi read() dipanggil sejak sistem boot.
---

## 🛠️ Rincian Implementasi

* menambahkan Struktur pinfo dan Counter readcount, dalam file proc.c dan sysproc.c.
*  menambahkan Nomor System Call Baru, dalam file syscall.h dan syscall.c , user.h dan usys.c.
* mengimplemntasikan fungsi kernel. menambahkan kode dalam file sysproc.c.
* memodifikasi read() untuk Tambah Counter. Di sysfile.c, fungsi sys_read().
* membuat Program Penguji User-Level. dalam File: ptest.c (untuk getpinfo), dan File: rtest.c (untuk getreadcount).

---

## ✅ Uji Fungsionalitas

* `ptest`: Menampilkan informasi proses yang sedang aktif, seperti PID, status, dan penggunaan CPU/memori (sesuai isi struct pinfo).
* `rtest`: Menampilkan jumlah total pemanggilan read() yang telah terjadi sejak sistem boot.
---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. 

### 📍 Output `ptest`:

```
PID     MEM     NAME
1       12288   init
2       16384   sh
3       12288   ptest
```

### 📍 Output `rtest`:

```
Read Count Sebelum: 12
hello
Read Count Setelah: 13
```

---

## ⚠️ Kendala yang Dihadapi

 * Awalnya terjadi error karena salah memanggil pointer: ptable seharusnya menunjuk ke struct proc, bukan struct pinfo.
 * Juga muncul error incomplete type karena belum menyertakan #include "spinlock.h".
 * Perlu hati-hati saat menggunakan argptr() dan pointer di syscall agar data tidak corrupt.

---

## 📚 Referensi

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

