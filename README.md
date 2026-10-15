# Server Slides for Android

One Grafana server per slide, Slack-style channels, a 3D globe, and RAM/CPU alerts, as an Android app.

## Get the APK without installing anything (recommended)

1. Create a free account at https://github.com and click **New repository** (name it `server-slides`, keep it **Private**).
2. On the new repository page click **uploading an existing file**, then drag in **everything inside this folder**
   (including the hidden `.github` folder; on Windows turn on "Show hidden items" in File Explorer first). Click **Commit changes**.
3. Open the **Actions** tab. A build called **Build Android APK** starts by itself (about 5–8 minutes).
   If it doesn't start, click **Build Android APK → Run workflow**.
4. When it shows a green tick, open it and download **ServerSlides-APK** at the bottom. Unzip it to get **ServerSlides.apk**.

## Install on the phone

1. Copy `ServerSlides.apk` to the phone (WhatsApp to yourself, Google Drive, USB cable, or email).
2. Tap it. Android asks to allow installing apps from that source: tap **Settings → Allow**, then **Install**.
3. If Play Protect warns about an unknown developer, tap **More details → Install anyway**.

## Build on your own computer instead

Needs Android Studio (includes Java and the Android SDK) and Node.js 18+.

```
npm install
npx cap sync android
npx cap open android      # opens Android Studio: Build > Build APK(s)
```
or from a terminal: `cd android && ./gradlew assembleDebug`. The APK is in `android/app/build/outputs/apk/debug/`.

## Notes

- The phone must be on the company network or VPN to reach Grafana.
- App accounts are stored on the phone. Grafana passwords are encrypted on the phone.
- RAM/CPU alerts arrive as phone notifications while the app is open or in the background recently.
  For alerts at any time (phone locked, app closed), also set up Grafana's own alerting.
- Grafana dashboards appear inside the slides without changing any Grafana settings. The app loads
  from `slides.thelocal.co.in` internally so Grafana servers on `*.thelocal.co.in` keep you logged in.
  If your Grafana servers use another domain, change `server.hostname` in `capacitor.config.json`
  to a name under that domain and rebuild.
- This is a debug-signed APK, fine for installing on your own phones. Publishing on Google Play needs a release signing key.
