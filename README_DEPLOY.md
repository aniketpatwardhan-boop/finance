# Your finance dashboard as an app

This folder is your complete app. The dashboard inside `index.html` is AES-256
encrypted — whoever hosts it only ever sees scrambled data. It decrypts in your
browser with your password.

## One-time setup (~10 min)

1. Go to https://app.netlify.com (free account) → "Add new site" → "Deploy manually".
2. Drag THIS WHOLE FOLDER onto the page. You get a URL like https://something.netlify.app
   (you can rename it under Site settings → Change site name).
3. Open the URL on your phone → enter your password → tick "Remember on this device".
4. Install it like an app:
   - iPhone/iPad (Safari): Share button → "Add to Home Screen".
   - Android (Chrome): menu ⋮ → "Add to Home screen" / "Install app".

Now it opens full-screen with its own icon, and works offline after the first load.

## After every monthly data refresh

Ask Claude: "rebuild the app" (it runs `build_app.py` in the parent folder with your
password), then drag this folder onto Netlify again (Deploys → drag & drop). Done.

## Security notes

- The host (Netlify) never sees your data — only the encrypted blob.
- "Remember on this device" stores the decryption key on that device only. Don't use
  it on shared computers. To forget: clear the site's browsing data.
- If you want a new password, rerun: python3 ../build_app.py "new-password"

## Alternative: GitHub Pages (instead of Netlify)

Note: on a free GitHub account the repository must be PUBLIC. Only the encrypted
file is exposed — unreadable without your password — but Netlify keeps it unlisted
if you prefer.

1. Create an account at github.com (pick a neutral username — it appears in the URL).
2. "+" (top right) → New repository → name e.g. "finance" → Public → Create repository.
3. Add file → Upload files → drag the 5 files from this folder (index.html,
   manifest.webmanifest, sw.js, icon-192.png, icon-512.png) → Commit changes.
4. Settings → Pages → Source: "Deploy from a branch", branch "main", folder "/ (root)" → Save.
5. After 1–2 min the page shows: live at https://<username>.github.io/finance/
6. Open on phone → password → Add to Home Screen (Safari: Share menu; Chrome: ⋮ menu).

Monthly update: Add file → Upload files → drag the new index.html → Commit changes.
