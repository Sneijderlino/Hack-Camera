# Hack-Camera

![Hack-Camera Screenshot](screenshot.png)

**Alat phishing kamera berbasis Bash/Unix** yang menyederhanakan pembuatan
halaman phishing populer (Jio recharge, ucapan festival, live YouTube,
pertemuan online) dan mengelola tunneling secara otomatis.

Skrip utama `hack-camera.py` bukan Python meskipun berekstensi `.py` — ia
mengandung kode shell (`bash`) yang dijalankan di lingkungan Unix/Termux.

> ⚠️ *Peringatan:* Seluruh fitur dalam repositori ini dapat dipakai untuk
> melanggar privasi pengguna lain. Gunakan hanya dalam pengujian keamanan
> yang sah atau dengan izin eksplisit pemilik perangkat.

---

## Daftar Isi

1. [Persyaratan](#persyaratan)
2. [Instalasi](#instalasi)
3. [Penggunaan](#penggunaan)
4. [Struktur Proyek](#struktur-proyek)
5. [Lisensi](#lisensi)
6. [Kontribusi](#kontribusi)

---

## Persyaratan

- Sistem berbasis Unix (Linux/macOS) atau Termux di Android.
- Shell `bash` tersedia sebagai interpreter.
- Program berikut ada di PATH:
  - `php` (versi 7.x atau lebih baru)
  - `curl`
  - `wget`
  - `unzip`
- Koneksi internet untuk mengunduh template dan tunneler.

> Termux: skrip akan berupaya menginstal dependensi melalui paket `pkg`.


## Instalasi

1. Clone repositori:
   ```bash
   git clone https://github.com/Sneijderlino/Hack-Camera.git
   cd Hack-Camera
   ```
2. Berikan izin eksekusi pada skrip utama:
   ```bash
   chmod +x hack-camera.py
   ```
3. Opsi (direkomendasikan): tambah skrip ke PATH agar bisa dipanggil dari
   lokasi manapun:
   ```bash
   sudo ln -s "$(pwd)/hack-camera.py" /usr/local/bin/hack-camera
   ```

> Jika Anda menggunakan Termux, pastikan direktori kerja berada di
> `~/` (home) dan jalankan `termux-setup-storage` sekali untuk mengizinkan
> skrip menyimpan file di `Pictures`.


## Penggunaan

1. Jalankan perintah:
   ```bash
   hack-camera     # jika sudah membuat symlink
   # atau
   ./hack-camera.py
   ```
2. Ikuti menu interaktif.

Menu menyediakan opsi-opsi berikut:

| Pilihan | Keterangan                                     |
|---------|------------------------------------------------|
| `1`     | Jio Recharge                                   |
| `2`     | Festival (masukkan nama festival)              |
| `3`     | Live YouTube (masukkan ID video)               |
| `4`     | Online Meeting                                 |
| `d`     | Ubah direktori penyimpanan gambar             |
| `p`     | Ubah port default untuk server PHP             |
| `t`     | Ganti tunneler default (Ngrok ↔ Cloudflared)   |
| `x`     | Informasi alat dan penulis                     |
| `m`     | Buka tautan grup/alat lainnya                  |
| `0`     | Keluar                                         |

3. Setelah memilih bait, skrip akan:
   - Mengunduh dan mengekstrak template HTML/PHP.
   - Menjalankan server PHP lokal di `127.0.0.1:7777`.
   - Meluncurkan `ngrok` dan `cloudflared`.
   - Menampilkan URL publik yang tersedia serta versi pendek dari
     `is.gd` jika berhasil.
4. Bagikan URL kepada sasaran. Ketika link diakses:
   - Alamat IP akan dicatat di berkas `ips.txt`.
   - Apabila kamera mengirim gambar, file akan dipindahkan ke folder
     yang dipilih (default: `~/Pictures` atau `./Pictures`).
5. Tekan `Ctrl+C` untuk menghentikan dan keluar kapan saja.


## Struktur Proyek

```
hack-camera.py   # skrip utama (bash)
README.md        # dokumentasi ini
templates/       # direktori sementara untuk file HTML/PHP
```


## Lisensi

Tidak ada lisensi formal. Penulis menyerahkan skrip untuk tujuan
pendidikan dan riset keamanan. Anda bertanggung jawab atas segala
penggunaan.


## Kontribusi

Silakan fork repositori, lakukan perubahan, dan ajukan pull request.
Perbaikan dokumentasi, penambahan template atau fitur baru sangat
dipersilakan.

---

*Terakhir diperbarui: 25 Februari 2026*

<https://github.com/Sneijderlino/Hack-Camera>
# Hack-Camera
