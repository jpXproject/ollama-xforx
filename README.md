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
