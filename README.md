# Climbing App

A personal daily training log PWA built for the 12-week bouldering coaching cycle.

Live at: **https://c-bearman.github.io/climbing_app/**

---

## Project structure

```
climbing_app/
├── index.html      ← the entire app
├── manifest.json   ← makes it installable on Android
├── sw.js           ← service worker (offline support)
├── icons/          ← app icons
└── README.md       ← this file
```

---

## App icons

You need two PNG icons in the `icons/` folder. The quickest way to generate them:

1. Go to https://favicon.io/favicon-generator/
2. Type "CA", background colour `#1D9E75`, text colour white, font size ~50
3. Download and rename to `icon-192.png` and `icon-512.png`
4. Drop them into the `icons/` folder, commit and push

---

## Updating the app

Whenever you make a change, push it up and GitHub Pages will update within ~60 seconds:

```bash
git add .
git commit -m "describe what you changed"
git push
```

---

## Customising your training start date

In `index.html`, find this line (around line 210):

```js
const START = new Date('2026-06-02');
```

Change `2026-06-02` to the Monday your 12-week cycle actually starts. The "Week X of 12" counter will calculate automatically from there.

---

## Your data

All entries are stored in **localStorage** on your phone — nothing is sent anywhere. To share with your coach, use the **Export CSV** button in the app, which downloads a `.csv` you can drop into Google Sheets or Excel.

---

## Roadmap

- [ ] Water reminder notifications during sessions
- [ ] "Are you climbing today?" morning prompt
- [ ] Auto-sync to Google Sheets via Google Apps Script
- [ ] Charts showing energy/sleep trends over the 12 weeks
- [ ] Wrap as native APK with Capacitor → Bearman Climbs
