GATE CSE 2027 Study HQ — App package

WHAT THIS PACKAGE DOES
- Saves study progress automatically in browser storage after changes.
- Keeps a second local recovery snapshot in browser storage.
- Supports JSON export/import for backup and moving data between devices.
- Includes PWA manifest, icon, and service worker for install/offline support.
- Once installed from a secure HTTPS website, the app shell can open offline.

IMPORTANT LIMITS
- Browser storage is tied to the browser + website origin + device. It is not a normal folder that you can browse, and clearing browser/app data can erase it.
- This package does not automatically sync between devices or write files to Downloads in the background. Browsers restrict those actions for privacy/security.
- The previous file opened through a content:// file viewer may use separate storage. Existing progress will only carry over if the same browser storage is available or you import a JSON backup once.
- For proper installation and offline caching, serve the folder from HTTPS or localhost. Opening index.html directly as a file does not enable service-worker/PWA installation.

QUICK INSTALL (ANDROID)
1. Keep this folder together; do not separate index.html, manifest.webmanifest, sw.js, and icon.svg.
2. Upload the contents of this folder to an HTTPS static host (for example, a GitHub Pages site or another static hosting provider).
3. Open the HTTPS site in Chrome on your Android phone.
4. Use the visible Install app button if offered, or Chrome menu (⋮) > Install app / Add to Home screen.
5. Open the installed app. It will auto-save on that device and support offline launch after the first successful load.
6. If needed, use Backup > Export backup once in the old version, then Backup > Import backup in the installed app.

UPDATE THE APP
When replacing the app code with a newer version, keep the same HTTPS site address and scope. Browser storage will remain associated with that origin. The service worker cache version can be bumped when publishing a major update.
