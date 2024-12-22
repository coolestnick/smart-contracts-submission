# Aplikasi Manajemen Buku

## Deskripsi
Aplikasi ini adalah sistem manajemen buku berbasis teknologi blockchain menggunakan Internet Computer (IC) dengan dukungan stable storage menggunakan struktur data yang stabil (StableBTreeMap). Aplikasi ini menyediakan CRUD (Create, Read, Update, Delete) untuk mengelola buku, seperti menambahkan buku baru, meminjam, mengembalikan, dan menghapus buku.

### Fitur:
- Menambahkan buku baru ke dalam sistem.
- Mengambil buku berdasarkan ID.
- Mendapatkan daftar buku yang tersedia untuk dipinjam.
- Meminjam buku dan mengatur siapa yang meminjam.
- Mengembalikan buku.
- Menghapus buku berdasarkan ID.

### Genre Buku:
- Fiction
- NonFiction
- Science
- Technology

## Prasyarat
Sebelum menjalankan aplikasi ini, pastikan Anda memiliki lingkungan yang memenuhi prasyarat berikut:
- [Internet Computer Development Kit (ICDK)](https://sdk.dfinity.org/docs/)
- Pengetahuan dasar tentang Rust dan aplikasi dengan Internet Computer.
- Akses ke lingkungan pengembangan seperti `cargo`, `ic-cdk`, dan tools terkait lainnya.

## Instalasi & Menjalankan Aplikasi

### Persyaratan:
- **rustc** versi 1.64 atau lebih tinggi
  ```bash
  $ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
  $ source "$HOME/.cargo/env"
  ```
- **wasm32-unknown-unknown target**:
  ```bash
  $ rustup target add wasm32-unknown-unknown
  ```
- **candid-extractor**:
  ```bash
  $ cargo install candid-extractor
  ```
- **dfx**:
  ```bash
  $ DFX_VERSION=0.15.0 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"
  $ echo 'export PATH="$PATH:$HOME/bin"' >> "$HOME/.bashrc"
  $ source ~/.bashrc
  $ dfx start --background
  ```

### Langkah-Langkah Menjalankan Proyek:

1. **Persiapkan Lingkungan Pengembangan**:
   - Pastikan Anda sudah menginstal Internet Computer Development Kit (ICDK) dan telah menyiapkan proyek baru.

2. **Cloning Repository**:
   ```bash
   git clone https://github.com/your-repo/manajemen-buku.git
   cd manajemen-buku
   ```

3. **Install Dependencies**:
   Pastikan semua dependensi yang dibutuhkan telah diinstal:
   ```bash
   cargo build --release
   ```

4. **Menjalankan Proyek**:
   Jalankan proyek dengan menggunakan perintah berikut:
   ```bash
   ic-cdk serve
   ```

5. **Interaksi dengan API**:
   Setelah server berjalan, Anda dapat menggunakan perintah berikut untuk mengakses fungsi-fungsi:
   - `add_book`: Menambahkan buku baru.
     ```bash
     ic-cdk-query --query add_book "title: 'Buku Baru', author: 'Penulis', genre: 'Fiction'"
     ```
   - `get_book`: Mengambil buku berdasarkan ID.
     ```bash
     ic-cdk-query --query get_book 1
     ```
   - `borrow_book`: Meminjam buku.
     ```bash
     ic-cdk-update --update borrow_book 1
     ```
   - `return_book`: Mengembalikan buku.
     ```bash
     ic-cdk-update --update return_book 1
     ```
   - `delete_book`: Menghapus buku berdasarkan ID.
     ```bash
     ic-cdk-update --update delete_book 1
     ```

6. **Mengelola Buku**:
   - Gunakan endpoint-query dan endpoint-update untuk berinteraksi dengan data buku.
