# Recipe Circle — Android recipe discovery and sharing app

Features: recipes from TheMealDB, search, categories, ingredient lists, instructions, YouTube video links, local favorites, locally authored recipes with optional photos, responsive mobile UI.

## Android APK via GitHub (recommended)
1. Create a new GitHub repository and upload all files in this project, including `.github/workflows/build-apk.yml`.
2. Open GitHub **Actions** > **Build Android APK** > **Run workflow**.
3. When the workflow completes, download the `recipe-circle-debug-apk` artifact.
4. Unzip the artifact to obtain `app-debug.apk` and install it on your Android phone. Android may require allowing installation from that source.

## Local build (requires Node.js, JDK 21 and Android SDK)
```
npm install
npm run build
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```
APK: `android/app/build/outputs/apk/debug/app-debug.apk`.

## Browser preview
```
npm install
npm start
```
Open the URL printed by Vite. For Android changes run `npm run android:sync` before rebuilding.

## Important limitations
- TheMealDB public test key `1` is included for development/personal testing. Production app-store publication requires a supporter key per TheMealDB's terms.
- Recipes and photos are loaded from TheMealDB over the internet; they are not copied from Google Search.
- User-created recipes and favorites are stored **on the current device only** using localStorage. To support real multi-user sharing, authentication, moderation, cloud image storage and a backend database must be added.
- This package includes APK build automation, **not a precompiled APK**. The Android toolchain is not available in this environment, so compilation has not been verified here.
