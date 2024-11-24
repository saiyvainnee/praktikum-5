## flowchart
```mermaid
flowchart TD
    A(["Mulai"]) --> B["Tampilkan Menu: (L)ihat, (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar"]
    B --> C["Input Pilihan Menu"]
    C --> D{"Pilihan Valid?"}
    D -->|Ya| E["Cabang Berdasarkan Pilihan"]
    D -->|Tidak| F["Tampilkan 'Pilihan tidak valid'"] --> G["Kembali ke menu"]

    %% Cabang Pilihan
    E --> H["L: Lihat Data"]
    E --> I["T: Tambah Data"]
    E --> J["U: Ubah Data"]
    E --> K["H: Hapus Data"]
    E --> L["C: Cari Data"]
    E --> M["K: Keluar Program"]

    %% Lihat Data
    H --> N{"Data kosong?"}
    N -->|Ya| O["Tampilkan 'TIDAK ADA DATA'"] --> G
    N -->|Tidak| P["Tampilkan daftar data mahasiswa"] --> G

    %% Tambah Data
    I --> Q["Input NIM"]
    Q --> R{"NIM sudah ada?"}
    R -->|Ya| S["Tampilkan 'Data dengan NIM tersebut sudah ada'"] --> G
    R -->|Tidak| T["Input data baru dan hitung Nilai Akhir"] --> U["Tampilkan 'Data berhasil ditambahkan!'"] --> G

    %% Ubah Data
    J --> V{"Data kosong?"}
    V -->|Ya| O
    V -->|Tidak| W["Input NIM"]
    W --> X{"NIM ditemukan?"}
    X -->|Ya| Y["Input data baru dan perbarui data"] --> G
    X -->|Tidak| Z["Tampilkan 'NIM tidak ditemukan'"] --> G

    %% Hapus Data
    K --> AA{"Data kosong?"}
    AA -->|Ya| O
    AA -->|Tidak| AB["Input NIM"]
    AB --> AC{"NIM ditemukan?"}
    AC -->|Ya| AD["Hapus data"] --> G
    AC -->|Tidak| Z

    %% Cari Data
    L --> AE["Input keyword (Nama/NIM)"]
    AE --> AF{"Data ditemukan?"}
    AF -->|Ya| P
    AF -->|Tidak| AG["Tampilkan 'Data tidak ditemukan'"] --> G

    %% Keluar Program
    M --> AH["Tampilkan 'Program selesai'<br>Program berhenti"]
    AH --> AI(["Selesai"])
```
# Pengelolaan Data Mahasiswa
Program berbasis Python yang digunakan untuk mengelola data mahasiswa, seperti menambahkan, melihat, mengubah, menghapus, dan mencari data mahasiswa. Berikut adalah penjelasan fungsi-fungsi utama dalam kode:

## 1. Struktur Data

```python 
data_mahasiswa = {}
```
- ```data_mahasiswa```: Dictionary untuk menyimpan data mahasiswa.
- Key: NIM (Nomor Induk Mahasiswa)
- Value: Dictionary yang berisi detail mahasiswa seperti nama, nilai tugas, UTS, UAS, dan nilai akhir.

## 2. Fungsi Utama
### a. ```lihat_data()```
- Fungsi ini menampilkan semua data mahasiswa dalam format tabel.
- Jika tidak ada data, tabel kosong akan ditampilkan dengan pesan "TIDAK ADA DATA".
- Jika ada data, setiap mahasiswa ditampilkan dengan nomor, nama, NIM, nilai tugas, UTS, UAS, dan nilai akhir (dihitung otomatis).

### b. ```tambah_data()```
- Digunakan untuk menambahkan data mahasiswa baru.
#### 1. Meminta pengguna memasukkan:
- NIM, Nama, Nilai Tugas, Nilai UTS, dan Nilai UAS.
#### 2. Menghitung Nilai Akhir menggunakan rumus:
- Nilai Akhir=(Nilai Tugas×30%)+(Nilai UTS×35%)+(Nilai UAS×35%)
#### 3. Menyimpan data ke dalam dictionary ```data_mahasiswa```.
#### 4. Memeriksa jika NIM sudah ada untuk menghindari duplikasi.

### c. ```ubah_data()```
- Mengubah data mahasiswa berdasarkan NIM.
#### 1. Menampilkan data mahasiswa menggunakan fungsi ```lihat_data()```.
#### 2. Meminta pengguna memasukkan NIM mahasiswa yang akan diubah.
#### 3. Jika NIM ditemukan, pengguna dapat memasukkan data baru (Nama, Nilai Tugas, UTS, UAS).
#### 4. Nilai Akhir dihitung ulang, dan data diperbarui.

### d. ```hapus_data()```
- Menghapus data mahasiswa berdasarkan NIM.
#### 1. Menampilkan data mahasiswa menggunakan fungsi ```lihat_data()```.
#### 2. Meminta pengguna memasukkan NIM yang ingin dihapus.
#### 3. Jika NIM ditemukan, data dihapus dari dictionary ```data_mahasiswa```.


### e. ```cari_data()```
- Mencari data mahasiswa berdasarkan Nama atau NIM.
#### 1. Meminta pengguna memasukkan keyword pencarian.
#### 2. Mencari data yang sesuai (Nama atau NIM) dengan metode filter.
#### 3. Menampilkan hasil pencarian dalam format tabel.
#### 4. Jika tidak ditemukan, menampilkan pesan "Data tidak ditemukan".
