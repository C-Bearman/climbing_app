# Send It — PWA Setup Guide

## What's in this folder

```
sendit-pwa/
├── index.html      ← the entire app
├── manifest.json   ← makes it installable on Android
├── sw.js           ← service worker (offline support)
├── icons/          ← app icons (you need to add these — see below)
└── README.md       ← this file
```

---

## Step 1 — Add app icons

You need two PNG icons. The quickest way:

1. Go to https://favicon.io/favicon-generator/
2. Type "SI", pick background colour `#1D9E75`, text colour white, font size ~50
3. Download and grab the `android-chrome-192x192.png` and `android-chrome-512x512.png` files
4. Rename them to `icon-192.png` and `icon-512.png`
5. Drop them into the `icons/` folder

---

## Step 2 — Put it on GitHub Pages (free hosting)

1. Go to https://github.com and sign in (or create a free account)
2. Click **New repository** → name it `sendit-pwa` → set to **Public** → click Create
3. On your computer, open a terminal in this folder and run:

```bash
git init
git add .
git commit -m "Initial Send It PWA"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/sendit-pwa.git
git push -u origin main
```

4. In GitHub, go to **Settings → Pages**
5. Under "Source", select **main** branch, folder **/ (root)** → click Save
6. After ~60 seconds your app is live at:
   `https://YOUR_USERNAME.github.io/sendit-pwa/`

---

## Step 3 — Install on your Pixel 8

1. Open **Chrome** on your Pixel 8
2. Go to `https://YOUR_USERNAME.github.io/sendit-pwa/`
3. Tap the **three-dot menu (⋮)** in the top right
4. Tap **"Add to Home screen"**
5. Tap **Add**

The app now appears on your home screen, opens full-screen with no browser bar, and works offline. It looks and feels like a native app.

---

## Updating the app later

Whenever you want to change something, edit `index.html`, then:

```bash
git add .
git commit -m "describe what you changed"
git push
```

GitHub Pages updates within ~60 seconds. The app on your phone will pick up the new version automatically next time it has an internet connection.

---

## Customising your training start date

In `index.html`, find this line (around line 210):

```js
const START = new Date('2026-06-02');
```

Change `2026-06-02` to the actual Monday your 12-week cycle starts. The "Week X of 12" counter will calculate automatically.

---

## Your data

All entries are stored in your browser's **localStorage** on your phone. Nothing is sent anywhere. To back up or share with your coach, use the **Export CSV** button inside the app — it downloads a `.csv` file you can open in Google Sheets or Excel.

---

## What's next (future features)

- [ ] Water reminder notifications during sessions
- [ ] "Are you climbing today?" morning prompt
- [ ] Auto-sync to Google Sheets via Google Apps Script
- [ ] Charts showing your energy/sleep trends over the 12 weeks
- [ ] Wrap as native APK with Capacitor
