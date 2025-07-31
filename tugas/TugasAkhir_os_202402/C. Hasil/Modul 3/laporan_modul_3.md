# 📝 Laporan Tugas Akhir

* **Mata Kuliah**: Sistem Operasi
* **Semester**: Genap / Tahun Ajaran 2024–2025
* **Nama**: `<Nama Lengkap>`
* **NIM**: `<Nomor Induk Mahasiswa>`
* **Modul yang Dikerjakan**:
 Modul 3 — Manajemen Memori Tingkat Lanjut (xv6-public x86)  

---

## 📌 Deskripsi Singkat Tugas

Modul 3 – Manajemen Memori Tingkat Lanjut (xv6-public x86)
Mengimplementasikan dua fitur utama:
* Copy-on-Write Fork (CoW) untuk efisiensi pemanggilan fork()
* Shared Memory dengan shmget(key) dan shmrelease(key) untuk berbagi memori antar proses
---

## 🛠️ Rincian Implementasi

Tuliskan secara ringkas namun jelas apa yang Anda lakukan:

###  Copy-on-Write Fork

* Modifikasi fork() pakai teknik CoW dengan bit PTE_COW.
* Tambah handler page fault CoW di trap.c, serta incref()/decref() untuk reference count.
* Ubah walkpgdir() dan pastikan exit()/wait() mengelola ref_count dengan benar.

### Shared Memory ala System V

* Tambah syscall shmget(key) dan shmrelease(key) serta tabel shmtab[].
* Shared memory dipetakan dari USERTOP ke bawah dan tetap terhubung setelah fork().
---

## ✅ Uji Fungsionalitas

Program uji yang digunakan:
* cowtest: untuk menguji fork dengan Copy-on-Write
* shmtest: untuk menguji shmget() dan shmrelease()

---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. Contoh:

### 📍 Output `cowtest`:

```
Child sees: Y
Parent sees: X
```

### 📍 Output `shmtest`:

```
Child reads: A
Parent reads: B
```

---

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Salah implementasi `page fault` menyebabkan panic
* Salah memetakan alamat shared memory ke USERTOP
* Proses biasa bisa akses audit log (belum ada validasi PID)

---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

