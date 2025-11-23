# Changelog - Universal Flashcard App

All notable changes to the Universal Flashcard App will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [3.1.0] - 2025-01-23

### 🎉 Major Release: Cloud Synchronization

This release introduces comprehensive cloud synchronization with Firebase, enabling multi-device access and automatic backup of all vocabulary data.

### ☁️ Added - Cloud Sync Features

- **Firebase Integration**: Real-time database synchronization across devices
- **User Authentication**: Username/password authentication system (no email required)
- **End-to-End Encryption**: AES-256-GCM client-side encryption before data upload
- **Account Management System**:
  - Sign up with username and password
  - Login/logout functionality
  - Change password (with automatic re-encryption)
  - Delete account (permanent, with confirmation)
- **Sync Status Indicators**: Visual feedback (✅ Synced, ⏳ Syncing, ❌ Error)
- **Offline Mode**: Optional "Skip Login" button for local-only usage
- **Multi-Device Support**: Access vocabulary from any device with login credentials
- **Automatic Backup**: Every change automatically synced to cloud
- **Login Modal**: Appears on app launch with Sign Up/Login/Skip options

### 🔒 Added - Security Features

- **SHA-256 Password Hashing**: Passwords never stored in plaintext
- **PBKDF2 Key Derivation**: 100,000 iterations for encryption key generation
- **Client-Side Encryption**: Data encrypted on device before upload
- **Secure Database Path**: `users-universal/` separates from other apps
- **Session Management**: localStorage-based session with auto-login
- **Password Validation**: Minimum 8 characters enforced
- **Username Validation**: Alphanumeric with underscore/hyphen only

### 🔄 Changed

- **LocalStorage Wrapper**: Added encryption-aware localStorage wrapper
- **Data Structure**: Vocabulary data now includes encryption metadata
- **Account Button**: New UI element in top-right corner when logged in
- **App Title**: Updated to reflect v3.1 with cloud sync

### 🐛 Fixed

- **Infinite Recursion**: Fixed localStorage wrapper causing stack overflow
- **Session Persistence**: Improved session management across page reloads
- **Error Handling**: Better network error handling and user feedback
- **Sync Race Conditions**: Resolved conflicts with simultaneous data changes

### 📚 Documentation

- Created comprehensive Firebase setup guide (FIREBASE_SETUP.md)
- Added cloud sync section to README.md
- Updated user guide with account management instructions
- Added troubleshooting section for sync issues

---

## [3.0.0] - 2024-12-15

### 🎉 Major Release: Language Auto-Detection System

Complete redesign of language selection with intelligent auto-detection capabilities.

### 🤖 Added - Language Detection

- **Intelligent Auto-Detection**: Automatically analyzes CSV content to detect languages
- **15+ Language Support**: German, English, Spanish, French, Italian, Portuguese, Russian, Japanese, Korean, Chinese, Arabic, Hindi, Dutch, Polish, Turkish, Swedish, Danish, Norwegian, Finnish
- **Pattern Recognition Algorithm**:
  - Special character detection (ä, ö, ü, ñ, ç, à, etc.)
  - Common word matching (der, the, el, le, etc.)
  - Script detection (Latin, Cyrillic, Arabic, Hangul, Kanji/Kana, Chinese)
  - Scoring system for accurate language identification
- **Visual Detection Indicators**:
  - ✓ Green checkmark for auto-detected languages
  - 📝 Blue pencil for manually selected languages
- **Manual Override**: Easy dropdown selection if detection incorrect
- **Real-time Voice Updates**: Voices reload when language changed

### 🎨 Changed - UI/UX Improvements

- **Step-by-Step Workflow**: Clear "Step 1: Select Languages" → "Step 2: Choose Format"
- **Enhanced Language Selector**:
  - Prominent green gradient design
  - Centered layout with clear instructions
  - Dynamic labels showing detection status
  - Success message on detection completion
- **Better Labeling**: Labels update based on selection method
- **Improved Column Mapping**: Modal popup with visual preview table

### 🔄 Changed - Technical Improvements

- Refactored `detectLanguage()` function with multi-language support
- Added `detectLanguages()` for dual-column detection
- Improved CSV parsing with language analysis
- Enhanced voice selection based on detected language
- Better error handling for unsupported languages

### 🐛 Fixed

- Language selector visibility issues after file upload
- Voice selection logic for detected languages
- Label updating mechanism inconsistencies
- Column mapping modal display issues

### 📚 Documentation

- Added Language Auto-Detection section to README
- Updated CSV format examples
- Created language detection troubleshooting guide
- Added visual indicators explanation

---

## [2.4.0] - 2024-11-10

### ✨ Added - Enhanced Voice System

- **Premium Google Voices**: High-quality natural pronunciation
  - Added 🔊 indicator for Google voices
  - Priority selection for supported languages
- **Microsoft Voices**: High-quality voices for Windows/Edge
  - Added 🎙️ indicator for Microsoft voices
  - Excellent clarity and enunciation
- **Voice Quality Indicators**: Visual icons show voice type
- **Enhanced Voice Information**: Detailed voice names and language codes
- **Improved Voice Selection UI**: Better organized dropdowns with quality indicators

### 🔄 Changed

- Voice selection prioritizes quality: Google > Microsoft > System
- Voice dropdowns now show provider icons
- Better voice availability detection

---

## [2.3.0] - 2024-10-05

### ✨ Added - Advanced Learning Features

- **Session Recording**: Record entire study session audio
  - MediaRecorder API integration
  - Download as .webm audio file
  - Review pronunciation later
- **Study Timer**: Set study duration (5-60 minutes)
  - Visual countdown display
  - Auto-stops when time expires
  - Session statistics preserved
- **Sleep Timer**: Set bedtime learning duration (10-45 minutes)
  - Perfect for passive learning before sleep
  - Auto-stops to prevent overnight playback
- **Loop Mode**: Restart from beginning when reaching end
  - Continuous review sessions
  - Toggle on/off easily
- **Repeat Mode**: Repeat each card 2-5 times before moving on
  - Intensive memorization
  - Configurable repeat count
- **Focus Mode**: Distraction-free full-screen learning
  - Minimal UI
  - Centered flashcard display
  - Press Esc to exit
- **Session Statistics**: Real-time tracking during auto-play
  - Cards reviewed
  - Time studying
  - Cards per minute
  - Session start time
- **Extended Content Toggle**: Option to read or skip example sentences

### 🔄 Changed

- Enhanced auto-play controls with more granular settings
- Improved audio timing with event-driven callbacks
- Better session state management

---

## [2.1.0] - 2024-08-20

### ✨ Added - Format Selection System

- **Three Format Selection Methods**:
  1. **Predefined Formats**: Quick selection for common formats
     - 2-column, 3-column, 4-column options
     - Fastest loading method
  2. **Manual Column Mapping**: Click-to-assign column types
     - Interactive modal with preview table
     - Visual column type assignment
     - Flexible for custom formats
  3. **Auto-Detection**: Intelligent format recognition
     - Analyzes CSV structure
     - Selects best format automatically
     - Fallback if detection uncertain

### 🎨 Changed - UI Improvements

- Added format selection buttons with clear descriptions
- Created modal popup for manual column mapping
- Improved visual feedback during format selection
- Better error messages for format issues

### 🐛 Fixed

- CSV parsing edge cases with varied formats
- Column mapping persistence issues
- Format detection false positives

---

## [2.0.0] - 2024-07-01

### ✨ Added - Major Features

- **Spaced Repetition (SM-2 Algorithm)**:
  - Intelligent scheduling based on recall performance
  - Ease factor calculation
  - Automatic review intervals
  - Long-term retention optimization
- **Category Management System**:
  - Create custom categories and subcategories
  - Assign CSV files to categories
  - View all categories with file counts
  - Organize vocabulary by topic/level
- **Auto-Play Mode**:
  - Automated flashcard review
  - Customizable delays and settings
  - Hands-free learning
  - Pronunciation integration

### 🔄 Changed

- Complete UI redesign with modern gradient styling
- Improved mobile responsiveness
- Better keyboard shortcut handling
- Enhanced progress tracking

---

## [1.5.0] - 2024-05-15

### ✨ Added

- **Voice Settings**:
  - Speech rate adjustment (0.5x - 1.5x)
  - Pitch adjustment (0.5 - 2.0)
  - Voice selection per language
- **Extended Content Support**:
  - Source and target example sentences
  - Hidden until revealed for better learning
- **Progress Filtering**: "Show Only Unlearned Cards" toggle

### 🐛 Fixed

- Voice selection persistence
- Audio playback interruption issues
- Progress saving inconsistencies

---

## [1.0.0] - 2024-03-01

### 🎉 Initial Release

### ✨ Features

- **Core Flashcard Functionality**:
  - CSV file upload support
  - Basic navigation (previous/next)
  - Show/hide translation
  - Card counter and progress indicator
- **CSV Format Support**:
  - Automatic separator detection (comma, semicolon, tab, pipe)
  - 2-column, 3-column, 4-column formats
- **Speech Synthesis**:
  - Text-to-speech pronunciation
  - Automatic voice selection
  - Keyboard shortcuts (P for source, E for target)
- **Progress Tracking**:
  - Mark cards as learned/unlearned
  - LocalStorage persistence
  - Progress preserved across sessions
- **Keyboard Shortcuts**:
  - Arrow keys for navigation
  - Space/Enter to reveal
  - P/E for pronunciation
  - L to mark learned
- **Basic Language Support**:
  - Manual language selection
  - German, English, Spanish, French, Italian
- **LocalStorage Persistence**:
  - Save flashcard progress
  - Remember last loaded file
  - Persist settings

### 🎨 UI Features

- Clean, modern interface
- Responsive design
- Mobile-friendly layout
- Gradient backgrounds
- Smooth animations

---

## Version History Summary

| Version | Release Date | Key Feature | Status |
|---------|-------------|-------------|--------|
| **3.1.0** | 2025-01-23 | ☁️ Cloud Sync | Current |
| **3.0.0** | 2024-12-15 | 🤖 Language Auto-Detection | Previous |
| **2.4.0** | 2024-11-10 | 🎙️ Enhanced Voices | Previous |
| **2.3.0** | 2024-10-05 | 📹 Session Recording | Previous |
| **2.1.0** | 2024-08-20 | 📋 Format Selection | Previous |
| **2.0.0** | 2024-07-01 | 🔄 Spaced Repetition | Previous |
| **1.5.0** | 2024-05-15 | 🎚️ Voice Settings | Previous |
| **1.0.0** | 2024-03-01 | 🎉 Initial Release | Previous |

---

## Planned Features (Roadmap)

### Version 3.2 (Future)

- **Collaborative Learning**:
  - Share vocabulary decks with other users
  - Import community-created decks
  - Deck ratings and reviews

- **Advanced Analytics**:
  - Learning progress charts
  - Word difficulty analysis
  - Study time heatmaps
  - Retention rate tracking

- **Enhanced Mobile Support**:
  - Progressive Web App (PWA)
  - Offline-first architecture
  - Install to home screen
  - Push notifications for review reminders

### Version 3.3 (Future)

- **AI-Powered Features**:
  - AI-generated example sentences
  - Pronunciation feedback
  - Difficulty estimation
  - Smart review scheduling

- **Gamification**:
  - Streaks and achievements
  - Daily goals and challenges
  - Leaderboards (optional)
  - XP and levels

- **Extended Import/Export**:
  - Anki deck import
  - Quizlet integration
  - JSON export format
  - Backup/restore system

---

## Migration Guides

### Migrating from v3.0 to v3.1

**New Users:**
- Create account on first launch
- All data automatically synced

**Existing Users (Local Only):**
1. Open app with v3.0 data in browser
2. Click "Sign Up" in v3.1
3. Data automatically uploaded during signup
4. Login on other devices to access

**No Breaking Changes:**
- All v3.0 features still work
- Local storage preserved
- Can use "Skip Login" for offline mode

### Migrating from v2.x to v3.0

**Breaking Changes:**
- Language selection now required after CSV upload
- Old format detection replaced with new system

**Migration Steps:**
1. Upload CSV as before
2. Verify auto-detected languages (new feature)
3. Manually adjust if needed
4. Load flashcards (same as before)

**Data Compatibility:**
- All saved progress preserved
- Categories unchanged
- Settings maintained

---

## Deprecation Notices

### v3.1
- None

### v3.0
- **Old language detection**: Replaced with new multi-language system
- **Automatic format loading**: Now requires explicit format selection

---

## License

This project is open source and available for personal and educational use.

**Author**: Masoud Sadeghi
**Repository**: [Universal-Flashcard-App-Public](https://github.com/MasoudSade/Universal-Flashcard-App-Public)

---

## Links

- [README.md](README.md) - Main documentation
- [USER_GUIDE.md](USER_GUIDE.md) - Complete user guide
- [QUICK_START.md](QUICK_START.md) - Quick start guide
- [FIREBASE_SETUP.md](FIREBASE_SETUP.md) - Cloud sync setup
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Problem solving

---

**Last Updated**: January 2025
