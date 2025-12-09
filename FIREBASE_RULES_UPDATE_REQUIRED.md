# Firebase Rules Update Required for Settings Feature

## Error:
```
PERMISSION_DENIED: Permission denied at /users-universal/masoud/settings
```

## Solution:
You need to update your Firebase Realtime Database rules to allow writing to the settings path.

## Steps to Fix:

### Option 1: Using Firebase Console (Recommended)

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project
3. Click on **Realtime Database** in the left sidebar
4. Click on the **Rules** tab
5. Replace the existing rules with:

```json
{
  "rules": {
    "users": {
      "$username": {
        ".read": true,
        ".write": true
      }
    },
    "users-universal": {
      "$username": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

6. Click **Publish** button

### Option 2: More Secure Rules (Recommended for Production)

If you want more secure rules that only allow users to write to their own data:

```json
{
  "rules": {
    "users-universal": {
      "$username": {
        ".read": true,
        ".write": "auth != null && auth.uid == $username"
      }
    }
  }
}
```

**Note:** Option 2 requires implementing Firebase Authentication. Since the current app uses custom password hashing, use Option 1 for now.

### After Updating Rules:

1. Wait 10-30 seconds for rules to propagate
2. Refresh your flashcard app
3. Try logging in again
4. Change a setting (e.g., speech rate)
5. You should see a success indicator in the top-right corner

## What This Fixes:

- ✅ Allows users to save their settings to the cloud
- ✅ Allows users to load their settings from the cloud
- ✅ Each user's settings are stored separately at: `users-universal/{username}/settings`
- ✅ Settings include: speech rate, voice selection, autoplay, delays, repeat counts, timers, filter mode

## Verification:

After updating the rules, you should see in the browser console:
```
✅ User settings saved to cloud
```

Instead of:
```
❌ Error saving user settings: Error: PERMISSION_DENIED
```
