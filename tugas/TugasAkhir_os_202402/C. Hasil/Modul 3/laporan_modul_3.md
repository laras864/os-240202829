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

Lampirkan hasil uji berupa output terminal.

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

**Kendala Implementasi Copy-on-Write (CoW)**:
- Terjadi page fault berulang dan panic saat proses anak mencoba menulis ke memori yang seharusnya disalin → penyebabnya adalah handler page fault belum menangani penyalinan halaman read-only dengan benar.
- Lupa mengatur flag PTE_W saat mengalokasikan salinan halaman baru setelah copy-on-write, sehingga halaman tetap read-only dan kembali memicu fault.
- Reference count (ref_count[]) tidak ter-decrement dengan benar pada saat exit() → menyebabkan kebocoran memori.
- Beberapa halaman kernel tidak boleh dibagi (seperti stack) namun ikut dimap secara CoW → menyebabkan error saat write.

**Kendala Implementasi Shared Memory**:
- Terjadi panic trap 14 saat proses mengakses shared memory → ternyata alamat virtual yang digunakan tidak konsisten atau sudah digunakan proses sebelumnya.
- Error multiple definition of 'shmtab' karena shmtab dideklarasikan di shm.h dan vm.c → seharusnya hanya satu deklarasi extern di header.
- Shared memory tidak termapping ulang dengan benar di proses anak setelah fork() → menyebabkan akses ke NULL atau unmapped address.
- Refcount shared memory tidak turun ke 0 saat semua proses selesai → karena shmrelease() tidak dipanggil secara eksplisit.

---

## 📚 Referensi

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

