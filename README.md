# 🌿 EcoAudit — Community Waste Logger

A web app for logging disposed waste with automatic GPS verification. Built as part of the CodeChef VITC Projects Department recruitment task.

---

## What It Does

Users pick a waste category, enter a weight, and submit. The app automatically captures their GPS coordinates on submission — no manual location input, so entries can't be faked. Everything gets saved to Firebase and shows up live on the dashboard for anyone to see, including a map with pins at each log location and running totals per category.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Database | Firebase Firestore |
| Maps | Leaflet.js + OpenStreetMap |
| Deployment | Vercel |

I went with vanilla JS instead of React because this was my first time building and deploying something end-to-end, and I didn't want a build setup getting in the way of actually shipping it. No npm, no bundler, one HTML file — Vercel deploys it in 30 seconds.

---

## Features

### MVP
- [x] Waste category + weight form
- [x] Auto GPS capture via `navigator.geolocation` — no manual input allowed
- [x] Real-time dashboard feed of all entries
- [x] Live per-category totals + grand total
- [x] Firebase Firestore persistence

### Bonus
- [x] Leaflet.js map with color-coded pins per category
- [x] Location error handling — permission denied, GPS unavailable, timeout all handled with clear UI messages
- [x] "Other" category with custom text input (appears only when selected)

---

## How to Run Locally

### 1. Clone the repo
```bash
git clone https://github.com/jaagritimandal/ecoaudit.git
cd ecoaudit
```

### 2. Add your Firebase config

Go to [console.firebase.google.com](https://console.firebase.google.com), create a project, enable Firestore in test mode, register a web app, and paste your config into `index.html` here:

```js
const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  ...
};
```

### 3. Serve locally

You need a local server because of ES Modules — just opening the file won't work.

```bash
# Python
python -m http.server 8000

# or Node
npx serve .
```

Then open `http://localhost:8000`.

---

## What I'd Improve With More Time

- **Better UI** — the current design is clean but I'd push it further, more polish on mobile especially
- **User accounts** — right now anyone can log anything anonymously. Adding Firebase Auth would let you tie entries to verified users, which makes the anti-fraud angle actually meaningful
- **Firestore security rules** — currently in test mode (open read/write). Production would need proper rules locked to authenticated users

---

## How I Built This

First time building something fully from scratch and deploying it. I'd done bits before — written JS, used APIs — but never the whole pipeline. The GPS part was new to me (figuring out how `navigator.geolocation` works and how to handle all the edge cases like denial and timeout). Same with Leaflet — hadn't used a map library before. Designed the UI in Figma first, then coded it to match. Used AI tools to understand steps I hadn't done before, looked up docs and debugged along the way.

---

## Links

- **Live app:** https://ecoaudit-q2m4c3jb8-jaagritimandals-projects.vercel.app
- **GitHub:** https://github.com/jaagritimandal/ecoaudit

---

*Built by Jaagriti Mandal*
