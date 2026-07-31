# 🦙 jpxcodex/xforx

[![Ollama](https://img.shields.io/badge/Ollama-Registry-000?logo=ollama)](https://ollama.com/jpxcodex/xforx)
[![Llama 3.2](https://img.shields.io/badge/Base-Llama%203.2-blue)](https://llama.meta.com/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> Model turunan dari Llama 3.2 dengan system prompt khusus untuk menjadi asisten yang ramah dan hangat.  
> Tersedia di [Ollama Registry](https://ollama.com/jpxcodex/xforx).

---

## 📖 Tentang Model Ini

`jpxcodex/xforx` adalah model **custom** yang dibangun di atas **Llama 3.2** (versi 3B atau 1B, tergantung yang ditarik).  
Perubahan utama hanya pada **system prompt** yang diatur menjadi:

> *"You are a friendly assistant. Always respond with a warm, helpful, and positive tone. If you don't know the answer, say so honestly and offer to help find the information."*

Dengan prompt ini, model akan selalu merespons dengan sikap bersahabat tanpa perlu Anda setel ulang setiap kali memulai percakapan. Ini sangat berguna untuk aplikasi chatbot, asisten pribadi, atau prototyping.

---

## ✨ Fitur

- Berbasis **Llama 3.2** dari Meta – ringan, cepat, dan open-weight.
- System prompt bawaan → respons selalu hangat dan positif.
- Parameter inferensi telah dioptimalkan untuk percakapan santai.
- Siap pakai secara lokal setelah di-pull (offline).
- Mudah dimodifikasi (Modelfile tersedia di bawah).

---

## 📋 Prasyarat

- **Ollama** versi terbaru (≥ 0.1.30) – [unduh di sini](https://ollama.com/download)
- Koneksi internet (untuk pull pertama kali)
- Ruang penyimpanan ~2 GB (untuk menyimpan model)

---

## 🚀 Instalasi & Penggunaan

### 1. Tarik (Pull) Model dari Registry

Karena model sudah dipublikasikan, Anda hanya perlu menariknya ke komputer lokal:

```bash
ollama pull jpxcodex/xforx
```

Proses ini akan mengunduh semua layer yang diperlukan (total sekitar 2 GB). Tunggu hingga muncul tulisan `success`.

### 2. Jalankan Model

Setelah berhasil di-pull, jalankan dengan:

```bash
ollama run jpxcodex/xforx
```

Anda akan masuk ke mode interaktif. Mulai ketik pertanyaan atau perintah.

### 3. Contoh Penggunaan

#### Mode interaktif
```bash
$ ollama run jpxcodex/xforx
>>> Halo, apa kabar?
Halo! Saya baik-baik saja, terima kasih sudah bertanya. Ada yang bisa saya bantu hari ini? 😊

>>> Ceritakan tentang cuaca hari ini.
Maaf, saya tidak memiliki akses ke informasi cuaca terkini. Tapi saya sarankan Anda cek aplikasi cuaca favorit atau situs BMKG. Semoga harimu cerah!
```

#### Mode one-shot (langsung jawab)
```bash
ollama run jpxcodex/xforx "Berikan saya 3 tips untuk tetap produktif"
```

#### Dengan input dari file
```bash
ollama run jpxcodex/xforx < input.txt
```

---

## ⚙️ Konfigurasi (Modelfile)

Berikut adalah isi lengkap `Modelfile` yang digunakan untuk membuat model ini.  
Simpan kode di bawah sebagai `Modelfile` jika Anda ingin membangun ulang atau memodifikasi sendiri.

```dockerfile
# Modelfile untuk jpxcodex/xforx
# Dibuat berdasarkan llama3.2

FROM llama3.2

# System prompt
SYSTEM """
You are a friendly assistant. Always respond with a warm, helpful, and positive tone. 
If you don't know the answer, say so honestly and offer to help find the information.
"""

# Parameter default
PARAMETER temperature 0.7
PARAMETER top_p 0.9
PARAMETER top_k 40
PARAMETER num_ctx 4096
PARAMETER stop "</s>"
PARAMETER stop "<|eot_id|>"
```

### Penjelasan Parameter

| Parameter      | Nilai | Fungsi |
|----------------|-------|--------|
| `temperature`  | 0.7   | Kontrol kreativitas (rendah = lebih deterministik, tinggi = lebih variatif) |
| `top_p`        | 0.9   | Nucleus sampling – membatasi pilihan kata berdasarkan probabilitas kumulatif |
| `top_k`        | 40    | Hanya pertimbangkan 40 kata teratas setiap langkah |
| `num_ctx`      | 4096  | Ukuran jendela konteks (token) – cukup untuk percakapan sedang |
| `stop`         | `</s>`, `<|eot_id|>` | Token penghenti untuk mengakhiri generasi |

---

## 🔧 Membangun Ulang atau Memodifikasi

Jika Anda ingin mengubah perilaku model (misal mengganti system prompt atau parameter), ikuti langkah ini:

1. **Salin** kode `Modelfile` di atas ke dalam file bernama `Modelfile` di komputer Anda.
2. **Edit** sesuai keinginan (misal ubah kalimat system prompt, atau sesuaikan `temperature`).
3. **Buat model baru** dengan perintah:
   ```bash
   ollama create -f Modelfile nama-model-baru-anda
   ```
4. **Uji** model baru:
   ```bash
   ollama run nama-model-baru-anda
   ```
5. **(Opsional) Publikasikan** ke registry jika ingin dibagikan:
   ```bash
   ollama push username-anda/nama-model
   ```

---

## 🧪 Verifikasi Model

Untuk memastikan model telah terunduh dengan benar, Anda bisa mengecek daftar model lokal:

```bash
ollama list
```

Anda akan melihat `jpxcodex/xforx` dengan tag `latest`.  
Untuk melihat detail konfigurasi:

```bash
ollama show jpxcodex/xforx
```

---

## 📄 Lisensi & Atribusi (Termasuk Teks Meta)

Model ini menggunakan dua lapis lisensi:

### 1. Lisensi Model Dasar (Llama 3.2)
Model dasar **Llama 3.2** adalah karya dari **Meta Platforms, Inc.** dan dilisensikan di bawah **[Llama 3.2 Community License](https://llama.meta.com/llama3/license/)**.  
Dengan menggunakan model ini, Anda setuju untuk mematuhi ketentuan lisensi tersebut, termasuk:
- Penggunaan komersial diperbolehkan selama dalam batas tertentu.
- Tidak boleh digunakan untuk melanggar hukum atau kebijakan Meta.
- Wajib mencantumkan atribusi kepada Meta jika model ini digunakan dalam produk atau layanan.

### 2. Lisensi Modifikasi dan Konfigurasi
Seluruh perubahan (system prompt, parameter, dan konfigurasi) yang dilakukan oleh **jpxcodex** dilisensikan di bawah lisensi **MIT** yang sederhana dan permisif.  
Berikut teks lengkap lisensi MIT untuk bagian modifikasi:

```
MIT License

Copyright (c) 2026 jpxcodex

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Ucapan Terima Kasih

- **Meta AI** – atas pengembangan dan rilis terbuka model Llama 3.2 yang menjadi fondasi model ini.
- **Ollama** – atas platform luar biasa yang memudahkan pengelolaan dan distribusi model AI secara lokal.

---

**Selamat mencoba!** Semoga model ini bermanfaat dan menjadi teman diskusi yang ramah. 😊
