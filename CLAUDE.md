# Earmark: notes for Claude

Earmark is a phone-first budget app: record money in and out, set money aside for planned payments, budgets, savings goals ("tabung"), debts (cards, paylater, loans) and trip budgets. Live at https://earmarkapp.github.io (GitHub Pages, served from `main`).

## Working with the owner
- The owner is not a programmer. Explain things in plain, short English, without jargon. Tell her exactly what to click or type when she has to do something herself.
- Plan first: for anything bigger than a small fix, write a short plan in plain words and get her OK before changing code.
- She tests on her own iPhone (installed to the Home Screen) and reports what to change.
- Keep the wording in the app plain and friendly, not "AI-sounding".

## How it's built
- No framework, no build step, no server. Everything is in `index.html` (HTML, CSS and JS), plus `sw.js` (offline cache), `manifest.json` and `icons/`.
- Currency is RM. Settings for the owner are in `CONFIG` near the top of the script (`supportUrl` is empty because there is no Ko-fi yet; leave it empty until she gives a link).

## User data: be careful
- Each user's data lives only in their own browser: `localStorage` key `earmark:v1` (theme: `earmark:theme`). No accounts, no sync, nothing is sent anywhere. Keep it that way unless she decides otherwise.
- Never rename the key or change the data shape without code that upgrades existing data. Real people (including the owner) have months of real money records in there.
- Backup/restore (one file) is the only safety net if the phone clears site data. Any change to the data must keep old backup files restorable. Test it: make data, back up, wipe, restore, and check every total matches.

## Releasing an update
1. Bump `APP_VERSION` in `index.html` (1.x.0 for new features, 1.x.y for fixes) and add an entry at the top of `CHANGELOG` (plain words, shown to users as "What's new").
2. Bump `VERSION` in `sw.js` (`earmark-vNN`) so phones load the new files.
3. Check it works on a phone-sized screen (light and dark), then commit and push to `main`.
- Commit author: `Earmark <noreply@earmarkapp.github.io>`.
- For risky experiments, use a branch and merge only after she has tried it.

## Privacy of the owner
- The credit line in the app is `@nurulkhairida_` (Instagram). Do not add any other handle, account or project of hers to this repo or the app.
- This repo is public. Don't put personal details, keys or passwords in it.

## Security checklist (static site)
- Anything the user types (names, notes, categories) must be escaped before it goes into the page (use the existing `esc()` helper). Never put user text straight into `innerHTML`.
- No outside scripts or trackers. Keep it that way.
- Restoring a backup must check the file and never run anything from it.
