# ✏️ Doodle Clipboard

A fun doodle-style online clipboard that lets you share text across devices in real-time using a 6-digit PIN.

---

## 🚀 Quick Setup (Local)

### 1. Install dependencies
```bash
npm install
```

### 2. Start the server
```bash
npm start
```

### 3. Open in browser
```
http://localhost:3000
```

---

## 📱 Cross-Device Sharing (Same Network)

To share between devices on the **same Wi-Fi**:

1. Find your computer's local IP address:
   - **Windows**: Run `ipconfig` → look for `IPv4 Address` (e.g. `192.168.1.10`)
   - **Mac/Linux**: Run `ifconfig` or `ip addr` → look for `inet` (e.g. `192.168.1.10`)

2. Start the server:
   ```bash
   npm start
   ```

3. On your phone/tablet, open:
   ```
   http://192.168.1.10:3000
   ```
   *(replace with your actual IP)*

Now Device A can send text → get a PIN → Device B enters the PIN → gets the text! ✅

---

## 🌍 Deploy to the Internet (Render.com — Free)

To share across the internet (different networks):

1. Push this folder to a GitHub repo
2. Go to [https://render.com](https://render.com) and sign up free
3. Click **New → Web Service** → connect your GitHub repo
4. Set:
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Environment**: Node
5. Click **Deploy** — Render gives you a free public URL like:
   ```
   https://doodle-clipboard.onrender.com
   ```

Both devices open that URL and sharing works from anywhere in the world!

---

## 🌍 Deploy to Railway (Alternative — also free)

```bash
npm install -g @railway/cli
railway login
railway init
railway up
```

---

## ✨ Features

| Feature | Description |
|---|---|
| 🚀 Send | Paste text → get a 6-digit PIN |
| 📥 Retrieve | Enter PIN on any device → get text |
| 🔥 Burn after reading | Text deleted after first retrieval |
| ⏳ Auto-expire | 1h / 24h / 7d / 30d options |
| 📋 Snippets | Save unlimited local snippets |
| 🔗 Share link | Direct URL with PIN embedded |
| 📷 QR Code | Scan to open on mobile instantly |
| 💾 Export/Import | Backup snippets as JSON |

---

## 📁 Project Structure

```
doodle-clipboard/
├── server/
│   └── index.js        ← Express API server
├── public/
│   └── index.html      ← Frontend (served by Express)
├── package.json
└── README.md
```

---

## ⚙️ API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/send` | Save text, returns PIN |
| GET | `/api/retrieve/:pin` | Fetch text by PIN |
| GET | `/api/status` | Server health check |

---

## 📝 Notes

- Text is stored **in memory** on the server — it clears if the server restarts
- For persistent storage, you can swap the in-memory `store` object with a database like SQLite or MongoDB
- Max text size: **100KB**
- PINs are **6-digit numbers** (100,000 – 999,999)
