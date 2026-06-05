# Climbing App

A personal daily training log PWA built.

Live at: **https://c-bearman.github.io/climbing_app/**

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
