# BearmanClimbs

A personal climbing training log — built as a PWA (Progressive Web App) using vanilla HTML, CSS and JavaScript.

**Live app:** https://c-bearman.github.io/climbing_app/

---

## What it does

Daily logging of training metrics, stored locally on your phone:

- Climbing day / Rest day toggle
- Sleep hours and water intake
- Physical and mental energy (1–10)
- Session rating and session notes (climbing days)
- Stretching / mobility toggle and flexibility rating (1–10)
- Optional nutrition (calories and protein)
- General notes

**Charts tab** — visualise trends over time: session ratings, sleep, water, energy, flexibility and stretching consistency. Includes goal lines for sleep and water targets.

**CSV export / import** — keeps a single master file you can hand to your coach or restore from at any time.

---

## Your data

All entries live in **localStorage** on your phone — nothing is sent anywhere. To back up or share with your coach, tap **Export CSV** in the Data section. To restore on a new device or after clearing your browser, tap **Import CSV** and select your file.

---

## Installing on Android

1. Open **Chrome** on your phone and go to the live URL above
2. Tap the three-dot menu → **Add to Home screen**
3. The app will appear on your home screen and open full-screen with no browser bar

---

## Updating the app

Whenever a change is pushed to `master`, GitHub Pages redeploys within ~60 seconds. The service worker will pick up the new version automatically on the next load. If changes don't appear, go to Chrome → Settings → Privacy and security → Clear browsing data → Cached images and files.

---

## Roadmap

### Recently shipped
- [x] `feature/notes-tooltips` — 40-char notes fields with live counter; two-line tooltips on Session Rating and Flexibility charts
- [x] `feature/workout-tracker` — third Workout tab; exercises with flexible field tracking (Reps / Weight / Duration); PB chips; sets with copy/hold-to-delete; full-screen save confirmation; CSV export & import

### Next up
- [ ] Workout data visualisations in Charts tab — refine the exercise picker UX; add PB milestone marker (dashed line at all-time best); wire up the existing time-range slider to workout charts
- [ ] History log UX — show 3 entries at a time, scrollable, rather than the full list
- [ ] Onboarding / tutorial overlay — first-launch walkthrough of Log, Workout and Charts tabs

### Log page — planned additions
- [ ] **Body measurements (optional, infrequent)** — weight (kg) and height (cm) stored as a separate profile, not a daily log field. Not something you fill in every session — more like a one-time or monthly update. Needs a dedicated section or modal, separate from the day-to-day log form
- [ ] **Strength-to-weight insights** — once body weight is stored, workout charts can express lifts as % of bodyweight (e.g. Pull-ups +60 kg at 90 kg = 167% BW). Climbing is a power-to-weight sport so this reframes raw numbers in a meaningful way
- [ ] **"Why track this?" info button** — a hold-to-reveal tooltip or info overlay on optional fields (weight, height, nutrition, supplements) explaining what insights that data unlocks. Keeps the UI clean for people who just want to log, but rewards curiosity
- [ ] **Nutrition quality slider** (1–10, self-rated — how well did you eat today?) alongside the existing calorie/protein fields
- [ ] **Supplement tracker** — user-defined tick-box list (creatine, vitamin D, protein shake, etc.); presence/absence per day is enough — no units needed. Configurable by the user, similar to how exercises are defined in the workout tracker

### Future branches
- [ ] Goal lines extended to more metrics beyond sleep and water
- [ ] Water reminder notifications during climbing sessions
- [ ] Auto-sync to Google Sheets via Google Apps Script

### Eventual v1.0
- [ ] Wrap as native APK with Capacitor → **Bearman Climbs** on the Play Store
