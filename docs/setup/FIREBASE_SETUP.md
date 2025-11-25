# Firebase Cloud Sync Setup Guide

This guide explains how the Universal Flashcard App's cloud synchronization works with Firebase Realtime Database.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Firebase Project Details](#firebase-project-details)
- [Database Structure](#database-structure)
- [Security & Encryption](#security--encryption)
- [User Authentication Flow](#user-authentication-flow)
- [Data Synchronization](#data-synchronization)
- [For Developers: Setting Up Your Own Firebase](#for-developers-setting-up-your-own-firebase)
- [Troubleshooting](#troubleshooting)

---

## 🔍 Overview

Universal Flashcard App v3.1 uses **Firebase Realtime Database** for cloud synchronization with:

- ☁️ **Real-time sync** across multiple devices
- 🔒 **End-to-end encryption** (AES-256-GCM)
- 🔐 **Username/password authentication** (no email required)
- 📱 **Multi-device support** with automatic conflict resolution
- 🔄 **Automatic backup** of all vocabulary data

### Key Features

| Feature | Implementation |
|---------|---------------|
| **Database** | Firebase Realtime Database |
| **Authentication** | SHA-256 password hashing |
| **Encryption** | AES-256-GCM client-side |
| **Database Path** | `users-universal/` |
| **Conflict Resolution** | Last-write-wins (timestamp-based) |
| **Offline Support** | LocalStorage fallback |

---

## 🔥 Firebase Project Details

### Project Information

```
Project Name: flashcard-sync-15835
Project ID: flashcard-sync-15835
Database URL: https://flashcard-sync-15835-default-rtdb.europe-west1.firebasedatabase.app/
Region: europe-west1
```

### Firebase Configuration

The app uses the following Firebase configuration (public, safe to share):

```javascript
const firebaseConfig = {
    apiKey: "AIzaSyDHvMOZbLj-hqvdUOXxHPTrv8F0xQXJkV8",
    authDomain: "flashcard-sync-15835.firebaseapp.com",
    databaseURL: "https://flashcard-sync-15835-default-rtdb.europe-west1.firebasedatabase.app",
    projectId: "flashcard-sync-15835",
    storageBucket: "flashcard-sync-15835.firebasestorage.app",
    messagingSenderId: "486124626635",
    appId: "1:486124626635:web:5c6e87c5e9b1b7ce3e5e5b"
};
```

---

## 🗄️ Database Structure

### Path Separation

The Firebase database is organized to separate different apps:

```
flashcard-sync-15835 (Root)
├── users/              ← German Flashcard App
│   └── username/
│       ├── data: "encrypted_vocabulary"
│       ├── passwordHash: "sha256_hash"
│       └── lastModified: timestamp
│
└── users-universal/    ← Universal Flashcard App (THIS APP)
    └── username/
        ├── data: "encrypted_vocabulary"
        ├── passwordHash: "sha256_hash"
        └── lastModified: timestamp
```

### User Data Structure

Each user entry under `users-universal/` contains:

```javascript
{
    "username": {
        "data": "U2FsdGVkX1...",  // AES-256-GCM encrypted vocabulary JSON
        "passwordHash": "5e884898da...",  // SHA-256 hash of password
        "lastModified": 1704067200000  // Unix timestamp (milliseconds)
    }
}
```

### Encrypted Data Format

Before encryption, the vocabulary data is structured as:

```javascript
{
    "flashcards": {
        "filename1.csv": [...flashcard objects...],
        "filename2.csv": [...flashcard objects...]
    },
    "categories": [...category objects...],
    "fileCategories": {...file to category mappings...}
}
```

After encryption with AES-256-GCM:
```
U2FsdGVkX1+abcdef123456789... (encrypted string)
```

---

## 🔒 Security & Encryption

### Password Security

1. **Password Hashing**
   - Algorithm: SHA-256
   - Input: User's password
   - Output: 64-character hex string
   - Usage: User authentication only (NOT for encryption)

```javascript
// Example (simplified)
const passwordHash = await sha256(password);
// Result: "5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8"
```

2. **Password Requirements**
   - Minimum 8 characters
   - Stored only as SHA-256 hash
   - Never transmitted or stored in plaintext

### Data Encryption

1. **Encryption Algorithm**: AES-256-GCM
   - **Key Derivation**: PBKDF2 with 100,000 iterations
   - **Salt**: Random 128-bit salt per encryption
   - **IV (Initialization Vector)**: Random 96-bit per encryption
   - **Authentication**: GCM provides built-in authentication

2. **Encryption Process**
   ```
   User Data → JSON.stringify → AES-256-GCM (with password) → Encrypted String → Firebase
   ```

3. **Decryption Process**
   ```
   Firebase → Encrypted String → AES-256-GCM (with password) → JSON.parse → User Data
   ```

4. **Key Features**
   - ✅ Encryption happens on client (your device)
   - ✅ Only encrypted data sent to Firebase
   - ✅ Firebase never sees plaintext data
   - ✅ Decryption only possible with correct password

---

## 🔐 User Authentication Flow

### Sign Up Process

```mermaid
graph LR
    A[Enter Username/Password] --> B[Validate Input]
    B --> C[Hash Password SHA-256]
    C --> D[Check Username Available]
    D --> E[Encrypt Vocabulary Data]
    E --> F[Upload to Firebase]
    F --> G[Save Session Locally]
```

**Steps:**
1. User enters username and password
2. App validates input (username: alphanumeric, password: 8+ chars)
3. Password hashed with SHA-256
4. Check if username exists in `users-universal/`
5. If available, encrypt vocabulary data with password
6. Upload encrypted data + password hash to Firebase
7. Save session info in localStorage

### Login Process

```mermaid
graph LR
    A[Enter Username/Password] --> B[Hash Password SHA-256]
    B --> C[Fetch User Data from Firebase]
    C --> D[Compare Password Hashes]
    D --> E[Decrypt Vocabulary Data]
    E --> F[Load into App]
    F --> G[Save Session]
```

**Steps:**
1. User enters username and password
2. Password hashed with SHA-256
3. Fetch user data from `users-universal/{username}`
4. Compare hashed password with stored hash
5. If match, decrypt vocabulary data using password
6. Load decrypted data into app
7. Save session for future page loads

### Session Management

- **Session Storage**: `localStorage.cloudSyncSession`
  ```javascript
  {
      username: "john_doe",
      loggedIn: true,
      lastSync: 1704067200000
  }
  ```
- **Auto-Login**: Session checked on page load
- **Logout**: Clears session, preserves cloud data

---

## 🔄 Data Synchronization

### Sync Triggers

Data automatically syncs to Firebase when:

1. ✅ **Flashcard progress changes** (marked as learned/unlearned)
2. ✅ **New CSV file loaded**
3. ✅ **Category created/modified**
4. ✅ **File assigned to category**
5. ✅ **Manual sync requested** (implicit on data change)

### Sync Process

```mermaid
graph TD
    A[Data Changed] --> B[Show ⏳ Syncing]
    B --> C[Collect All Vocabulary Data]
    C --> D[Encrypt with AES-256-GCM]
    D --> E[Add Timestamp]
    E --> F[Upload to Firebase]
    F --> G{Success?}
    G -->|Yes| H[Show ✅ Synced]
    G -->|No| I[Show ❌ Error]
    I --> J[Retry Logic]
```

### Conflict Resolution

**Strategy**: Last-Write-Wins (based on `lastModified` timestamp)

1. **Single User, Multiple Devices**:
   - Most recent change wins
   - Older data overwritten
   - User sees newest data

2. **Simultaneous Edits** (rare):
   - Timestamp determines winner
   - Later timestamp overwrites earlier
   - No merge conflicts

### Sync Status Indicators

| Icon | Status | Meaning | Duration |
|------|--------|---------|----------|
| ✅ | Synced | All changes saved to cloud | Persistent |
| ⏳ | Syncing | Upload in progress | 1-3 seconds |
| ❌ | Error | Sync failed | Until resolved |
| 🔒 | Encrypted | Data encrypted before upload | During sync |

---

## 🛠️ For Developers: Setting Up Your Own Firebase

If you want to host your own instance:

### Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add Project"
3. Enter project name (e.g., "my-flashcard-app")
4. Disable Google Analytics (optional)
5. Click "Create Project"

### Step 2: Enable Realtime Database

1. In Firebase Console, select your project
2. Click "Realtime Database" in left menu
3. Click "Create Database"
4. Select location (e.g., `europe-west1`)
5. Start in **Test Mode** (we'll add security rules next)

### Step 3: Configure Security Rules

Set up Firebase Security Rules to allow access:

```json
{
  "rules": {
    "users-universal": {
      "$username": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

**⚠️ Security Note**: These rules allow public read/write. This is acceptable because:
- Data is encrypted client-side
- Password hash verification happens client-side
- No sensitive data stored in plaintext
- For private instance, add Firebase Authentication

### Step 4: Get Firebase Config

1. Go to Project Settings (gear icon)
2. Scroll to "Your apps"
3. Click "Web" (</> icon)
4. Register app (nickname: "Flashcard Web App")
5. Copy the `firebaseConfig` object

### Step 5: Update App Code

In your `flashcard.html`, replace the Firebase config:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

### Step 6: Test Connection

1. Open `flashcard.html` in browser
2. Open browser console (F12)
3. Try signing up with test account
4. Check Firebase Console → Realtime Database for new user entry

---

## 🔧 Troubleshooting

### Common Issues

#### 1. "Failed to sync data" error

**Causes:**
- No internet connection
- Firebase service down
- Incorrect Firebase config

**Solutions:**
```javascript
// Check network
navigator.onLine // Should be true

// Check Firebase connection in console
firebase.database().ref('.info/connected').on('value', (snap) => {
    console.log('Connected:', snap.val());
});
```

#### 2. "Invalid username or password" on login

**Causes:**
- Wrong password
- Username doesn't exist
- Data corruption

**Solutions:**
- Double-check credentials (case-sensitive)
- Try "Skip Login" to use offline mode
- Create new account if password forgotten

#### 3. Data not syncing across devices

**Causes:**
- Different usernames on each device
- Firebase config mismatch
- Encryption/decryption error

**Solutions:**
- Verify same username used on all devices
- Check browser console for errors
- Clear localStorage and login again

#### 4. "Encryption failed" error

**Causes:**
- Password too weak
- Browser crypto API not available
- Corrupt data

**Solutions:**
```javascript
// Check if Web Crypto API available
console.log('Crypto available:', !!window.crypto.subtle);

// Use 8+ character password
// Enable HTTPS (crypto requires secure context)
```

### Debug Commands

Open browser console (F12) and run:

```javascript
// Check current session
console.log('Session:', localStorage.getItem('cloudSyncSession'));

// Check encrypted data
firebase.database().ref('users-universal/YOUR_USERNAME')
    .once('value')
    .then(snap => console.log('Cloud data:', snap.val()));

// Test encryption/decryption
const testData = {test: "hello"};
encryptData(JSON.stringify(testData), "password123")
    .then(encrypted => {
        console.log('Encrypted:', encrypted);
        return decryptData(encrypted, "password123");
    })
    .then(decrypted => console.log('Decrypted:', decrypted));
```

### Network Debugging

```javascript
// Monitor Firebase connection status
const connectedRef = firebase.database().ref('.info/connected');
connectedRef.on('value', (snap) => {
    if (snap.val() === true) {
        console.log('✅ Connected to Firebase');
    } else {
        console.log('❌ Disconnected from Firebase');
    }
});
```

---

## 🔗 Related Documentation

- [README.md](README.md) - Main documentation
- [USER_GUIDE.md](USER_GUIDE.md) - User guide
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Troubleshooting guide
- [CHANGELOG.md](CHANGELOG.md) - Version history

---

## 📞 Support

For Firebase-specific issues:
- Check [Firebase Status](https://status.firebase.google.com/)
- Review [Firebase Documentation](https://firebase.google.com/docs/database)
- Open an issue on GitHub

---

**Last Updated**: January 2025
**Version**: 3.1
