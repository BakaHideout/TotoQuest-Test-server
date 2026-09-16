# TotoQuest — self-hosting & updates

## Put it on GitHub Pages (free, ~5 minutes)
1. Create a new GitHub repo (public or private).
2. Upload all 5 files in this folder to the repo root: `index.html`, `manifest.json`,
   `sw.js`, `icon-192.png`, `icon-512.png`.
3. In the repo, go to **Settings → Pages**, set Source to your default branch, root folder.
4. GitHub gives you a URL like `https://yourname.github.io/your-repo/`. Open it on your
   phone and use "Add to Home Screen" — it installs like a real app icon.

## Pushing updates
Any time you want to change something (swap the logo, tweak balance, fix a bug):
1. Edit the files locally (or edit them right on github.com) and commit/push.
2. That's it — no rebuild step, no app store review.

## How players get notified of the update
The app checks for a new version every time it's opened or brought back to the
foreground. If it finds one, a banner slides up:

> 🔄 A new version of TotoQuest is available — tap to update

Tapping it swaps in the new version and reloads. Nothing happens automatically in the
background without their tap, so a player is never yanked into a reload mid-battle.

Technical note: this works because `sw.js` includes a version string
(`CACHE_NAME = 'totoquest-v2'`). Browsers automatically re-check `sw.js` for byte
changes, so simply changing that version string (or any other file) is enough to
trigger the update banner for everyone — you don't need to do anything extra.
