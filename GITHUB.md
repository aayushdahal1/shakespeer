# Putting shakespeer on GitHub Pages

Two ways. The first needs no git.

## A. Straight through the website

1. **github.com/new** — name it `shakespeer`, set it **Public**, don't tick
   "Add a README". Create.
2. On the empty repo page click **uploading an existing file**.
3. Drag in *the files from inside this folder* — `index.html`, `sw.js`,
   `manifest.webmanifest`, `.nojekyll` and the four icons. Not the folder
   itself: `index.html` has to sit at the top level of the repo.
   > `.nojekyll` may be hidden in your file browser. On macOS press
   > **Cmd + Shift + .** in the file dialog to show it.
4. **Commit changes**.
5. **Settings → Pages**. Source: *Deploy from a branch*. Branch: `main`,
   folder `/ (root)`. **Save**.
6. Wait a minute or two, then reload that page — the URL appears at the top:

   `https://<your-username>.github.io/shakespeer/`

That link is what you send your friends. Anyone can open it, no account needed.

## B. With git

```bash
cd shakespeer-site
git init -b main
git add .
git commit -m "shakespeer"
git remote add origin https://github.com/<your-username>/shakespeer.git
git push -u origin main
```

Then do step 5 above.

## Updating it later

Replace `index.html` and commit again. Pages redeploys in about a minute.

One catch: the app caches itself for offline use, so a friend who already
opened it may keep seeing the old version until they reload twice. If you
change it, bump `CACHE = "shakespeer-v1"` in `sw.js` to `v2` and everyone
gets the new one on their next visit.

## A domain of your own

Buy one anywhere, then Settings → Pages → Custom domain. GitHub gives you
the DNS records to paste at your registrar, and issues the HTTPS certificate
itself. The `github.io` address keeps working.

## What your friends get

A real site: installable, works offline after the first visit, and their
scripts are stored in their own browser. Nothing is uploaded anywhere and
there is no account — which also means a script written on a laptop will not
show up on a phone.
