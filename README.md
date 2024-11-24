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
