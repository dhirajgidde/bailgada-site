# बैलगाडा शर्यत — landing site

A single-page static site that describes the game and lets people download the APK.
Plain HTML/CSS/JS, no build step. Host on **Vercel** (or any static host).

```
bailgada-site/
├── index.html        # the whole landing page
├── vercel.json       # serves the APK with the right download headers
├── assets/
│   ├── hero.png      # hero artwork
│   └── icon.png      # app icon / favicon
│   └── shot*.png     # (optional) phone screenshots you add
└── bailgada.apk      # ← put your signed APK here (see below)
```

## 1. Add your APK
Two options (set the choice in `index.html` → `APK_URL`):

- **Simple** — copy your built APK into this folder and name it `bailgada.apk`:
  ```bash
  cp "/Users/dhirajgidde/bailgada-android/android/app/build/outputs/apk/release/app-release.apk" \
     "/Users/dhirajgidde/bailgada-site/bailgada.apk"
  ```
  Keep `APK_URL = "./bailgada.apk"` (the default).

- **Recommended for big files** — upload the APK to a **GitHub Release** (no size worries, doesn't bloat the deploy) and set `APK_URL` to that release download URL in `index.html`.

> Tip: a **signed release** APK is best for sharing (the debug APK works too, but Android warns more). Build it with `cd bailgada-android/android && ./gradlew assembleRelease`.

## 2. (Optional) Add screenshots
Drop phone PNGs into `assets/` and list them in `index.html` → `SHOTS = ["shot1.png", ...]`. The gallery shows automatically.

## 3. Deploy to Vercel
**Easiest (dashboard):** go to vercel.com → *Add New → Project* → drag this folder in (or import the GitHub repo). Framework preset = **Other**. Deploy.

**CLI:**
```bash
cd /Users/dhirajgidde/bailgada-site
npx vercel        # preview deploy
npx vercel --prod # production
```

That's it — your site goes live at `https://<name>.vercel.app`, with the download button serving `bailgada.apk`.

## Preview locally
```bash
cd /Users/dhirajgidde/bailgada-site && python3 -m http.server 8080
# open http://localhost:8080
```
