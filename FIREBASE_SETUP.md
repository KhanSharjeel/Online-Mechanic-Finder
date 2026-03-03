# Firebase Setup Instructions

## Current Status
The app is configured to work **without Firebase** for now. Firebase features will be disabled until you complete the setup below.

## To Enable Firebase Features

### Step 1: Create Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or select an existing project
3. Follow the setup wizard

### Step 2: Add Android App to Firebase
1. In Firebase Console, click the Android icon (or "Add app")
2. Enter package name: `com.example.roadease`
3. Register the app
4. Download `google-services.json`

### Step 3: Add google-services.json
1. Place the downloaded `google-services.json` file in:
   ```
   android/app/google-services.json
   ```

### Step 4: Rebuild the App
1. In Android Studio: `Build → Clean Project`
2. Then: `Build → Rebuild Project`
3. Run the app again

## What Firebase Features Are Used
- **Firebase Authentication** - User login/registration
- **Firebase Storage** - Profile and shop image uploads
- **Firebase Cloud Messaging (FCM)** - Push notifications
- **Cloud Firestore** - Database (optional, can use SQL backend instead)

## Note
The app will work without Firebase, but authentication and image upload features will need the backend API to handle them differently.

