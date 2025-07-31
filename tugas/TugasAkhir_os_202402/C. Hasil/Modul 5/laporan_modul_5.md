# 📝 Laporan Tugas Akhir

* **Mata Kuliah**: Sistem Operasi
* **Semester**: Genap / Tahun Ajaran 2024–2025
* **Nama**: Anindiya Larasati
* **NIM**: 240202829
* **Modul yang Dikerjakan**:
Modul 5 – Audit dan Keamanan Sistem (xv6-public)

---

## 📌 Deskripsi Singkat Tugas

* **Modul 5 – Audit dan Keamanan Sistem (xv6-public)**:
 Mengimplementasikan fitur audit log dan keamanan akses pada xv6, termasuk pencatatan aktivitas system call dan validasi akses berdasarkan PID.
---

## 🛠️ Rincian Implementasi

* Menambahkan struktur struct audit_entry untuk menyimpan log setiap syscall (audit.h)
* Membuat array global audit_log[MAX_AUDIT] di audit.c sebagai buffer log melingkar
* Menyisipkan logging ke semua entri syscall di syscall() (dalam trap.c)
* Menambahkan syscall baru get_audit_log() di sysproc.c, usys.S, syscall.c, dan syscall.h
* Syscall get_audit_log() hanya dapat dipanggil oleh proses tertentu (misal PID 1 atau audit user program)
* Membuat program pengguna audit.c untuk menampilkan isi log ke terminal
---

## ✅ Uji Fungsionalitas

Program uji yang digunakan:

* audit: Untuk mencetak semua log syscall yang telah terekam oleh kernel, termasuk informasi PID, nomor SYSCALL, dan TICK saat syscall terjadi.

---

## 📷 Hasil Uji

Hasil uji berupa screenshot atau output terminal. 

### 📍 Output audit (dijalankan oleh PID 1):

```
=== Audit Log ===
[0] PID=1 SYSCALL 7 TICK=4
[1] PID=1 SYSCALL 15 TICK=4
[2] PID=1 SYSCALL=17 TICK=4
[3] PID=1 SYSCALL 15 TICK=5
[4] PID=1 SYSCALL 10 TICK=6
[5] PID=1 SYSCALL 10 TICK=6
[6] PID=1 SYSCALL=16 TICK=6
[7] PID=1 SYSCALL=16 TICK=6
[8] PID=1 SYSCALL=16 TICK=6
[9] PID=1 SYSCALL 16 TICK=6
[10] PID=1 SYSCALL-16 TICK=6
[11] PID=1 SYSCALL=16 TICK=6
[12] PID=1 SYSCALL=16 TICK=6
[13] PID=1 SYSCALL=16 TICK=6
[14] PID=1 SYSCALL=16 TICK=6
[15] PID=1 SYSCALL=16 TICK=6
[16] PID=1 SYSCALL=16 TICK=6
[17] PID=1 SYSCALL=16 TICK=6
[18] PID=1 SYSCALL=16 TICK=6
[19] PID=1 SYSCALL=16 TICK=6
[20] PID=1 SYSCALL=16 TICK=6
[21] PID=1 SYSCALL=16 TICK=6
[22] PID=1 SYSCALL=16 TICK=6
[23] PID=1 SYSCALL-16 TICK=6
[24] PID=1 SYSCALL=16 TICK=6
[25] PID=1 SYSCALL=16 TICK=6
[26] PID=1 SYSCALL=16 TICK=6
[27] PID=1 SYSCALL=7 TICK=6
[28] PID=1 SYSCALL 28 TICK=7
```

### 📍 Output audit (jika dijalankan oleh selain PID 1):

```
Access denied or error
```

---

## ⚠️ Kendala yang Dihadapi

* Validasi awal get_audit_log() hanya mengizinkan PID 1, sehingga pengujian terbatas — solusinya validasi akses sementara dinonaktifkan.
* Penggunaan argptr() harus tepat agar tidak terjadi page fault saat memmove() dipanggil di kernel.

---

## 📚 Referensi

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

