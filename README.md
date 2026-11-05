# Tugas 1: Sistem Keanggotaan Gym FitTrack

## Judul dan Identitas
* **Nama Tugas:** Remedial UTS Praktikum PBO - Tugas 1 (Sistem Keanggotaan Gym FitTrack)
* **Nama Lengkap:** Rahadatul Qudsi
* **NPM:** 250810701100026
* **Praktikum:** Pemrograman Berbasis Objek

## Deskripsi Singkat
Aplikasi ini dikembangkan untuk mendigitalkan sistem pencatatan data keanggotaan gym FitTrack yang sebelumnya manual. Program ini memastikan seluruh data member yang dimasukkan selalu valid melalui penerapan penanganan kesalahan dan prinsip OOP berbasis Java.

## Fitur Utama
1. **Pendataan Member Gym:** Menyimpan informasi nama, nomor telepon, tanggal pendaftaran, dan jenis paket keanggotaan.
2. **Validasi Input Otomatis:** Memastikan nomor telepon diawali angka 0 dan minimal 10 digit, nama tidak boleh kosong, serta jenis paket terdaftar secara valid.
3. **Konstruksi Fleksibel:** Menyediakan pilihan pembuatan akun member secara manual atau otomatis mengaktifkan paket *Basic*.
4. **Perlindungan Data (Data Safety):** Menolak data tidak valid pada perubahan (*setter*) tanpa merusak nilai lama yang sudah ada.

## Konsep OOP yang Diterapkan
| Konsep OOP | Lokasi Penerapan | Alasan Pemilihan |
| :--- | :--- | :--- |
| **Encapsulation** | Class `Member` (Atribut `private`, `getter/setter`) | Menyembunyikan data sensitif dan memastikan semua perubahan data diproses lewat fungsi validasi. |
| **Constructor Overloading** | Class `Member` | Memberikan fleksibilitas pendaftaran member dengan atau tanpa menentukan paket awal. |
| **Constructor Chaining (`this`)** | Class `Member` | Menghindari duplikasi kode pendaftaran (*DRY principle*). |
| **Method Overriding** | Method `toString()` pada class `Member` | Memberikan format cetak data yang jelas dan informatif saat objek diprint. |

## Struktur Project
```text
tugas1-fittrack/
├── .gitignore
├── README.md
└── src/
    ├── Member.java
    └── TesFitTrack.java
```

## Aturan Validasi

| Atribut | Aturan Validasi | Dampak Jika Gagal Validasi |
| :--- | :--- | :--- |
| **Nama** | Tidak boleh `null`, kosong, atau hanya berisi spasi (`!nama.trim().isEmpty()`). | Menampilkan pesan error validasi; data tidak diperbarui. |
| **No. Telepon** | Wajib diawali angka **`0`** dan memiliki panjang **minimal 10 digit**. | Menampilkan pesan error validasi; data lama tetap dipertahankan. |
| **Tanggal Daftar** | Tidak boleh `null` atau kosong. | Menampilkan pesan error validasi; data tidak diperbarui. |
| **Jenis Paket** | Hanya menerima pilihan: **`Basic`**, **`Premium`**, atau **`VIP`** (*case-sensitive*). | Menampilkan pesan error validasi; paket diisi/dipertahankan sesuai status sebelumnya. |

## Cara Menjalankan Program:
## Prasyarat
* **Java Development Kit (JDK)**: Versi 21
* **IDE (Disarankan)**: Visual Studio Code / IntelliJ IDEA / NetBeans

### Melalui Command Line (Terminal)

1. Clone Repository ini:
```bash
git clone [https://github.com/RahadatulQudsi/tugas1-fittrack.git](https://github.com/RahadatulQudsi/tugas1-fittrack.git)
cd tugas1-fittrack

Kompilasi program Java:
javac src/*.java

Jalankan program:
java -cp src TesFitTrack

###  Melalui IntelliJ IDEA / VS Code

1. Buka folder proyek `tugas1-fittrack` pada IDE pilihan Anda.
2. Pastikan SDK proyek telah diatur ke **JDK 21**.
3. Buka file `src/TesFitTrack.java`.
4. Klik tombol **Run** (atau tekan `Shift + F10` di IntelliJ / ikon tombol Play di VS Code).

---

## Contoh Output

```text
=== 1. SKENARIO PEMBUATAN OBJEK & VALIDASI CONSTRUCTOR ===
[Uji Coba Input Salah] Error Validasi: Nomor telepon harus diawali angka 0 dan minimal 10 digit!
Error Validasi: Jenis paket hanya boleh 'Basic', 'Premium', atau 'VIP'!

=== 2. SKENARIO PERUBAHAN DATA LEWAT SETTER (VALIDASI) ===
Nomor Telepon Awal Budi: 085678901234
Mencoba mengubah nomor telepon Budi dengan nilai tidak valid ('123')... Error Validasi: Nomor telepon harus diawali angka 0 dan minimal 10 digit!
Nomor Telepon Budi Setelah Gagal Diubah: 085678901234

=== 3. CETAK DAFTAR MEMBER DENGAN PERULANGAN FOR & TOSTRING() ===
Member ke-1: Member FitTrack [Nama: 'Andi Wijaya', No. Telepon: '081234567890', Tanggal Daftar: '10-10-2026', Jenis Paket: 'Premium']
Member ke-2: Member FitTrack [Nama: 'Budi Santoso', No. Telepon: '085678901234', Tanggal Daftar: '12-10-2026', Jenis Paket: 'VIP']
Member ke-3: Member FitTrack [Nama: 'Citra Dewi', No. Telepon: '089012345678', Tanggal Daftar: '14-10-2026', Jenis Paket: 'Basic']
Member ke-4: Member FitTrack [Nama: 'Eko Prasetyo', No. Telepon: 'null', Tanggal Daftar: '15-10-2026', Jenis Paket: 'null']
```