# 📝 Laporan Tugas Akhir

* **Mata Kuliah**: Sistem Operasi
* **Semester**: Genap / Tahun Ajaran 2024–2025
* **Nama**: Anindiya Larasati
* **NIM**: 240202829
* **Modul yang Dikerjakan**:
Modul 4 – Subsistem Kernel Alternatif (xv6-public)

---

## 📌 Deskripsi Singkat Tugas

Modul 4 – Subsistem Kernel Alternatif (xv6-public)
Menambahkan dua fitur ke sistem operasi xv6, yaitu:

* chmod(path, mode) syscall untuk mengatur mode file (read-only atau read-write)
* Driver pseudo-device /dev/random yang menghasilkan byte acak saat dibaca
---

## 🛠️ Rincian Implementasi

* Tambah system call chmod: fungsi sys_chmod di sysfile.c, nomor syscall di syscall.h, deklarasi di user.h, usys.S.
* Tambah field mode di struct inode (fs.h) dan modifikasi writei() untuk cek flag read-only.
* Tambah device /dev/random: entry device di ide.c/sysfile.c, fungsi randomread(), dan register via mknod() di init.c.
* Program uji: chmodtest.c (cek proteksi write), randomtest.c (baca 8 byte pseudo-random).
---

## ✅ Uji Fungsionalitas

Program uji yang digunakan:
* chmodtest: untuk menguji syscall chmod(path, mode)
* randomtest: untuk menguji pembacaan dari /dev/random

---

## 📷 Hasil Uji

Lampirkan hasil uji berupa output terminal.

### 📍 Output `chmodtest`:

```
Write blocked as expected
```

### 📍 Output `randomtest`:

```
114 97 110 100 111 109 116 101
```
---

## ⚠️ Kendala yang Dihadapi

* File /dev/random hilang setelah reboot — diatasi dengan menambahkan mknod di init.c.
* Salah register device major menyebabkan panic saat device diakses.
* Proteksi read-only tidak berfungsi sampai writei() dimodifikasi.
---

## 📚 Referensi

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

