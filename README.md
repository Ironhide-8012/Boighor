# Boighor (বইঘর) — Mobile-ready EPUB Reader

## Local Windows setup
1. Install Node.js LTS.
2. Open this folder in a terminal.
3. Run `npm install` and `npm run dev`.
4. Visit the URL printed by Vite.

## Android installation through GitHub Pages (recommended)
1. Create a **new public GitHub repository** called `boighor` (or any name).
2. Upload **the contents of this project folder**, including the hidden `.github` folder, to the repository root and commit to branch `main`. The GitHub web upload interface sometimes hides dot-folders; using GitHub Desktop is more reliable.
3. Open GitHub repo **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. Open **Actions**; wait for the 'Deploy Boighor to GitHub Pages' workflow to finish successfully.
5. Open `https://YOUR_USERNAME.github.io/boighor/` (replace username/repository name).
6. On Android Chrome, tap **⋮ → Add to Home screen → Install**. Open the installed app, and import your EPUBs on the phone.

For an existing repository, see `.github/workflows/deploy.yml`. It builds and deploys the app automatically after a push to `main`.

## Custom font upload
In Settings or the reader's **Aa** panel → Typeface → Upload custom font. Import `.ttf`, `.otf`, `.woff`, or `.woff2` (up to 15 MB per font). Fonts are saved locally in IndexedDB and remain available after app restarts. They are **per-device** and not synced across PC and Android. Do not clear site storage or uninstall without backups.

## Important storage details
- The IndexedDB name remains `pathok-v11` for migration compatibility on the **same browser origin**. Old books remain there when installed over the same local URL.
- A **new GitHub Pages URL is a new origin**: its library will start empty. Re-import original EPUBs on your phone.
- Reading backup currently exports positions/marks/bookmarks, **not EPUB files or custom font binaries**.
- Offline app-shell functionality depends on a successful first online load. Browser storage cleanup can delete books and fonts.
- The GitHub workflow deploys a PWA, **not an APK**. A native Android APK would require a separate Capacitor/Android build.
