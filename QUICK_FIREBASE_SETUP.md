# 🚀 Quick Firebase Setup (5 Minutes)

## ⚠️ Current Status
Your app is running but Firebase is not configured yet. Follow these steps to enable Firebase.

## 📋 Step-by-Step Instructions

### Step 1: Create Firebase Project (2 minutes)
1. Go to: **https://console.firebase.google.com/**
2. Click **"Add project"** or **"Create a project"**
3. Enter project name: `RoadEase` (or any name)
4. Click **Continue** → **Continue** → **Create project**
5. Wait for project creation → Click **Continue**

### Step 2: Add Android App (1 minute)
1. In Firebase Console, click the **Android icon** (📱)
2. Enter these details:
   - **Android package name**: `com.example.roadease`
   - **App nickname** (optional): `RoadEase`
   - **Debug signing certificate SHA-1**: Skip for now
3. Click **"Register app"**

### Step 3: Download Configuration File (30 seconds)
1. Click **"Download google-services.json"**
2. **IMPORTANT**: Save this file to:
   ```
   C:\Users\malix\OM\android\app\google-services.json
   ```
   ⚠️ Make sure it's in `android/app/` folder, NOT `android/` folder!

### Step 4: Enable Required Services (1 minute)

#### Enable Authentication:
1. In Firebase Console, go to **Build** → **Authentication**
2. Click **"Get started"**
3. Click on **"Email/Password"**
4. Toggle **"Enable"** → Click **"Save"**

#### Enable Storage:
1. Go to **Build** → **Storage**
2. Click **"Get started"**
3. Choose **"Start in test mode"**
4. Select location → Click **"Done"**

### Step 5: Rebuild App (30 seconds)
1. In Android Studio: **Build** → **Clean Project**
2. Then: **Build** → **Rebuild Project**
3. Or: **File** → **Sync Project with Gradle Files**
4. Click **Run** (▶️) again

## ✅ Verification

After adding `google-services.json` and rebuilding, you should see:
- ✅ No Firebase errors in console
- ✅ App runs normally
- ✅ Firebase features work

## 🔍 Check File Location

Make sure the file is here:
```
android/
  └── app/
      └── google-services.json  ← Should be here
```

## 🆘 Still Getting Errors?

1. **Check file name**: Must be exactly `google-services.json` (not `.txt`)
2. **Check location**: Must be in `android/app/` folder
3. **Check package name**: Must match `com.example.roadease` in Firebase
4. **Clean & Rebuild**: Always clean before rebuilding
5. **Restart Android Studio**: Sometimes helps

## 📞 Need Help?

- Firebase Console: https://console.firebase.google.com/
- Check `FIREBASE_SETUP_GUIDE.md` for detailed instructions

