# 🔐 Code Block Encryptor (Password-Based)

A lightweight, **client-side web app** that encrypts and decrypts code blocks using a password.  
Everything runs **entirely in your browser** — no servers, no uploads, no telemetry.

Perfect for safely sharing sensitive snippets in notes, GitHub issues, chat, or documentation.
[[https://robbie-med.github.io/encryptor/]]
---

## ✨ Features

- 🔒 **Strong encryption**: AES-256-GCM
- 🔑 **Password-derived keys** using PBKDF2 (SHA-256, 200k iterations)
- 🌐 **Client-only**: works offline, no backend required
- 📋 **Copy-paste friendly** encrypted output
- 🧾 Self-describing encrypted bundle format (JSON → Base64URL)
- 🚫 Tamper detection (AES-GCM authentication)

---

## 🚀 Getting Started

### Option 1: Run Locally
1. Clone or download this repository
2. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)
3. That’s it — no build step, no dependencies

### Option 2: GitHub Pages
1. Push the repo to GitHub
2. Enable **Settings → Pages**
3. Select the branch containing `index.html`
4. Access via your GitHub Pages URL

---

## 🧠 How It Works (High Level)

1. You enter a **password**
2. A cryptographic key is derived using:
   - PBKDF2
   - SHA-256
   - 200,000 iterations
   - Random salt
3. The code block is encrypted with **AES-GCM**
4. Output is packaged as a portable encrypted bundle

All cryptography is handled by the **Web Crypto API**.

---

## 📦 Encrypted Bundle Format

The encrypted output is a Base64URL-encoded JSON object:

```json
{
  "v": 1,
  "alg": "AES-GCM",
  "kdf": "PBKDF2",
  "iter": 200000,
  "hash": "SHA-256",
  "salt": "...",
  "iv": "...",
  "ct": "..."
}
