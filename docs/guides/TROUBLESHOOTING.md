# Troubleshooting Guide - Universal Flashcard App

Solutions to common problems and error messages

---

## 📋 Table of Contents

- [Quick Diagnostics](#quick-diagnostics)
- [CSV File Issues](#csv-file-issues)
- [Cloud Sync Problems](#cloud-sync-problems)
- [Voice & Pronunciation Issues](#voice--pronunciation-issues)
- [Language Detection Problems](#language-detection-problems)
- [Performance Issues](#performance-issues)
- [Browser Compatibility](#browser-compatibility)
- [Data Loss & Recovery](#data-loss--recovery)
- [Error Messages](#error-messages)
- [Advanced Debugging](#advanced-debugging)

---

## 🔍 Quick Diagnostics

Before diving into specific issues, run these quick checks:

### Basic Health Check

1. **Open Browser Console** (Press F12)
2. **Check for Errors** (red messages)
3. **Verify Browser** (Chrome 90+, Edge 90+, Safari 14+, Firefox 88+)
4. **Check Internet** (for cloud sync features)
5. **Clear Cache** (Ctrl+Shift+Del → Clear cache)

### Quick Fixes (Try These First)

```
✅ Reload the page (Ctrl+R or F5)
✅ Clear browser cache
✅ Try in incognito/private mode
✅ Restart browser
✅ Try different browser
✅ Check console for errors (F12)
```

---

## 📄 CSV File Issues

### Problem: "CSV file won't load"

#### Symptom
- Click "Choose File" but nothing happens
- File selected but flashcards don't appear
- Error message: "Failed to parse CSV"

#### Causes & Solutions

**Cause 1: Unsupported Separator**
```
❌ Wrong: Using obscure separators like @ or #
✅ Right: Use comma (,), semicolon (;), tab, or pipe (|)

Example fix:
Word@Translation  →  Word,Translation
Hola@Hello            Hola,Hello
```

**Cause 2: File Encoding Issues**
```
❌ Wrong: ANSI, Windows-1252, or other encodings
✅ Right: UTF-8 encoding

How to fix:
1. Open CSV in text editor (Notepad++, VS Code)
2. Save As → Encoding: UTF-8
3. Reload in flashcard app
```

**Cause 3: Empty Rows or Columns**
```
❌ Wrong:
Word,Translation
Hola,Hello

Adiós,Goodbye  ← Empty row between

✅ Right:
Word,Translation
Hola,Hello
Adiós,Goodbye
```

**Cause 4: Special Characters in Headers**
```
❌ Wrong: "Word (German)",Translation
✅ Right: Word,Translation

Or use manual column mapping
```

### Problem: "Wrong columns loaded"

#### Symptom
- Translation shows where word should be
- Examples missing or in wrong place

#### Solution: Use Manual Column Mapping

```
1. Upload CSV
2. Click "Select Columns Manually"
3. In modal, click each column header to assign:
   🌍 Source Word
   📝 Source Example
   🎯 Target Word
   📖 Target Example
   🚫 Ignore
4. Click "Apply Mapping"
```

### Problem: "Special characters display as �"

#### Cause
File not saved as UTF-8

#### Solution
```
In Excel:
1. File → Save As
2. Format: CSV UTF-8 (Comma delimited) (.csv)
3. Save

In Google Sheets:
1. File → Download → Comma Separated Values (.csv)
2. Already UTF-8 by default

In Notepad++:
1. Encoding → Convert to UTF-8
2. File → Save
```

---

## ☁️ Cloud Sync Problems

### Problem: "Failed to sync data"

#### Symptom
- ❌ Red error icon in top-right
- Changes not saving to cloud
- Can't access data on other devices

#### Causes & Solutions

**Cause 1: No Internet Connection**
```
Check:
- WiFi/Ethernet connected
- Can access other websites
- Firebase status: https://status.firebase.google.com/

Fix:
- Reconnect to internet
- Changes will auto-sync when connection restored
- Data saved locally in meantime
```

**Cause 2: Firebase Service Down**
```
Check: https://status.firebase.google.com/

If down:
- Wait for service restoration
- Use "Skip Login" for offline mode
- Data preserved locally
```

**Cause 3: Browser Blocking Firebase**
```
Check:
- Console (F12) for CORS errors
- Ad blockers disabled
- Privacy extensions (uBlock, Privacy Badger) disabled

Fix:
- Whitelist firebasedatabase.app domain
- Disable ad blockers temporarily
- Try different browser
```

### Problem: "Invalid username or password"

#### On Sign Up

**Cause 1: Username Already Exists**
```
Error: "Username already taken"

Fix:
- Try different username
- Or login if it's your account
```

**Cause 2: Invalid Username Format**
```
❌ Wrong: "user name" (spaces)
❌ Wrong: "user@email.com" (special chars)
✅ Right: "username123"
✅ Right: "user_name"
✅ Right: "user-name"

Rules: Letters, numbers, underscore, hyphen only
```

**Cause 3: Password Too Short**
```
❌ Wrong: "pass123" (7 chars)
✅ Right: "password123" (8+ chars)

Minimum: 8 characters
```

#### On Login

**Cause 1: Wrong Password**
```
- Passwords are case-sensitive
- Check Caps Lock
- No password recovery (by design for privacy)

If forgotten:
1. Click "Skip Login" for offline mode
2. Or create new account
```

**Cause 2: Username Case Mismatch**
```
- Usernames are case-sensitive
- "JohnDoe" ≠ "johndoe"

Fix: Use exact username from sign-up
```

### Problem: "Data not syncing between devices"

#### Symptom
- Login on Device A: sees vocabulary
- Login on Device B: different or missing vocabulary

#### Causes & Solutions

**Cause 1: Different Usernames**
```
Check: Using same username on all devices

Fix: Verify username in Account button (👤)
```

**Cause 2: Sync Not Completed**
```
Check: Wait for ✅ Synced icon before closing browser

Fix:
1. Make changes
2. Wait for ✅ Synced indicator
3. Then close browser/switch devices
```

**Cause 3: Cached Old Data**
```
Fix:
1. Logout on problematic device
2. Clear browser data (localStorage)
3. Login again
4. Fresh data downloads
```

### Problem: "Cannot delete account"

#### Symptom
- Click "Delete Account" but account still exists
- Error: "Failed to delete"

#### Solution
```
1. Verify password correct (required for security)
2. Check internet connection
3. Wait 5 seconds after clicking "Delete"
4. If persists, open console (F12) for error details
5. Try different browser
```

---

## 🎙️ Voice & Pronunciation Issues

### Problem: "No voices available"

#### Symptom
- Voice dropdowns empty
- Speaker buttons do nothing
- No sound when pressing P or E

#### Causes & Solutions

**Cause 1: Voices Not Loaded Yet**
```
Fix:
1. Wait 2-3 seconds after page load
2. Reload page (F5)
3. Check console: window.speechSynthesis.getVoices()
```

**Cause 2: Browser Doesn't Support Web Speech API**
```
Check Support:
console.log('Speech Synthesis:', !!window.speechSynthesis)

If false:
- Use Chrome 90+ (best support)
- Use Edge 90+
- Update browser to latest version
```

**Cause 3: System Voices Disabled**
```
Windows:
1. Settings → Time & Language → Speech
2. Enable Speech services

Mac:
1. System Preferences → Accessibility → Speech
2. Enable Speak selection

Linux:
- Install espeak: sudo apt install espeak
```

### Problem: "Wrong language pronunciation"

#### Symptom
- Spanish voice speaks German words
- English voice for French text

#### Solution
```
Fix 1: Manual Language Selection
1. Change dropdown to correct language
2. Voices reload automatically

Fix 2: Manual Voice Selection
1. Click "Select Voices" in settings
2. Choose appropriate voice manually
3. Look for voice with correct language code
   Example: "Google Español" for Spanish

Fix 3: Verify CSV Content
- Ensure source column actually contains expected language
- Auto-detection based on content, not filename
```

### Problem: "Voice cuts off mid-sentence"

#### Symptom
- Long sentences stop abruptly
- Only first few words pronounced

#### Solution
```
Fix 1: Reduce Speech Rate
Settings → Speech Rate → 0.8x or slower

Fix 2: Shorten Sentences
- Edit CSV to break long sentences
- Keep under 200 characters

Fix 3: Disable Extended Content
Auto-Play Settings → "Read Extended Content" → OFF

Fix 4: Try Different Voice
- Some voices handle long text better
- Google voices usually best for long content
```

### Problem: "Pronunciation sounds robotic"

#### Symptom
- Unnatural intonation
- Choppy speech
- Mispronounced words

#### Solution
```
Fix 1: Use Premium Voices
Look for:
🔊 Google Voices (best quality)
🎙️ Microsoft Voices (high quality)
Avoid: 🔈 System voices (basic quality)

Fix 2: Adjust Pitch & Rate
Settings:
- Speech Rate: 0.9x - 1.0x (more natural)
- Pitch: 0.9 - 1.1 (closer to human)

Fix 3: Check Text Quality
- Add punctuation to CSV (improves intonation)
- Use proper capitalization
- Spell out abbreviations
```

---

## 🌐 Language Detection Problems

### Problem: "Wrong language detected"

#### Symptom
- App detects Spanish but CSV is French
- Source and target languages swapped

#### Solution (Easy)
```
1. Simply change the dropdown to correct language
2. Label updates to "📝 Manually Selected"
3. Voices reload automatically
4. Detection override remembered
```

### Problem: "Language not detected at all"

#### Symptom
- Dropdowns stay on "Select Language"
- No "✓ Auto-detected" label appears

#### Causes & Solutions

**Cause 1: CSV Too Small**
```
Detection needs 5+ rows

Fix: Add more vocabulary entries
```

**Cause 2: Language Not in Supported List**
```
Supported: German, English, Spanish, French, Italian,
Portuguese, Russian, Japanese, Korean, Chinese, Arabic,
Hindi, Dutch, Polish, Turkish, Swedish, Danish, Norwegian,
Finnish

Fix: Manually select language from dropdown
```

**Cause 3: Mixed Languages in Column**
```
❌ Wrong:
Word
Hello (half English)
Hola (half Spanish)
Bonjour (half French)

✅ Right:
English,Spanish
Hello,Hola
Goodbye,Adiós

Fix: Ensure each column is single language
```

### Problem: "Detection works but wrong voices"

#### Symptom
- Language detected correctly (e.g., German)
- But English voice selected

#### Solution
```
1. Voices may not match detected language
2. Manually select voice:
   Settings → Source Voice → Choose German voice
3. Or reload page (voices reload on startup)
```

---

## ⚡ Performance Issues

### Problem: "App slow with large CSV files"

#### Symptom
- Navigation laggy with 500+ cards
- Loading takes 10+ seconds
- Browser freezes

#### Solutions

**Solution 1: Split Large Files**
```
Instead of:
vocabulary.csv (1000 words)

Use:
vocabulary_part1.csv (250 words)
vocabulary_part2.csv (250 words)
vocabulary_part3.csv (250 words)
vocabulary_part4.csv (250 words)
```

**Solution 2: Disable Features Temporarily**
```
Turn off:
- Auto-play recording
- Extended content display
- Multiple repeat mode
```

**Solution 3: Browser Optimization**
```
1. Close other tabs
2. Disable unnecessary extensions
3. Clear browser cache
4. Use Chrome or Edge (best performance)
```

### Problem: "Auto-play stutters or skips"

#### Symptom
- Cards skip before pronunciation finishes
- Timing inconsistent

#### Solution
```
Fix 1: Increase Delays
Auto-Play Settings:
- Delay Between Languages: 2s → 3s
- Delay Before Next Card: 2s → 3s

Fix 2: Disable Extended Content
- Reduces text-to-speech load

Fix 3: Use Faster Voices
- Google voices fastest
- System voices slowest
```

---

## 🌐 Browser Compatibility

### Recommended Browsers

| Browser | Version | Support | Notes |
|---------|---------|---------|-------|
| **Chrome** | 90+ | ✅ Full | Best performance, voices |
| **Edge** | 90+ | ✅ Full | Excellent on Windows |
| **Safari** | 14+ | ⚠️ Limited | Fewer voices, some issues |
| **Firefox** | 88+ | ⚠️ Limited | Speech API limitations |

### Browser-Specific Issues

#### Safari Issues

**Problem: Voices Don't Load**
```
Fix:
1. Enable JavaScript (should be on by default)
2. Allow audio autoplay:
   Preferences → Websites → Auto-Play → Allow All Auto-Play
3. Try desktop Safari (iOS Safari very limited)
```

**Problem: Cloud Sync Fails**
```
Fix:
1. Disable "Prevent Cross-Site Tracking"
   Preferences → Privacy → Uncheck
2. Allow Firebase domain in exceptions
```

#### Firefox Issues

**Problem: Limited Voice Selection**
```
Issue: Firefox has fewer voices than Chrome

Workaround:
1. Use Chrome for better voice support
2. Or install system voices:
   - Windows: Settings → Speech
   - Mac: System Preferences → Accessibility
```

**Problem: LocalStorage Quota**
```
Firefox limits localStorage to 10MB

Fix:
1. Don't load massive CSV files (1000+ cards)
2. Clear old flashcard data periodically
3. Use cloud sync to free up local storage
```

---

## 💾 Data Loss & Recovery

### Problem: "Lost all my progress after clearing browser data"

#### Prevention
```
✅ Use Cloud Sync (Sign Up)
- Automatic backup
- Multi-device access
- Progress preserved

Or manually backup:
1. Open console (F12)
2. Run: console.log(localStorage)
3. Copy output to text file
4. Save securely
```

#### Recovery (If No Cloud Sync)
```
If recent:
1. Check browser history (may have cached version)
2. Check backup files (if you exported CSV with progress)

If long ago:
❌ Not recoverable without cloud sync
Lesson: Enable cloud sync going forward
```

### Problem: "Accidentally deleted account"

#### Symptom
- Clicked "Delete Account"
- Data gone from cloud

#### Recovery
```
❌ Cannot recover
- Deletion is permanent (security feature)
- No backups kept (privacy feature)

Prevention:
- Export vocabulary before deletion
- Create backup account
- Or use "Logout" instead of "Delete"
```

---

## ⚠️ Error Messages

### "Failed to load flashcards"

**Causes:**
1. CSV format incorrect
2. File corrupted
3. Encoding issue

**Fix:**
```
1. Open CSV in text editor
2. Check for:
   - Consistent separators
   - No binary data
   - UTF-8 encoding
3. Re-save as CSV UTF-8
4. Try loading again
```

### "Encryption failed"

**Causes:**
1. Password issue
2. Browser crypto API unavailable
3. Non-HTTPS context (if using remote server)

**Fix:**
```
1. Use 8+ character password
2. Check: console.log(window.crypto.subtle)
   - Should not be undefined
3. Use HTTPS or localhost
4. Try different browser
```

### "Decryption failed"

**Causes:**
1. Wrong password entered
2. Data corrupted
3. Encryption key mismatch

**Fix:**
```
1. Verify password (case-sensitive)
2. Try "Forgot password" (create new account)
3. Check console for detailed error
4. If data corrupted, no recovery possible
```

### "Storage quota exceeded"

**Cause:**
Browser localStorage limit reached (usually 5-10MB)

**Fix:**
```
1. Delete old flashcard files:
   - Load each file
   - Delete from categories

2. Clear localStorage:
   Console: localStorage.clear()
   (⚠️ Loses all local data)

3. Use cloud sync (offloads storage)
```

---

## 🔧 Advanced Debugging

### Check Browser Console Logs

```javascript
// Open console (F12) and run these commands:

// 1. Check localStorage size
let total = 0;
for (let key in localStorage) {
    total += localStorage[key].length;
}
console.log('LocalStorage used:', (total / 1024).toFixed(2), 'KB');

// 2. Check loaded flashcards
console.log('Flashcards:', window.flashcards);

// 3. Check cloud sync session
console.log('Session:', localStorage.getItem('cloudSyncSession'));

// 4. Check available voices
console.log('Voices:', window.speechSynthesis.getVoices());

// 5. Test Firebase connection
firebase.database().ref('.info/connected').on('value', (snap) => {
    console.log('Firebase connected:', snap.val());
});

// 6. Check encryption support
console.log('Crypto available:', !!window.crypto.subtle);
```

### Test Individual Features

```javascript
// Test language detection
detectLanguage("Guten Tag"); // Should return "de"
detectLanguage("Hello"); // Should return "en"

// Test encryption/decryption
const password = "test1234";
const data = JSON.stringify({test: "data"});
encryptData(data, password)
    .then(encrypted => {
        console.log('Encrypted:', encrypted);
        return decryptData(encrypted, password);
    })
    .then(decrypted => console.log('Decrypted:', decrypted));

// Test voice synthesis
const utterance = new SpeechSynthesisUtterance("Hello world");
utterance.lang = 'en-US';
window.speechSynthesis.speak(utterance);
```

### Export Diagnostic Report

```javascript
// Run in console to get diagnostic info:
const diagnostics = {
    browser: navigator.userAgent,
    localStorageSize: (() => {
        let total = 0;
        for (let key in localStorage) total += localStorage[key].length;
        return `${(total / 1024).toFixed(2)} KB`;
    })(),
    speechSupport: !!window.speechSynthesis,
    cryptoSupport: !!window.crypto.subtle,
    voicesCount: speechSynthesis.getVoices().length,
    cloudSession: localStorage.getItem('cloudSyncSession'),
    flashcardsLoaded: !!window.flashcards
};
console.log('DIAGNOSTICS:', JSON.stringify(diagnostics, null, 2));
```

---

## 📞 Still Having Issues?

### Before Reporting

1. **Try all solutions above**
2. **Check browser console** for errors (F12)
3. **Test in incognito mode** (rules out extensions)
4. **Try different browser** (Chrome recommended)

### Reporting Bugs

Open GitHub issue with:

```
**Browser & Version**: Chrome 120
**Operating System**: Windows 11
**Issue**: Brief description
**Steps to Reproduce**:
1. Step one
2. Step two
3. Step three

**Expected Result**: What should happen
**Actual Result**: What actually happens
**Console Errors**: (paste from F12 console)
**Screenshots**: (if applicable)
```

---

## 🔗 Related Documentation

- [README.md](README.md) - Features overview
- [USER_GUIDE.md](USER_GUIDE.md) - Complete user manual
- [QUICK_START.md](QUICK_START.md) - Getting started
- [FIREBASE_SETUP.md](FIREBASE_SETUP.md) - Cloud sync details
- [CHANGELOG.md](CHANGELOG.md) - Version history

---

**Last Updated**: January 2025
**App Version**: 3.1
**Guide Version**: 1.0
