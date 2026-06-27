# 🌿 EcoAudit — Community Waste Logger

A lightweight web app for logging disposed waste with **automatic GPS verification**. Built for the CodeChef VITC Projects Department recruitment task.

---

## What It Does

- Users log waste by selecting a **category** (Plastic, E-Waste, Organic, etc.) and entering a **weight in kg**
- On submit, the browser's **native Geolocation API** automatically captures real GPS coordinates — no manual input allowed (anti-fraud)
- Entries are saved to **Firebase Firestore** and appear in real-time for all users
- The **Dashboard** shows live aggregate totals per category, a **Leaflet.js map** with pins at each log location, and a chronological feed of all entries

---

## Tech Stack

| Layer      | Technology                          |
|------------|-------------------------------------|
| Frontend   | Vanilla HTML, CSS, JavaScript (ES Modules) |
| Database   | Firebase Firestore (real-time NoSQL) |
| Maps       | Leaflet.js + OpenStreetMap (free, no API key needed) |
| Deployment | Vercel / Netlify (static hosting)   |
| Fonts      | Space Grotesk + Space Mono (Google Fonts) |

No build step. No framework. No npm. One HTML file.

---

## Features

### MVP (Required)
- [x] Waste category + weight form
- [x] Auto GPS capture via `navigator.geolocation` (no manual location field)
- [x] All entries displayed on the Dashboard feed
- [x] Live per-category totals + grand total
- [x] Firebase Firestore persistence

### Bonus
- [x] Map visualization with Leaflet.js (pins colored by category)
- [x] Location error handling (permission denied, unavailable, timeout — all handled with clear UI messages)

---

## How to Run Locally

### 1. Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/ecoaudit.git
cd ecoaudit
```

### 2. Set up Firebase

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add Project** → name it `ecoaudit` → continue
3. On the project homepage, click the **`</>`** (Web) icon to add a web app
4. Register the app, copy the `firebaseConfig` object shown
5. Go to **Firestore Database** → **Create database** → choose **Start in test mode** → pick any region → Done

### 3. Paste your Firebase config

Open `index.html` and find this block near the top:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  ...
};
```

Replace the placeholder values with your actual config from step 2.

### 4. Open the app

Because this uses ES Modules, you need a local server (not just opening the file directly).

**Option A — VS Code Live Server extension:**
Right-click `index.html` → "Open with Live Server"

**Option B — Python:**
```bash
python -m http.server 8000
# then open http://localhost:8000
```

**Option C — Node.js:**
```bash
npx serve .
```

---

## Deployment (Vercel — recommended)

1. Push your code to a **public GitHub repository**
2. Go to [https://vercel.com](https://vercel.com) → **Add New Project**
3. Import your GitHub repo
4. Click **Deploy** — Vercel will detect it's a static site automatically
5. Your live URL will appear in ~30 seconds

> ⚠️ Make sure your Firebase config is already filled in before deploying.

---

## Project Structure

```
ecoaudit/
└── index.html      # Entire app (HTML + CSS + JS in one file, intentionally minimal)
└── README.md
```

The app is intentionally a single file — there's no build step, no bundler, and no framework overhead. Firebase and Leaflet are loaded via CDN. This makes deployment trivially simple.

---

## Firebase Security Note

The Firestore database is in **test mode** for this submission (open read/write). For a production app, you would add Firestore Security Rules and Firebase Auth before going public.
