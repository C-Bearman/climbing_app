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
- [x] `feature/workout-visualisations` — Workout Progress section in Charts tab; exercise picker adds individual cards; metric pills (Session Max / Session Total); sleep/energy dot colour coding with dynamic legend; "Colour nodes by" selector on Session Rating, Flexibility and Workout charts; time range slider wired to workout charts
- [x] `chore/ui-polish` — single-dot chart empty state ("not enough data" message); Remove Exercise button styled red and labelled clearly; tooltip colour metric line on all colour-coded charts (Session Rating, Flexibility, Workout Progress); tooltip label reads "Max 22.5kg" / "Total 12 reps" etc.; consistent date format across all chart tooltips ("Fri 3 Apr"); Stretching Consistency tooltip reads "Stretched X times" with week label "w/c 20 Apr"; coloured square removed from all tooltips; tooltip spacing and styling unified across chart types; Sleep/Water/Energy Trends nodes filled and all four lines have area fill; Trends tooltip formatted with colour square and units ("Sleep: 8h", "Mental: 7/10"); goal line tooltip shows label only with no date
- [x] `feature/csv-validation` — workout data section styled to match log page; Save as new cancel bug fixed; import restricted to .csv files only; CSV validation overlay listing header and date format errors; re-upload bug after cancelling validation fixed; two-step confirmation on both log and workout imports; log import supports Merge (overwrite matching dates, keep the rest) or Replace all (wipe and reload) to support both personal sync and coach use-cases; `.gitignore` added
- [x] `feature/history-and-deletion` — log history panel now scrollable (all entries shown, capped height with native scroll); delete button per entry with inline confirmation (Delete / Cancel); Delete Application Data button on both log and workout data sections with confirmation overlay, backup prompt, and Save data option before proceeding
- [x] `feature/workout-refinements` — per-exercise session notes field (40-char, live counter) beneath the set controls; notes stored in workout CSV and surfaced as 📝 tooltip labels on workout progress charts; workout date picker replaced with a custom calendar grid showing a green tinge on dates with saved workout data; date badge shows an open/close chevron consistent with chart and exercise accordions

### Next up
- [ ] Workout data visualisations in Charts tab — refine the exercise picker UX
- [x] Workout session notes — per-exercise notes field (40-char) on the workout tracker; shown as 📝 tooltip labels on workout progress charts
- [x] **Workout plans** — "Save as Plan" snapshots the exercises currently on the list (name/fields/PB field, no set data) as a named, reusable plan, e.g. "S&C B" (Arched Weighted Pull Ups, Banded Pull Ups, Incline Dumbbell Bench Press). Saved plans show as tappable pills above the exercise list; tapping one adds all its exercises as fresh blocks, stacking onto whatever's already there rather than replacing it. Also fixed a pre-existing PB radio bug this surfaced — see Workout tab — UI polish below
- [ ] **Workout planner / plan management screen** *(not yet scoped — no clear use-case yet)* — currently plans can only be created (Save as Plan) and deleted; there's no way to edit an existing plan's exercise list, reorder plans, or otherwise manage them beyond that. Something in this space will probably be needed eventually, but holding off scoping it until a real use-case shows up through actual use of the app rather than guessing upfront
- [x] **Plan cue notes** — optional per-exercise note on a plan (e.g. "37 degrees incline on my bench"), distinct from the graphed per-session "Session notes" field — a setup/technique reminder saved once on the plan rather than retyped every time. Prompted when saving a plan, shown in the apply confirm preview and as a persistent blue chip on the exercise block. Editable after the fact via each plan group's "Plan notes" button (tap to edit, no tight character limit since these aren't graphed) — see Workout plan groups below
- [x] **Workout plan groups** — applying a plan now wraps its exercises in a collapsible group card titled with the plan name, instead of appending them as an undifferentiated flat list — so applying two plans in one session stays traceable (which exercise came from which). Plan pills highlight once applied (light blue for the first plan applied that day, progressively darker for each subsequent one), reset when the viewed date changes. Each group has a small "Plan Notes" pill (left-aligned); tapping it opens a speech-bubble panel (CSS triangle tail pointing back at the pill) showing that plan's cue notes, with an "Edit notes" pill underneath that swaps to editable textareas + a Save pill. A ✕ in the group header removes that plan from today's session only (the saved plan itself is untouched) — a safeguard for applying the wrong plan on the wrong day
- [x] **Edit/extend a plan from within its group** — each group has its own "+ Add Exercise" (e.g. applied "Pull/Dip Day" then want to add Push Ups alongside it), plus two optional buttons: "Add to Plan" overwrites the saved plan with the group's current exercises (preserving existing cue notes by name match), "Create Plan" saves them as a new, separate plan instead and leaves the original untouched
- [ ] Rest day data — decide how rest days interact with the workout tracker; currently the workout tab is always available regardless of the daily log climbing toggle. Consider whether rest day entries should be blocked, flagged, or used to show recovery context on workout charts
- [x] History log UX — show 3 entries at a time, scrollable, rather than the full list
- [ ] Onboarding / tutorial overlay — first-launch walkthrough of Log, Workout and Charts tabs; must include how to rename or delete a misspelled exercise name (e.g. if a user saves "Jumpinh" they currently have no way to correct it); should also ask on first launch whether the user has existing data to import (supports the coach use-case where athletes export their CSV and hand it to a coach who can import and view their data)
- [ ] UX review: audit all info (ℹ︎) buttons across the app — check the text shown is accurate, helpful, and consistent in tone
- [x] **Energy scale reference** — ℹ︎ info button next to the Physical and Mental sliders on the Log tab, explaining the 1–3 / 4–7 / 8–10 bands. Colour thresholds for these two fields (slider fill + chart dot-colouring) were also aligned to the same 8/4 split so a given score shows the same colour everywhere in the app
- [ ] **User-configurable optional sections** — as more optional fields are added (finger health, nutrition, supplements, body measurements etc.), users should be able to hide sections they don't track and re-enable them later; a simple show/hide toggle per section stored in localStorage would keep the log form clean for users who only want the core fields
- [ ] User-configurable dot colour thresholds — Session Rating, Flexibility, and Workout Progress charts all let users choose which metric colours the dots (sleep / mental / physical energy); extend this so users can set their own green/amber/red thresholds per metric (e.g. "for me, 7h+ sleep is good, not 8h+")

### Charts — UI polish
- [ ] **Draggable chart ordering** — allow users to reorder the chart accordion sections by holding and dragging, so frequently used charts (e.g. Workout Progress) can be pinned to the top; order should persist across sessions via localStorage
- [x] **Session Rating x-axis** — switched from session numbers (1, 2, 3…) to actual calendar dates, matching the Trends chart style. Resolved the gap-handling concern by pre-filtering: the axis is built only from days that have a rating, so rest days are simply not ticks and the line never drops to zero
- [x] **Tooltip font rendering consistency** — previously Session Rating and Flexibility Rating charts used a custom linear x-axis while Workout Progress used a standard category axis, and Chart.js rendered Canvas tooltip text slightly differently between the two. Resolved as a side effect of the Session Rating x-axis change: all three chart types now share the same category axis and the tooltip fonts have been visually confirmed to match.
- [ ] **Selective chart re-render on colour selector change** — changing "Colour nodes by" on one chart currently triggers a full `drawAllCharts()` redraw, causing all visible charts to re-animate; ideally only the chart whose selector changed should update

### Charts — new visualisations
- [x] **Charts tab gating + starter view** — the full Charts tab (Daily goals, all chart sections) now stays hidden behind a simple "Getting started" view until `CHARTS_MIN_ENTRIES` (7, matching `checkMinData`'s existing "roughly one week" default) entries exist. The starter view shows a progress nudge (X/7) and a Climbing vs Rest day donut chart using green/blue-grey — colours picked as a reasonable default for this narrow two-colour case, not a stand-in for the palette decision below
- [x] **Climbing vs Rest day split chart (full dashboard version)** — a permanent "Climbing Activity" card in the main Charts dashboard (collapsible, like the other chart sections), with a Climbing vs Rest doughnut that respects the "Show last" time range slider, unlike the all-time starter-view version above
- [x] **Session type breakdown chart** — a doughnut in the same "Climbing Activity" card, scoped to climbing days in the selected time range, counting occurrences of each session type tag (Endurance / Max Power / Technical / Projecting / Volume / Outdoors / Social) — a day can carry multiple tags, so this counts tag occurrences rather than days. Colour palette: 7 distinct colours, none reusing the app's green/amber/red good/neutral/bad convention since no session type is "better" than another
- [x] **Volume and Outdoors session type tags** — added alongside the existing Endurance / Max Power / Technical / Projecting / Social tags
- [ ] **Climbing pyramid chart** — the classic climbing training pyramid: number of climbs completed at each grade, widest at the base (easier grades, more volume) narrowing towards the top (hardest sends). Depends on the route / grade log field above

### Workout tab — UI polish
- [ ] **Workout entry management** — no way to rename a misspelled exercise or delete individual saved sets; needs a management screen or edit flow, and must be covered in the onboarding tutorial
- [x] **Reps In Reserve (RIR)** — optional "RIR" checkbox alongside Reps/Weight/Duration; logs how many reps were left in reserve per set (0 = failure/max effort). Not offered as a PB metric. Not yet surfaced anywhere in charts — currently just logging/storage, no visualisation. Fixed a bug where re-importing an exported workout CSV containing RIR-tracked sets (fields like `reps|weight|rir`) falsely flagged them as "Invalid fields/pb_field" — the CSV validator's allowed-fields list had never been updated to include `rir` alongside `reps`/`weight`/`duration`
- [ ] **S&C catch-up sessions** *(low priority thought piece)* — explore how to handle S&C sets done on a different day than planned (e.g. missed Monday, did it Wednesday); currently the workout tab is date-agnostic but there is no way to flag a session as "catch-up" or link it to the intended session date
- [x] **Log entry deletion** — delete button per entry with inline confirmation; entry removed from localStorage, streak and week counter update immediately
- [x] **Workout date highlights** — workout date picker replaced with a custom calendar grid; dates with saved entries shown with a green tinge; date badge shows open/close chevron
- [x] **PB radio group collision bug** — `addExerciseBlock()` keyed each block's PB radio group on `Date.now()` (millisecond resolution); blocks added back-to-back synchronously (applying a workout plan, or loading a multi-exercise past day) could land in the same millisecond and silently share a radio group, so selecting "PB by: Reps" on one exercise would un-select it on another. Switched to an incrementing counter
- [x] **Workout plan apply/delete confirmations** — applying a plan confirms first and previews each exercise's last-session summary (e.g. "4 reps @ 138kg, then 3 sets of 3 reps @ 158kg"); deleting a plan explicitly warns it's permanent and lists what's being lost. Also added a persistent "Last time" chip inside each exercise block (same spot as the PB chip), so that reference info stays visible the whole time you're logging today's sets rather than only appearing once in a dialog you've since dismissed
- [ ] **Replace native `confirm()`/`prompt()` dialogs with styled overlays** — workout plans (apply/delete/save), and a few other spots in the app, currently use the browser's built-in confirm/prompt dialogs. They're functional but plain and can't be styled — worth swapping for the app's existing `.workout-overlay` pattern (already used for save confirmations etc.) for a more visually appealing, on-brand look
- [ ] **CSV import overlay UX** — the core import validation and Merge/Replace all flow is in place; revisit the wording, layout, and visual styling of the warning overlays on both Log and Workout tabs after real-world use to see if anything needs tightening up
- [ ] **Skip Merge/Replace prompt when there's no existing data** — if a user has just deleted all their data (or this is a first-time import) and there are zero existing entries, importing a CSV shouldn't need to ask Merge vs Replace all — there's nothing to merge with or replace, so the choice is meaningless. Check the entry count before showing the overlay; import straight away if it's empty. Applies to both the Log and Workout import flows
- [ ] **Workout tab needs the same post-import form refresh fix as the Log tab** — `doImportLog` was patched to re-read the selected date's data into the on-screen form after import, so sliders/toggles don't stay stale if the imported CSV includes the date already showing. `doImportWorkout` has the same underlying gap (saves data and refreshes the exercise picker/library, but never re-renders the currently viewed workout date) and needs the equivalent fix

### Log page — planned additions
- [x] **Climbing session type tracking** — tick-all-that-apply pill row on climbing days: Endurance, Max Power, Technical, Projecting, Social / Unstructured. Sits between Session Rating and Session notes, same `.pill` chip component used elsewhere. Feeds the session type breakdown chart below
- [x] **Time of day tracking** — optional single-select pill row (Morning/Afternoon/Evening/Night) on climbing days, to spot correlations between when you climb and how you feel (energy, session rating). Click the active pill again to clear it
- [ ] **Perceived session effort** — a simple 1–10 slider or rating for "how hard did today's session feel?", distinct from Session Rating (which captures quality/performance). Useful for tracking RPE trends and spotting when high effort isn't translating to good sessions (fatigue, overtraining signals)
- [ ] **Sleep quality rating** *(optional field)* — a daily sleep quality score (1–5: very poor → very good) alongside existing sleep hours; mirrors the scale used by the coach's tracking sheet and gives a richer picture than hours alone
- [ ] **Training % complete** — a field to log what percentage of the planned session was completed (0–100%); distinct from session rating (which captures quality); useful for flagging interrupted or partial sessions and correlating completion rate with energy and recovery metrics
- [x] **Work stress tracking** *(optional field)* — "Track today" / "Skip" toggle on the Log tab, then a 1–10 scale, following the same pattern as Stretching/Flexibility. Colour-coding is inverted from the energy sliders (high stress = red, not green). Also added as a "colour nodes by" option on Session Rating, Flexibility and Workout Progress charts, with days it wasn't tracked falling back to the existing grey "no data" dot
- [ ] **Route / grade log** — record what was actually climbed in a session: grade, and how many attempts/repeats (e.g. "6b — sent, repeated 3 times"; "7a — tried 4 times, not sent"). Needs a way to add multiple routes per session with grade + attempt count + sent/not-sent. This is the underlying data the climbing pyramid chart below is built from
- [ ] **Finger health tracking** *(optional field)* — a daily finger health rating (1–10) or a quick "any issues?" toggle with a notes field; useful for monitoring tweaks, pulley strains, and recovery over time. Could tie into the charts tab to overlay finger health against session ratings
- [ ] **Flexibility / stretching session notes** *(optional field)* — no metadata is currently captured for stretching sessions beyond the flex rating; add a dedicated notes field (e.g. what was stretched, type of mobility work, duration) similar to the session notes field already available for climbing days
- [ ] **Body measurements (optional, infrequent)** — weight (kg) and height (cm) stored as a separate profile, not a daily log field. Not something you fill in every session — more like a one-time or monthly update. Needs a dedicated section or modal, separate from the day-to-day log form
- [ ] **Strength-to-weight insights** — once body weight is stored, workout charts can express lifts as % of bodyweight (e.g. Pull-ups +60 kg at 90 kg = 167% BW). Climbing is a power-to-weight sport so this reframes raw numbers in a meaningful way
- [ ] **"Why track this?" info button** — a hold-to-reveal tooltip or info overlay on optional fields (weight, height, nutrition, supplements) explaining what insights that data unlocks. Keeps the UI clean for people who just want to log, but rewards curiosity
- [x] **Nutrition quality slider** (1–10, self-rated — how well did you eat today?) — opt-in Track today/Skip toggle alongside the existing calorie/protein fields, plus a 40-char notes field
- [ ] **Nutrition section mix-and-match clarity** — Calories, Protein, Nutrition quality and notes all sit behind one Track today/Skip toggle, but it's not obvious that each field within is independently optional too (e.g. logging only Protein, or only the quality rating, without filling the others). Needs some kind of visual hint — placeholder text, lighter field styling, or per-field "optional" labelling — so it reads as "fill in whatever's relevant" rather than implying all-or-nothing
- [ ] **Supplement tracker** — user-defined tick-box list (creatine, vitamin D, protein shake, etc.); presence/absence per day is enough — no units needed. Configurable by the user, similar to how exercises are defined in the workout tracker

### Future branches
- [ ] **Desktop / responsive layout** *(optional — Play Store is the primary target)* — the app is designed for a mobile viewport and works on phone screens. On a laptop or monitor the layout is narrow and centred. A responsive pass could widen the layout at larger breakpoints, reflow the tab navigation, and make charts larger — useful if coaches want to review athlete data on a desktop. This is lower priority than the Play Store APK build (see Eventual v1.0 below), but could be a lightweight CSS-only change if the scope is kept narrow.
- [ ] **Time-of-day visual theming** *(fun/polish, low priority)* — now that sessions can be tagged Morning/Afternoon/Evening/Night, the app's look could shift to match: background colours, lighting mood, maybe tied to actual device time rather than (or as well as) the logged session time. Wants a cute bear mascot worked in too — a nod to the Bearman Climbs name — e.g. a small illustration that changes scene per time of day (bear waking up at sunrise, bear under stars at night). Needs its own design thinking session before any build
- [ ] Goal lines extended to more metrics beyond sleep and water
- [ ] Water reminder notifications during climbing sessions
- [ ] Auto-sync to Google Sheets via Google Apps Script

### Eventual v1.0
- [ ] Wrap as native APK with Capacitor → **Bearman Climbs** on the Play Store

### Vision — accounts & personalisation *(long-term, not scoped yet)*
Eventually, support user accounts so each person can choose what they want to track rather than every optional field being on by default. Likely to become more important once/if the app reaches the Play Store (see Eventual v1.0 above) — a "real" distributed app tends to need accounts, and it would let preferences follow a user across devices.

Core principle this has to preserve: accounts are for storing *preferences* (which optional fields someone wants to log), not for syncing their actual training journal off the device. The "nothing is sent anywhere" promise (see **Your data** above) stays true for personal log data by default — an account doesn't change that unless a user explicitly opts in to something further, like the community insights idea below.

- [ ] **User accounts / login** — lightweight accounts scoped specifically to storing tracking preferences (not training data), so those preferences can follow a user across devices. Needs a minimal backend/auth strategy — deliberately narrow in scope, not a general data-sync backend
- [ ] **Onboarding asks what to track** — as part of first-launch onboarding (see Onboarding / tutorial overlay above), ask the user which optional metrics they want to log: work stress, physical/mental energy, finger health, nutrition, supplements, body measurements, etc. Builds on the User-configurable optional sections item above, but driven by account setup rather than discovered later in settings
- [ ] **Profile-driven dashboard** — the Charts tab shows only the sections relevant to what the user chose to track during onboarding, rather than every chart regardless of whether they log that data. Cascades from the onboarding choices above
- [ ] **Opt-in community insights** *(speculative, far future — only if the app reaches meaningful scale)* — generate anonymised, aggregate insights from users who explicitly opt in to sharing that data (e.g. benchmarking trends across the community). Strictly opt-in and aggregate only. The app's core purpose stays as a personal training journal for individual insight into your own sessions and trends — this would be an optional layer on top, never the default
- [ ] **Coach mode — assign workout plans to athletes** *(far future, depends on accounts above)* — a coach-facing version of the app where a coach can set/assign workout plans (see Workout plans above) for someone else to use, rather than each athlete only building their own. Needs accounts to exist first (to distinguish coach vs athlete), and its own view/permissions — a coach shouldn't see the exact same interface as an athlete
