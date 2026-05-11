# Grocery Store App

[![Release](https://img.shields.io/github/v/release/808cadger/grocery-store-app?include_prereleases&label=release)](https://github.com/808cadger/grocery-store-app/releases)
[![Last commit](https://img.shields.io/github/last-commit/808cadger/grocery-store-app)](https://github.com/808cadger/grocery-store-app/commits)
[![License](https://img.shields.io/github/license/808cadger/grocery-store-app)](https://github.com/808cadger/grocery-store-app/blob/HEAD/LICENSE)
![Platforms](https://img.shields.io/badge/platform-Expo%2FReact%20Native%2C%20Android%2C%20Web%2C%20API%20service-2563eb)

AI grocery assistant for shopping lists, store-aware workflows, and mobile shopping guidance.

## Project Snapshot

| Area | Details |
|------|---------|
| Primary use case | AI grocery assistant for shopping lists, store-aware workflows, and mobile shopping guidance. |
| Platforms | Expo/React Native, Android, Web, API service |
| Core stack | Expo, React Native, Android, FastAPI |
| Review first | `app`, `backend` |

## Download Links

| Platform | Link |
|----------|------|
| iOS / iPhone | [Open the PWA in Safari](https://808cadger.github.io/grocery-store-app/) and choose **Share -> Add to Home Screen** |
| Android | [Download the latest APK from GitHub Releases](https://github.com/808cadger/grocery-store-app/releases/latest) |
| Source | [Download the GitHub source ZIP](https://github.com/808cadger/grocery-store-app/archive/refs/heads/main.zip) |
| Repository | [View on GitHub](https://github.com/808cadger/grocery-store-app) |

## Why This Repo Is Worth Reviewing

- Mobile-first architecture fits in-store use.
- Backend/API service is documented for AI-powered shopping features.
- Android build path is ready for device testing.


<!-- INSTALL-START -->
## Install and run

These instructions install and run `grocery-store-app` from a fresh clone.

### Clone
```bash
git clone https://github.com/808cadger/grocery-store-app.git
cd grocery-store-app
```

### Expo app
```bash
cd app
npm install
npm start
npm run web
```

### Expo Android build
```bash
cd app
npm run android
npm run build:android
```

### Python/API service
```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### Notes
- Expo apps require the Expo/React Native local prerequisites for native Android builds.
- Create any required `.env` file from `.env.example` before starting backend services.

### AI/API setup
- If the app has AI features, add the required provider key in the app settings or local `.env` file.
- Browser-only apps store user-provided API keys on the local device unless a backend endpoint is configured.

### License
- Apache License 2.0. See [`LICENSE`](./LICENSE).
<!-- INSTALL-END -->


> AI-powered grocery assistant — detects when you walk into the store, guides you to every item on your list, and puts an AI chatbot on every screen.

---

## What it does

| Feature | Description |
|---------|-------------|
| 🏪 **Store detection** | GPS geofence auto-detects when you enter the store and greets you |
| 🛒 **AI chatbot** | Full-screen chat powered by Claude on every screen — drag the FAB anywhere |
| 🗺️ **Route planning** | Give it your list, get optimized step-by-step aisle directions |
| 📍 **Item finder** | Find any item's exact aisle and section instantly |
| 🔄 **Out-of-stock alerts** | Suggests nearby stores with the item in stock |
| 📝 **Shopping list** | Persistent list with checkoff and AI-powered routing |
| 🏪 **Store map** | Visual aisle-by-aisle layout with item locations |
| 🛍️ **Online ordering** | One-tap order links for 13+ major grocery chains |

---

## Screenshots

> App features a full-screen AI chat, draggable floating assistant button with animated glow ring, slide-in message animations, and real-time streaming responses.

---

## Tech stack

```
app/        React Native (Expo 51) + TypeScript
backend/    Python FastAPI + Claude claude-opus-4-6 (Anthropic)
```

---

## Getting started

### 1. Get an Anthropic API key

Sign up at [console.anthropic.com](https://console.anthropic.com) → Create API Key

### 2. Start the backend

```bash
cd backend
cp .env.example .env
# Paste your key into .env:  ANTHROPIC_API_KEY=sk-ant-...

pip install -r requirements.txt
python main.py
# Runs at http://localhost:8000
```

### 3. Start the mobile app

```bash
cd app
npm install
npm start
```

Install **Expo Go** on your phone → scan the QR code → done.

### 4. Set your backend IP (physical device)

In `app/services/api.ts`, update `API_BASE_URL`:

```ts
// Android emulator
const API_BASE_URL = "http://10.0.2.2:8000";

// Physical phone (use your computer's local IP)
const API_BASE_URL = "http://192.168.x.x:8000";
```

---

## Build standalone APK

```bash
cd app
npm install -g eas-cli
eas login
eas build --platform android --profile preview
```

EAS gives you a download link and QR code to share.

---

## Customize for your store

Edit `backend/main.py`:

- `STORE_INVENTORY` — add/remove items, update aisles and prices
- `STORE_LAT` / `STORE_LNG` in `app/screens/HomeScreen.tsx` — your store's GPS coordinates
- `GEOFENCE_RADIUS_METERS` — detection radius (default 200m)

---

## Supported store chains

Walmart · Kroger · Safeway · Whole Foods · Target · Publix · Costco · ALDI · H-E-B · Trader Joe's · Food Lion · Meijer · Instacart

---

## Architecture

```
app/
  App.tsx                  ← Bottom tab navigation + onboarding
  screens/
    HomeScreen.tsx         ← GPS detection, quick actions, store selector
    ShoppingListScreen.tsx ← Persistent list with AI routing
    StoreMapScreen.tsx     ← Visual aisle map
    OnboardingScreen.tsx   ← First-run setup flow
  components/
    ChatBar.tsx            ← Full-screen AI chat (draggable FAB, animations)
    StoreIdentityCard.tsx  ← Current store display
  services/
    api.ts                 ← Streaming SSE client

backend/
  main.py                  ← FastAPI + Claude with 7 tools + streaming
```

---

Built with [Claude claude-opus-4-6](https://anthropic.com) · React Native (Expo) · FastAPI
