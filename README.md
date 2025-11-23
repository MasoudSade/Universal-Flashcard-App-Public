# 🌍 Universal Language Flashcards v3.1

**A powerful, multi-language flashcard application with cloud synchronization, intelligent auto-detection, speech synthesis, and advanced learning features.**

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://masoudsade.github.io/Universal-Flashcard-App-Public/flashcard.html)
[![Version](https://img.shields.io/badge/version-3.1-blue)](https://github.com/MasoudSade/Universal-Flashcard-App-Public)

**NEW in v3.1:** ☁️ Cloud synchronization with end-to-end encryption, multi-device support, and automatic backup!

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [New in v3.1](#new-in-v31---cloud-sync)
- [New in v3.0](#new-in-v30)
- [Getting Started](#getting-started)
- [Cloud Sync Setup](#-cloud-sync-setup-v31)
- [CSV File Format](#csv-file-format)
- [Language Auto-Detection](#language-auto-detection)
- [Advanced Features](#advanced-features)
- [Usage Guide](#usage-guide)
- [Technical Details](#technical-details)
- [Browser Compatibility](#browser-compatibility)
- [Changelog](#changelog)
- [Support](#support)

---

## 🎯 Overview

Universal Language Flashcards is a web-based application designed to help you learn any language pair through interactive flashcards. Built with pure HTML, CSS, and JavaScript, it runs entirely in your browser with no server required.

### Why Universal Flashcards?

- **🌐 Any Language Pair**: Learn German ↔ English, Spanish ↔ French, Japanese ↔ English, or any combination
- **🤖 Smart Auto-Detection**: Automatically detects source and target languages from your CSV
- **🎙️ Natural Pronunciation**: Uses Google and Microsoft premium voices for accurate pronunciation
- **📊 Progress Tracking**: Spaced repetition algorithm remembers your progress
- **🔒 Privacy First**: All data stays in your browser - no uploads, no tracking

---

## ✨ Key Features

### 1. **Intelligent Language Auto-Detection**
- Analyzes your CSV content and automatically identifies languages
- Supports 15+ languages: German, English, Spanish, French, Italian, Portuguese, Russian, Japanese, Korean, Chinese, Arabic, Hindi, Dutch, Polish, Turkish, Swedish, Danish, Norwegian, Finnish
- Pre-selects detected languages in dropdowns
- Visual indicators show auto-detected vs. manually selected languages
- Easy manual override if detection is incorrect

### 2. **Flexible CSV Format Support**
Three loading methods:
- **Quick Predefined Formats**: Common formats like 3-column, 4-column, 2-column
- **Manual Column Mapping**: Click-to-assign column types with visual preview
- **Smart Auto-Detection**: AI-powered format detection

### 3. **Premium Voice Synthesis**
- Google Voices (🔊): Premium quality, most natural pronunciation
- Microsoft Voices (🎙️): High quality, clear enunciation
- Adjustable speech rate (0.5x - 1.5x)
- Adjustable pitch (0.5 - 2.0)
- Automatic voice selection based on detected language

### 4. **Advanced Learning Features**
- **Auto-Play Mode**: Automated flashcard review with customizable timing
- **Spaced Repetition**: SM-2 algorithm for optimal learning
- **Progress Tracking**: Mark cards as learned, filter unlearned cards
- **Session Recording**: Record audio of your study sessions
- **Study/Sleep Timers**: Set time limits for study sessions
- **Loop & Repeat Modes**: Customize review patterns
- **Focus Mode**: Distraction-free full-screen learning

### 5. **Category Management**
- Organize flashcards by categories and subcategories
- Assign files to custom categories
- Filter and manage vocabulary collections

---

## 🆕 New in v3.1 - Cloud Sync

### ☁️ Cloud Synchronization Features
- **Multi-Device Access**: Login from any device and access your flashcards
- **Automatic Backup**: Every change automatically synced to cloud
- **End-to-End Encryption**: AES-256-GCM encryption before upload
- **Username/Password Auth**: Simple, secure authentication (no email required)
- **Account Management**: Change password, logout, delete account
- **Offline Mode**: Optional "Skip Login" for local-only usage
- **Sync Status Indicators**: Visual feedback (Synced, Syncing, Error)

### 🔒 Security & Privacy
- **Password Hashing**: SHA-256, never stored in plaintext
- **Client-Side Encryption**: Data encrypted before leaving your device
- **No Personal Data**: Only encrypted vocabulary stored
- **Database Separation**: `users-universal/` path (separate from German app)
- **Privacy First**: No tracking, no analytics, no third-party sharing

### 📱 Account Features
- **Login/Signup Modal**: Appears on first load
- **Account Button**: Top-right corner when logged in
- **Change Password**: Re-encrypts all data with new password
- **Delete Account**: Permanent deletion with confirmation
- **Logout**: Clears session, keeps cloud data

### 🔄 Database Structure
```
Firebase Project: flashcard-sync-15835
├── users/              ← German Flashcard App
└── users-universal/    ← Universal Flashcard App (this app)
    └── username/
        ├── data: "encrypted_vocabulary"
        ├── passwordHash: "sha256_hash"
        └── lastModified: timestamp
```

See [FIREBASE_DATABASE_STRUCTURE.md](FIREBASE_DATABASE_STRUCTURE.md) for complete database documentation.

---

## 🆕 New in v3.0

### Language Auto-Detection System
```
✓ Upload CSV → Auto-detect languages → Pre-select dropdowns
✓ Visual indicators: "✓ German (Auto-detected)" or "📝 Spanish (Manually Selected)"
✓ Smart detection using character patterns and common words
✓ 15+ languages supported
```

### Enhanced UI/UX
- **Step-by-step workflow**: Clear "Step 1: Select Languages" → "Step 2: Choose Format"
- **Prominent language selector**: Bright green gradient with clear instructions
- **Success messages**: Visual confirmation of auto-detection
- **Better labeling**: Dynamic labels update based on selection status

### Technical Improvements
- Multi-language pattern recognition algorithm
- Scoring system for accurate detection
- Improved column mapping with modal popup
- Better error handling and user feedback

---

## ☁️ Cloud Sync Setup (v3.1)

### Getting Started with Cloud Sync

#### First Time Users

1. **Launch the App**
   - Open `flashcard.html` in your browser
   - Login/Signup modal appears automatically

2. **Create Account**
   - Enter a username (letters, numbers, underscore, hyphen only)
   - Create a secure password (8+ characters)
   - Click "Sign Up"

3. **Start Using**
   - Upload your CSV files
   - All changes automatically sync to cloud
   - Watch for sync status: ✅ Synced | ⏳ Syncing | ❌ Error

#### Existing Users

1. **Login**
   - Enter your username and password
   - Click "Login"
   - Your vocabulary loads automatically

2. **Multi-Device Access**
   - Login from any device with same credentials
   - Data stays synchronized across all devices
   - Most recent changes always take priority

#### Offline Mode

- Click "Skip Login" to use app without cloud sync
- All data stored locally in browser
- No account required
- Switch to cloud sync anytime by logging in

### Account Management

Access account features via the Account button (👤) in top-right corner:

- **Change Password**: Enter current password, then new password
  - All data automatically re-encrypted with new password
  - Requires logout and login with new password

- **Logout**: Sign out of current session
  - Local data cleared
  - Cloud data preserved

- **Delete Account**: Permanently remove account and all data
  - Requires password confirmation
  - Cannot be undone
  - All data erased from cloud

### Security Features

- **Password Protection**: SHA-256 hashing, never stored in plaintext
- **End-to-End Encryption**: AES-256-GCM encryption before upload
- **Secure Transport**: HTTPS connection to Firebase
- **Privacy First**: Only encrypted vocabulary stored, no personal info
- **Separate Database**: `users-universal/` path isolates from other apps

### Sync Status Indicators

| Icon | Status | Meaning |
|------|--------|---------|
| ✅ | Synced | All changes saved to cloud |
| ⏳ | Syncing | Upload in progress |
| ❌ | Error | Sync failed (check connection) |
| 🔒 | Encrypted | Data encrypted before upload |

---

## 🚀 Getting Started

### Quick Start

1. **Open the App**
   ```
   Simply open flashcard.html in any modern web browser
   ```

2. **Upload Your CSV File**
   - Click "📁 Choose Vocabulary File"
   - Select your CSV file (comma, semicolon, tab, or pipe-separated)

3. **Language Auto-Detection**
   - App automatically detects your source and target languages
   - Verify the detected languages (shown with ✓)
   - Change if needed - dropdowns update to show manual selection (📝)

4. **Select Format**
   - Choose from predefined formats (fastest)
   - Or use manual column mapping (most flexible)
   - Or let auto-detection handle it

5. **Start Learning!**
   - Navigate with arrow buttons or keyboard (← →)
   - Press Space/Enter to reveal translation
   - Use Auto-Play for hands-free learning
   - Press 'P' for source pronunciation, 'E' for target pronunciation

---

## 📄 CSV File Format

### Supported Separators
✅ Comma (`,`)
✅ Semicolon (`;`)
✅ Pipe (`|`)
✅ Tab

All automatically detected!

### Supported Formats

#### **2-Column Simple**
```csv
Source,Target
Bonjour,Hello
Merci,Thank you
```

#### **3-Column Standard**
```csv
Source,SourceExample,Target
Bonjour,Bonjour mes amis,Hello
Merci,Merci beaucoup,Thank you
```

#### **3-Column Reverse**
```csv
Target,TargetExample,Source
Hello,Hello my friends,Bonjour
Thank you,Thank you very much,Merci
```

#### **4-Column Full**
```csv
Source,SourceExample,Target,TargetExample
Bonjour,Bonjour mes amis,Hello,Hello my friends
Merci,Merci beaucoup,Thank you,Thank you very much
```

### Column Types

- **🌍 Source Word**: Main vocabulary (visible immediately)
- **📝 Source Example**: Extended content/sentence (hidden until revealed)
- **🎯 Target Word**: Main translation (visible when revealed)
- **📖 Target Example**: Extended translation/sentence (hidden until revealed)
- **🚫 Ignore**: Skip this column entirely

---

## 🤖 Language Auto-Detection

### How It Works

1. **CSV Analysis**: Reads first 20 rows of your CSV
2. **Pattern Matching**: Checks for:
   - Special characters (ä, ö, ü, ß for German; á, é, í, ñ for Spanish, etc.)
   - Common words (der, die, das for German; the, a, an for English, etc.)
3. **Scoring Algorithm**: Assigns scores to each language
4. **Best Match**: Selects language with highest score
5. **UI Update**: Pre-selects detected language in dropdown

### Supported Languages

| Language | Detection Features |
|----------|-------------------|
| **German (de)** | ä, ö, ü, ß + der, die, das, ist, sind |
| **English (en)** | the, a, an, is, are, was, were |
| **Spanish (es)** | á, é, í, ó, ú, ñ, ¿, ¡ + el, la, es, son |
| **French (fr)** | à, â, ç, é, è, ê, ë + le, la, est, sont |
| **Italian (it)** | à, è, é, ì, ò, ù + il, la, è, sono |
| **Portuguese (pt)** | ã, õ, ç + o, a, é, são |
| **Russian (ru)** | Cyrillic characters + common words |
| **Japanese (ja)** | Hiragana, Katakana, Kanji characters |
| **Korean (ko)** | Hangul characters |
| **Chinese (zh)** | Chinese characters |
| **Arabic (ar)** | Arabic script |
| **Dutch (nl)** | de, het, een, is, zijn |
| **Polish (pl)** | ą, ć, ę, ł, ń, ó, ś, ź, ż + common words |
| **Turkish (tr)** | ç, ğ, ı, İ, ö, ş, ü + common words |
| **+ Swedish, Danish, Norwegian, Finnish, Hindi** | Character and word patterns |

### Visual Indicators

- **✓ Green Checkmark**: Language was auto-detected
  ```
  ✓ German (Auto-detected)
  ```

- **📝 Blue Pencil**: Language was manually selected
  ```
  📝 Spanish (Manually Selected)
  ```

### Manual Override

If auto-detection is wrong:
1. Simply change the dropdown to the correct language
2. Label updates automatically to show manual selection
3. Voices reload with the correct language

---

## 🎓 Advanced Features

### Auto-Play Mode

Automated flashcard review with customizable settings:

- **Pronounce Target Translation**: Enable/disable target language pronunciation
- **Delay Between Languages**: 0.5s - 3s (time between source and target)
- **Delay Before Next Card**: 1s - 5s (pause between cards)
- **Read Extended Content**: Include example sentences in pronunciation
- **Session Recording**: Record entire study session audio

### Spaced Repetition (SM-2 Algorithm)

- Cards are scheduled for review based on performance
- "Learned" cards return after calculated intervals
- Ease factor adjusts based on recall difficulty
- Progress persists across sessions (localStorage)

### Study Timers

- **Study Timer**: 5-60 minutes (stops when time expires)
- **Sleep Timer**: 10-45 minutes (for bedtime learning)
- Visual countdown display

### Advanced Modes

- **Loop Mode**: Restart from beginning when reaching the end
- **Repeat Mode**: Repeat each card 2-5 times before moving on
- **Focus Mode**: Full-screen distraction-free interface
- **Show Only Unlearned**: Filter out learned cards

### Category Management

- Create custom categories (e.g., "German A1", "Business English")
- Add subcategories (e.g., "German" → "A1 Vocabulary", "A2 Grammar")
- Assign CSV files to categories
- View all categories with file counts

### Session Statistics

Real-time tracking during Auto-Play:
- Cards reviewed
- Time studying
- Cards per minute
- Session start time

---

## 📖 Usage Guide

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `←` | Previous card |
| `→` | Next card |
| `Space` / `Enter` | Reveal translation |
| `P` | Pronounce source word |
| `E` | Pronounce target word |
| `L` | Mark as learned/unlearned |

### Mouse Controls

- **🔊 Speaker Button** (top-left): Pronounce source word
- **🔊 Speaker Button** (bottom): Pronounce target word
- **👁 Show Translation**: Reveal the target language side
- **← Previous / Next →**: Navigate between cards

### Best Practices

1. **Start with Auto-Detect**: Let the app detect languages first
2. **Use Manual Mapping for Complex CSVs**: If you have custom formats
3. **Enable Auto-Play for Passive Learning**: Great for commutes or workouts
4. **Mark Cards as Learned**: Builds your spaced repetition schedule
5. **Use Study Timers**: Set realistic goals (15-30 min sessions)
6. **Record Sessions**: Review your pronunciation later
7. **Focus Mode for Deep Study**: Eliminate distractions

---

## 🔧 Technical Details

### Architecture

```
Pure Client-Side Web Application
├── HTML5 (Structure)
├── CSS3 (Styling with gradients, animations)
└── Vanilla JavaScript (Logic)
    ├── CSV Parsing
    ├── Language Detection Engine
    ├── Speech Synthesis API
    ├── LocalStorage for Persistence
    └── MediaRecorder API for Recording
```

### Key Technologies

- **Web Speech API**: For text-to-speech pronunciation
- **FileReader API**: For CSV file reading
- **LocalStorage**: For progress and settings persistence
- **MediaRecorder API**: For session recording
- **Responsive Design**: Mobile and desktop friendly

### Data Storage

All data is stored locally in your browser:
- **Flashcard Progress**: `localStorage.flashcards_[filename]`
- **Categories**: `localStorage.flashcard_categories`
- **File Mappings**: `localStorage.flashcard_file_categories`

**Privacy**: No data leaves your device. No analytics. No tracking.

### Performance

- Handles CSVs with 1000+ cards efficiently
- Instant language detection (< 100ms)
- Minimal memory footprint
- No external dependencies

---

## 🌐 Browser Compatibility

### Fully Supported

✅ **Google Chrome** 90+ (Recommended)
✅ **Microsoft Edge** 90+
✅ **Safari** 14+
✅ **Firefox** 88+

### Requirements

- Modern browser with ES6 support
- Web Speech API support (for pronunciation)
- LocalStorage enabled
- MediaRecorder API (for recording feature)

### Voice Availability

- **Google Voices**: Best quality, available on Chrome/Edge
- **Microsoft Voices**: Available on Windows/Edge
- **System Voices**: Fallback on other platforms

---

## 📝 Changelog

### Version 3.1 (Current) - Cloud Synchronization Update

**Release Date**: January 2025

#### ☁️ Major Features
- **Cloud Synchronization**: Multi-device access with automatic backup
- **End-to-End Encryption**: AES-256-GCM encryption before data upload
- **Username/Password Authentication**: Simple, secure login (no email required)
- **Account Management**: Change password, logout, delete account
- **Sync Status Indicators**: Real-time visual feedback (✅ Synced, ⏳ Syncing, ❌ Error)
- **Offline Mode**: Optional "Skip Login" for local-only usage

#### 🔒 Security Features
- SHA-256 password hashing (never stored in plaintext)
- Client-side encryption (data encrypted on your device)
- Separate database path (`users-universal/`)
- Privacy-first approach (no tracking, no analytics)

#### 🐛 Bug Fixes
- Fixed localStorage wrapper to prevent infinite recursion
- Improved error handling for network failures
- Better session management across page reloads

---

### Version 3.0 - Language Auto-Detection Update

**Release Date**: December 2024

#### ✨ New Features
- **Intelligent Language Auto-Detection**: Automatically detects source and target languages from CSV content
- **15+ Language Support**: German, English, Spanish, French, Italian, Portuguese, Russian, Japanese, Korean, Chinese, Arabic, Hindi, Dutch, Polish, Turkish, and more
- **Visual Detection Indicators**: Green checkmark for auto-detected, blue pencil for manually selected
- **Enhanced Language Selector UI**: Prominent green gradient design with step-by-step workflow
- **Smart Detection Algorithm**: Pattern matching using special characters and common words
- **Manual Override Support**: Easy dropdown selection with automatic label updates
- **Real-time Voice Updates**: Voices reload automatically when language changes

#### 🔄 Improvements
- Redesigned language selection workflow (Step 1 → Step 2)
- Better visual feedback with color-coded labels
- Success messages for auto-detection completion
- Improved user experience for multi-language learning

#### 🐛 Bug Fixes
- Fixed language selector visibility after file upload
- Corrected voice selection logic for detected languages
- Improved label updating mechanism

---

### Version 2.4 - Enhanced Voice System

#### Features Added
- Premium Google voice support (🔊 indicator)
- Microsoft voice support (🎙️ indicator)
- Voice quality indicators in dropdown
- Enhanced voice information display
- Improved voice selection UI

---

### Version 2.3 - Advanced Features

#### Features Added
- Session recording capability
- Study and sleep timers
- Loop and repeat modes
- Focus mode for distraction-free learning
- Session statistics tracking
- Extended content reading toggle

---

### Version 2.1 - Format Selection

#### Features Added
- Three-way format selection (Predefined, Manual, Auto-detect)
- Interactive column mapping with modal popup
- Visual preview table for manual mapping
- Improved format detection algorithm

---

### Version 1.0 - Initial Release

#### Core Features
- Basic flashcard functionality
- CSV file upload
- Speech synthesis
- Progress tracking
- Spaced repetition
- Auto-play mode
- Category management

---

## 🆘 Support

### Common Issues

**Q: Language auto-detection is wrong**
A: Simply change the dropdown manually. The app will remember your selection and update the label to show "Manually Selected".

**Q: No voices available**
A: Check your browser's text-to-speech settings. Chrome/Edge have the best voice support. Try reloading the page.

**Q: CSV file won't load**
A: Ensure your CSV uses comma, semicolon, pipe, or tab separators. Check for special characters or encoding issues (UTF-8 recommended).

**Q: Progress not saving**
A: Enable cookies and localStorage in your browser. Some incognito/private modes disable storage.

**Q: Recording not working**
A: Grant microphone permissions when prompted. Recording requires HTTPS or localhost in most browsers.

---

### Troubleshooting

#### Language Detection Issues
```javascript
// Check browser console (F12) for detection logs:
// "🔍 Detected languages: { source: 'de', target: 'en' }"
```

#### Voice Issues
```javascript
// Check available voices in console:
window.speechSynthesis.getVoices()
```

#### CSV Format Issues
- Verify separator is consistent throughout file
- Check for quotes around text with commas
- Ensure UTF-8 encoding for special characters
- Remove BOM (Byte Order Mark) if present

---

## 🤝 Contributing

This is a personal learning project, but suggestions are welcome!

### Feature Requests
Create an issue on GitHub with:
- Clear description of the feature
- Use case examples
- Why it would be helpful

### Bug Reports
Include:
- Browser and version
- Steps to reproduce
- Expected vs. actual behavior
- Sample CSV (if applicable)

---

## 📜 License

This project is open source and available for personal and educational use.

**Author**: Masoud Sadeghi
**Contact**: [GitHub - masoudsade](https://github.com/masoudsade) | [GitHub - masoudsadeghi-oss](https://github.com/masoudsadeghi-oss)
**Repository**: [Telekom-Projects/Universal-Flashcard-App](https://github.com/masoudsade/Telekom-Projects)

---

## 🎓 Educational Use

Perfect for:
- Language learners of any level
- Students preparing for exams
- Teachers creating custom vocabulary sets
- Self-study and spaced repetition practice
- Polyglots learning multiple languages

---

## 🌟 Acknowledgments

- **Claude Code**: AI assistant that helped develop this application
- **Web Speech API**: Browser text-to-speech capabilities
- **SM-2 Algorithm**: Spaced repetition system by Piotr Woźniak
- **Community**: Feedback and suggestions from users

---

## 📞 Contact

- **GitHub (Personal)**: [masoudsade](https://github.com/masoudsade)
- **GitHub (Telekom)**: [masoudsadeghi-oss](https://github.com/masoudsadeghi-oss)
- **Repository**: [Telekom-Projects](https://github.com/masoudsade/Telekom-Projects)

---

**Built with ❤️ for language learners worldwide**

*Last Updated: January 2025*
