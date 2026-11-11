# Earmark

**Know what's actually safe to spend.**

Earmark is a simple budget app for your phone. Record money in and out in seconds, set aside money for bills, and track savings goals and debts.

- Planned payments that repeat every month, plus one-off ones
- Spending budgets (Groceries, Food) that you log against
- Credit cards, paylaters and loans, showing what you owe and roughly when it'll be paid off
- Backup and restore with a single file

🔒 **Your data never leaves your phone.** There's no account and no server. Everything is saved in your browser on your device. Save a backup now and then.

## Install on your phone
Open the site, then:
- **iPhone (Safari):** Share → *Add to Home Screen*
- **Android (Chrome):** ⋮ → *Add to Home screen* / *Install app*

## Settings for the site owner
At the top of `index.html`, in `CONFIG`:
- `supportUrl` — your Ko-fi / Buy Me a Coffee link (leave empty to hide the button)
- `madeBy`, `madeByUrl` — credit shown in Settings

When you update the site, bump `VERSION` in `sw.js` so phones pick up the new version.
