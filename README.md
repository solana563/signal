# SIGNAL — Capacitor build

Native Android wrapper around the SIGNAL live-TV player (`www/index.html`).

## Build the APK

**Option A — GitHub (no local setup):** push this folder to a repo, open *Actions → Build Android APK → Run workflow*, then download `signal-debug-apk` from the run. Install `app-debug.apk` on your phone (allow "install unknown apps").

**Option B — your PC:** needs Node 20+, JDK 21 and Android Studio (SDK 35+).
```
npm install
npm run android      # syncs and opens Android Studio -> press Run
# or from the command line:
npm run apk          # -> android/app/build/outputs/apk/debug/app-debug.apk
```

## After editing the web app
Edit `www/index.html`, then `npx cap sync android` and rebuild.

## What the native shell adds
- `hls.js` bundled locally (works without the CDN).
- Native HTTP (`CapacitorHttp`) so IPTV streams without CORS headers still load.
- Cleartext/mixed content allowed (many IPTV streams are plain `http://`).
- Hardware Back button closes sheets/player, clears search, then exits.
- Dark status bar.

## iOS
On a Mac: `npm i @capacitor/ios && npx cap add ios && npx cap open ios`.

## Release build
Debug APKs are fine for personal use. For Play Store, create a keystore and run `./gradlew bundleRelease` in `android/`, then sign it.
