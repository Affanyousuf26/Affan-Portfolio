# Affan Yousuf Siddiqui — Portfolio

A single-page, scrollable portfolio site (Flutter Developer / Mobile Systems Engineer), styled as a UAV ground-control telemetry HUD in black/red.

## Files
```
index.html        → the whole site (HTML + CSS + JS in one file)
images/affan.jpg   → your photo, used in the hero "ID card"
```

## Host it free on GitHub Pages

1. Go to https://github.com/new and create a repo (e.g. `portfolio` or `affan-portfolio`). Keep it **Public**.
2. On your computer, put `index.html` and the `images` folder (with `affan.jpg` inside) in that repo folder.
3. Push it to GitHub:
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin https://github.com/Affanyousuf26/YOUR-REPO-NAME.git
   git push -u origin main
   ```
   (Or just drag-and-drop both `index.html` and the `images` folder into the repo via the GitHub web UI → "Add file" → "Upload files".)
4. In the repo, go to **Settings → Pages**.
5. Under "Build and deployment" → **Source**, choose **Deploy from a branch**.
6. Branch: `main`, folder: `/ (root)` → **Save**.
7. Wait ~1 minute, then GitHub will show your live URL, typically:
   ```
   https://affanyousuf26.github.io/YOUR-REPO-NAME/
   ```

That's it — no server, build step, or backend needed. Anyone with the link can view it.

## Making changes later
Just edit `index.html` directly (it's plain HTML/CSS/JS, no build tools), commit, and push — GitHub Pages redeploys automatically in under a minute.
