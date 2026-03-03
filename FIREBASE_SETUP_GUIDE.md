# 🔥 Firebase Setup Guide - Step by Step

## Prerequisites
- Google account
- Android Studio installed
- Flutter project ready

## Step 1: Create Firebase Project

1. **Go to Firebase Console**
   - Visit: https://console.firebase.google.com/
   - Sign in with your Google account

2. **Create New Project**
   - Click "Add project" or "Create a project"
   - Enter project name: `RoadEase` (or any name you prefer)
   - Click "Continue"

3. **Configure Google Analytics** (Optional but recommended)
   - Choose to enable or disable Google Analytics
   - Select or create an Analytics account
   - Click "Create project"

4. **Wait for project creation** (takes a few seconds)
   - Click "Continue" when done

## Step 2: Add Android App to Firebase

1. **In Firebase Console**
   - Click the Android icon (or "Add app" → Android)
   - Or click the gear icon → Project settings → Add app

2. **Register Android App**
   - **Android package name**: `com.example.roadease`
     - ⚠️ **IMPORTANT**: This must match exactly with your `android/app/build.gradle.kts` file
     - Check line 30 in `android/app/build.gradle.kts`: `applicationId = "com.example.roadease"`
   
   - **App nickname** (optional): `RoadEase Android`
   
   - **Debug signing certificate SHA-1** (optional for now):
     - You can skip this for development
     - For production, you'll need to add it

3. **Click "Register app"**

## Step 3: Download google-services.json

1. **Download the file**
   - Firebase will show a "Download google-services.json" button
   - Click to download

2. **Place the file**
   - Copy the downloaded `google-services.json` file
   - Paste it into: `android/app/google-services.json`
   - ⚠️ **IMPORTANT**: It must be in `android/app/` folder, NOT in `android/` folder

## Step 4: Enable Firebase Services

### Enable Authentication
1. In Firebase Console, go to **Build** → **Authentication**
2. Click **Get started**
3. Enable **Email/Password** sign-in method:
   - Click on "Email/Password"
   - Toggle "Enable"
   - Click "Save"

### Enable Cloud Storage
1. Go to **Build** → **Storage**
2. Click **Get started**
3. Choose **Start in test mode** (for development)
4. Select a location (choose closest to your users)
5. Click "Done"

### Enable Cloud Messaging (FCM)
1. Go to **Build** → **Cloud Messaging**
2. It's automatically enabled when you add an Android app

### Enable Cloud Firestore (Optional - if you want to use it)
1. Go to **Build** → **Firestore Database**
2. Click **Create database**
3. Choose **Start in test mode** (for development)
4. Select a location
5. Click "Enable"

## Step 5: Verify Setup

1. **Check file location**
   ```
   android/app/google-services.json  ✅ Should exist
   ```

2. **Check build.gradle.kts**
   - `android/build.gradle.kts` should have Google Services classpath ✅
   - `android/app/build.gradle.kts` should apply the plugin ✅

3. **Rebuild the app**
   - In Android Studio: `Build → Clean Project`
   - Then: `Build → Rebuild Project`
   - Or run: `flutter clean && flutter pub get`

## Step 6: Test Firebase Connection

1. **Run the app**
   - Click Run (▶️) in Android Studio
   - Check the console/logcat for any Firebase errors

2. **Expected behavior**
   - App should start without Firebase errors
   - You should see Firebase initialization messages in logs

## Troubleshooting

### Error: "Failed to load FirebaseOptions"
- ✅ Make sure `google-services.json` is in `android/app/` (not `android/`)
- ✅ Check that package name matches: `com.example.roadease`
- ✅ Clean and rebuild: `Build → Clean Project` then `Rebuild Project`

### Error: "Plugin with id 'com.google.gms.google-services' not found"
- ✅ Make sure `android/build.gradle.kts` has the buildscript with classpath
- ✅ Sync Gradle files: `File → Sync Project with Gradle Files`

### Error: "google-services.json not found"
- ✅ Download the file again from Firebase Console
- ✅ Place it exactly in `android/app/google-services.json`
- ✅ Check file name is exactly `google-services.json` (not `google-services.json.txt`)

## Next Steps After Setup

1. **Test Authentication**
   - Try registering a new user
   - Try logging in

2. **Test Image Upload**
   - Try uploading a profile picture
   - Check Firebase Storage console

3. **Test Notifications**
   - Send a test notification from Firebase Console
   - Go to Cloud Messaging → Send test message

## Important Notes

- ⚠️ **Package Name**: If you change the package name in `build.gradle.kts`, you must update it in Firebase Console too
- ⚠️ **SHA-1**: For production, you'll need to add your app's SHA-1 certificate
- ⚠️ **Security Rules**: Update Firestore and Storage security rules before production

## Need Help?

- Firebase Documentation: https://firebase.google.com/docs
- FlutterFire Documentation: https://firebase.flutter.dev/

