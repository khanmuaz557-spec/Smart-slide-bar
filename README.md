# Crema Studio – Glassy SideBar V7 (app packages)

## 1) pwa/  — installable web app (easiest)
1. Upload the *contents* of `pwa/` to any HTTPS host (Netlify, Vercel, GitHub Pages, Cloudflare Pages).
2. Open the URL on your phone (Chrome/Android or Safari/iOS).
3. Android: menu -> "Install app". iOS: Share -> "Add to Home Screen".
After the first online load the app also opens offline (service worker caches the page and the Tailwind/icon CDN files).
Note: service workers do not run from file:// — it must be served over HTTPS (or localhost).

## 2) capacitor/ — native Android / iOS project
Requires Node.js 18+, Android Studio (Android) or Xcode on a Mac (iOS).
    cd capacitor
    npm install
    npm run android      # or: npm run ios
Build the APK/AAB from Android Studio (Build > Build Bundle(s) / APK(s)).
Native permissions (camera, location, notifications) must be declared in AndroidManifest.xml / Info.plist
after `cap add`.

## Backend
The shared database, live presence and Claude replies only exist inside the Claude-hosted artifact.
Outside it the app runs in demo mode (local data). To get a real shared backend, replace the
`dbh`/`convs`/`projects` code with Firebase or Supabase calls and add login.
