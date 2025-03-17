# Static Data Denominasi Paket Data Pergiyuks

Selamat datang di repositori **Static Data Denominasi** untuk paket data **Pergiyuks**. Repositori ini menyediakan data statis dalam format JSON yang mendeskripsikan berbagai denominasi paket data. Data ini dapat digunakan untuk keperluan integrasi ataupun referensi.

## Struktur Data

Setiap denominasi memiliki deskripsi lengkap yang mencakup informasi seperti nama paket, tag, masa berlaku, kuota, dan deskripsi. Berikut adalah contoh struktur data:

```json
{
    "txt": "VOUCHER UNLIMITED (2GB/HARI) 28 HARI",
    "tags": "internet",
    "expire_in": "28 hari",
    "quota": "2 GB/hari",
    "description": "Dapatkan voucher unlimited dengan kuota 2GB setiap hari selama 28 hari. Ayo, jangan lewatkan kesempatan untuk tetap terhubung!"
}
```

### Penjelasan Field:
- **`txt`**: Nama original dari paket data.
- **`tags`**: Kategori atau tag yang mendeskripsikan jenis paket (contoh: `internet`, `telepon`, dll.).
- **`expire_in`**: Masa berlaku paket data.
- **`quota`**: Kuota yang disediakan oleh paket data.
- **`description`**: Deskripsi lengkap tentang manfaat dan detail paket data.

## Cara Mengakses Data

Data denominasi tersedia secara statis melalui CDN menggunakan layanan [jsDelivr](https://www.jsdelivr.com/). Anda dapat mengakses data dengan format URL berikut:

```
https://cdn.jsdelivr.net/gh/agusibrahim/ppobdenom@main/denom/<crc32_hash>/data.json
```

### Langkah-langkah:
1. **Hitung CRC32 Hash**:
   - Ambil nama nominal/paket data yang ingin diakses.
   - Ubah nilai nilainya menjadi lowercase.
   - Hitung nilai CRC32 dari teks tersebut. Misalnya, jika namanya `"voucher unlimited (2gb/hari) 28 hari"`, maka CRC32 hash-nya adalah `1a2b3c4d`.

2. **Akses Data**:
   - Gunakan nilai CRC32 hash untuk mengakses file JSON yang sesuai.
   - Contoh URL:
     ```
     https://cdn.jsdelivr.net/gh/agusibrahim/ppobdenom@main/denom/1a2b3c4d/data.json
     ```

3. **Hasil Respon**:
   - Jika hash valid, Anda akan menerima respons JSON seperti berikut:
     ```json
     {
         "txt": "VOUCHER UNLIMITED (2GB/HARI) 28 HARI",
         "tags": "internet",
         "expire_in": "28 hari",
         "quota": "2 GB/hari",
         "description": "Dapatkan voucher unlimited dengan kuota 2GB setiap hari selama 28 hari. Ayo, jangan lewatkan kesempatan untuk tetap terhubung!"
     }
     ```

## Contoh Penggunaan

Berikut adalah contoh penggunaan dalam JavaScript untuk mengambil data denominasi:

```javascript
const crc32Hash = '1a2b3c4d'; // Ganti dengan CRC32 hash dari txt
fetch(`https://cdn.jsdelivr.net/gh/agusibrahim/ppobdenom@main/denom/${crc32Hash}/data.json`)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error fetching data:', error));
```

## Kontribusi

Kami sangat terbuka untuk kontribusi! Jika Anda menemukan masalah atau ingin menambahkan fitur baru, silakan buat issue atau pull request di repositori ini.

### Cara Menambahkan Data Baru:
1. Tambahkan file JSON baru ke direktori `denom/<crc32_hash>/data.json`.
2. Pastikan `txt` diubah menjadi lowercase sebelum menghitung CRC32 hash.
3. Kirim pull request dengan perubahan Anda.

### Cara Mengedit Data:
1. Cari menggunakan fitur search github pada repository ini untuk menemukan `data.json`
2. Edit `data.json` lalu save/commit
