# 4522210013_RajaWalidain_APBO_Daycare_28-05-2024
Proyek ini adalah sistem manajemen untuk penitipan anak yang mencakup fitur absensi untuk anak-anak, guru, dan staf. Sistem ini juga mencakup manajemen laporan, pembayaran, dan alamat untuk orang tua, anak, staf, dan guru.

## Isi Proyek

- **Entity-Relationship Diagram (ERD)**
- **Use Case Diagram**
- **Class Diagram**
## ERD
## Entity-Relationship Diagram (ERD)

ERD digunakan untuk menggambarkan hubungan antara entitas dalam basis data. Berikut adalah detail entitas dan relasi dalam sistem daycare ini:

### Entitas dan Atribut

1. **OrangTua**
   - `id_orangtua` (PK)
   - `nama`
   - `no_telp`
   - `email`
   - `id_alamat` (FK)

2. **Anak**
   - `id_anak` (PK)
   - `id_orangtua` (FK)
   - `nama`
   - `umur`
   - `tanggalLahir`
   - `tempatLahir`
   - `jenisKelamin`
   - `id_alamat` (FK)

3. **Staf**
   - `id_staf` (PK)
   - `nama`
   - `noTelp`
   - `email`
   - `id_alamat` (FK)

4. **Guru**
   - `id_guru` (PK)
   - `nama`
   - `noTelp`
   - `email`
   - `id_alamat` (FK)

5. **AbsensiAnak**
   - `id_absensiAnak` (PK)
   - `tanggal`
   - `waktuMasuk`
   - `waktuKeluar`
   - `deskripsi`
   - `id_staf` (FK)

6. **AbsensiGuru**
   - `id_absensiGuru` (PK)
   - `tanggal`
   - `waktuMasuk`
   - `waktuKeluar`
   - `deskripsi`
   - `id_staf` (FK)

7. **AbsensiStaf**
   - `id_absensiStaf` (PK)
   - `tanggal`
   - `waktuMasuk`
   - `waktuKeluar`
   - `deskripsi`

8. **Laporan**
   - `id_laporan` (PK)
   - `id_guru` (FK)
   - `id_anak` (FK)
   - `id_orangtua` (FK)
   - `deskripsi`
   - `tanggal`
   - `logistik`

9. **Pembayaran**
   - `metodePembayaran`
   - `nama`
   - `tanggal`
   - `id_orangtua` (FK)
   - `id_staf` (FK)
   - `id_pembayaran` (PK)

10. **Alamat**
    - `id_alamat` (PK)
    - `nomorRumah`
    - `rtRw`
    - `kodepos`
    - `namaJalan`
    - `kecamatan`
    - `kelurahan`
    - `provinsi`
    - `kota`

### Relasi

- **OrangTua** memiliki banyak **Anak**.
- **OrangTua** memiliki banyak **Pembayaran**.
- **OrangTua** menerima banyak **Laporan**.
- **Anak** menerima banyak **Laporan**.
- **Guru** membuat banyak **Laporan**.
- **Staf** mengawasi banyak **AbsensiAnak** dan **AbsensiGuru**, serta mencatat banyak **AbsensiStaf** dan memproses banyak **Pembayaran**.
- **OrangTua**, **Anak**, **Staf**, dan **Guru** terhubung dengan **Alamat**.
##
![image (4)](https://github.com/RajaWalidain/4522210013_RajaWalidain_APBO_Daycare_28-05-2024/assets/145961029/13342df4-e1e8-4a94-8199-b5f5243a31b1) 
## UseCase
Use Case Diagram menggambarkan interaksi antara aktor dan sistem. Berikut adalah beberapa use case yang terdapat dalam sistem ini:

### Use Cases

1. **OrangTua**
   - Mendaftarkan Anak
   - Melakukan Pembayaran
   - Menerima Laporan
   - Mengakses Absensi

2. **Staf**
   - Mencatat Absensi Anak
   - Mencatat Absensi Guru
   - Memproses Pembayaran
   - Mencatat Absensi Staf
   - Memperbarui Informasi Kontak

3. **Guru**
   - Membuat Laporan
   - Mencatat Pendaftaran
   - Melakukan Absensi
  
4. **Anak**
   - Melakukan Absensi

![UseCase_APBO_29-04-2024](https://github.com/RajaWalidain/4522210013_RajaWalidain_APBO_Daycare_28-05-2024/assets/145961029/ad9a219d-ea10-4ffb-a28e-1b3faaa2c198)



## Class Diagram
Class Diagram digunakan untuk menggambarkan struktur kelas dalam sistem dan hubungan antara kelas-kelas tersebut. Berikut adalah detail dari kelas-kelas yang ada dalam sistem ini:

### Kelas dan Metode

1. **OrangTua**
   - Atribut: `id_orangtua`, `nama`, `no_telp`, `email`, `id_alamat`
   - Metode:
     - `MempunyaiAnak(int id_anak)`
     - `MelakukanPendaftaran(int id_pembayaran)`
     - `MenerimaReport(int id_laporan)`

2. **Anak**
   - Atribut: `id_anak`, `id_orangtua`, `nama`, `umur`, `tanggalLahir`, `tempatLahir`, `jenisKelamin`
   - Metode:
     - `MengahdiriPenitipan(date tanggal, time waktuMasuk, time waktuKeluar)`
     - `MengisiData(string nama, int umur, date tanggalLahir, string tempatLahir, string jenisKelamin)`
     - `MenerimaLaporan(int id_laporan)`

3. **Staf**
   - Atribut: `id_staf`, `nama`, `noTelp`, `email`
   - Metode:
     - `MencatatAbsensiAnak(int id_absensiAnak)`
     - `MencatatAbsensiGuru(int id_absensiGuru)`
     - `MemprosesPembayartan(int id_pembayaran)`
     - `MencatatAbsensiStaf(int id_absensiStaf)`

4. **Guru**
   - Atribut: `id_guru`, `nama`, `noTelp`, `email`
   - Metode:
     - `MembuatLaporan(int id_laporan)`
     - `MenandaiKehadiran(tanggal, waktuMasuk, waktuKeluar, Deskripsi)`

5. **AbsensiAnak**
   - Atribut: `id_absensiAnak`, `tanggal`, `waktuMasuk`, `waktuKeluar`, `deskripsi`, `id_staf`
   - Metode:
     - `markAttendance(date tanggal, time waktuMasuk, time waktuKeluar, string deskripsi)`
     - `updateAttendance(time waktuKeluar, string deskripsi)`

6. **AbsensiGuru**
   - Atribut: `id_absensiGuru`, `tanggal`, `waktuMasuk`, `waktuKeluar`, `deskripsi`, `id_staf`
   - Metode:
     - `markAttendance(date tanggal, time waktuMasuk, time waktuKeluar, string deskripsi)`

7. **AbsensiStaf**
   - Atribut: `id_absensiStaf`, `tanggal`, `waktuMasuk`, `waktuKeluar`, `deskripsi`
   - Metode:
     - `markAttendance(date tanggal, time waktuMasuk, time waktuKeluar, string deskripsi)`

8. **Laporan**
   - Atribut: `id_laporan`, `id_guru`, `id_anak`, `id_orangtua`, `deskripsi`, `tanggal`, `logistik`
   - Metode:
     - `createReport(int id_guru, int id_anak, int id_orangtua, string deskripsi, date tanggal, string logistik)`

9. **Pembayaran**
   - Atribut: `metodePembayaran`, `nama`, `tanggal`, `id_orangtua`, `id_staf`, `id_pembayaran`
   - Metode:
     - `MembuatPembayaran(string metodePembayaran, string nama, date tanggal, int id_orangtua, int id_staf)`

10. **Alamat**
    - Atribut: `id_alamat`, `nomorRumah`, `rtRw`, `kodepos`, `namaJalan`, `kecamatan`, `kelurahan`, `provinsi`, `kota`
    - Metode:
      - `updateAddress(string nomorRumah, string rtRw, string kodepos, string namaJalan, string kecamatan, string kelurahan, string provinsi, string kota)`
  ##
![DiagramClass_APBO_Daycare drawio](https://github.com/RajaWalidain/4522210013_RajaWalidain_APBO_Daycare_28-05-2024/assets/145961029/1666c4f0-11e9-438e-9d38-94d487f4c946)


