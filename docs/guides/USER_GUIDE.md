# Universal Flashcard App - User Guide

A comprehensive guide to using all features of the Universal Flashcard App v3.1

---

## 📋 Table of Contents

- [Getting Started](#getting-started)
- [Cloud Sync Features (v3.1)](#cloud-sync-features-v31)
- [Loading Vocabulary](#loading-vocabulary)
- [Language Selection](#language-selection)
- [Studying Flashcards](#studying-flashcards)
- [Advanced Features](#advanced-features)
- [Category Management](#category-management)
- [Voice & Pronunciation](#voice--pronunciation)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Tips & Best Practices](#tips--best-practices)

---

## 🚀 Getting Started

### First Launch

1. **Open the Application**
   - Double-click `flashcard.html` or open it in your browser
   - Works offline (no internet required for basic features)

2. **Cloud Sync (Optional)**
   - **New to app?** Click "Sign Up" to create an account
   - **Have an account?** Click "Login" to access your data
   - **Offline mode?** Click "Skip Login" to use without cloud sync

3. **Load Your First Vocabulary File**
   - Click "📁 Choose Vocabulary File"
   - Select a CSV file from your computer
   - App automatically detects the format and languages

4. **Start Learning!**
   - Use arrow buttons (← →) or keyboard arrows to navigate
   - Click "👁 Show Translation" or press Space/Enter to reveal answer
   - Mark words as learned with the "✓ Mark Learned" button

---

## ☁️ Cloud Sync Features (v3.1)

### Creating an Account

1. **Click "Sign Up"** on the login modal
2. **Enter Username**
   - Use letters, numbers, underscore, or hyphen
   - Examples: `john_doe`, `language-learner123`
3. **Create Password**
   - Minimum 8 characters
   - Mix of letters and numbers recommended
4. **Click "Sign Up"**
   - Your data is encrypted and uploaded
   - You're automatically logged in

### Logging In

1. **Enter Your Credentials**
   - Username (case-sensitive)
   - Password
2. **Click "Login"**
   - Your encrypted data downloads
   - Vocabulary and progress restore automatically
3. **Multi-Device Access**
   - Login from phone, tablet, or any computer
   - All devices stay synchronized

### Account Management

Access via **Account button (👤)** in top-right corner:

#### Change Password
1. Click "Change Password"
2. Enter current password
3. Enter new password (8+ characters)
4. Confirm new password
5. Click "Change Password"
   - All data re-encrypted with new password
   - You'll be logged out
   - Login again with new password

#### Logout
1. Click "Logout"
2. Confirm action
   - Local data cleared
   - Cloud data preserved
   - Can login anytime to restore

#### Delete Account
1. Click "Delete Account"
2. Enter your password
3. Confirm deletion
   - **⚠️ This is permanent and cannot be undone**
   - All data erased from cloud
   - No recovery possible

### Sync Status

Watch the sync indicator in the top-right:

| Icon | Status | What It Means |
|------|--------|---------------|
| ✅ | **Synced** | All changes saved to cloud |
| ⏳ | **Syncing** | Uploading changes now |
| ❌ | **Error** | Sync failed - check connection |

**Sync happens automatically when:**
- You mark a flashcard as learned
- You load a new CSV file
- You create or edit categories
- You change app settings

---

## 📁 Loading Vocabulary

### Supported CSV Formats

The app accepts CSV files with these separators:
- ✅ Comma (`,`)
- ✅ Semicolon (`;`)
- ✅ Pipe (`|`)
- ✅ Tab

### Format Examples

#### 2-Column Simple
```csv
Source,Target
Bonjour,Hello
Merci,Thank you
```

#### 3-Column Standard
```csv
Source,SourceExample,Target
Bonjour,Bonjour mes amis,Hello
Merci,Merci beaucoup,Thank you
```

#### 4-Column Full
```csv
Source,SourceExample,Target,TargetExample
Bonjour,Bonjour mes amis,Hello,Hello my friends
Merci,Merci beaucoup,Thank you,Thank you very much
```

### Loading Methods

#### Method 1: Predefined Formats (Fastest)
1. Upload CSV file
2. Click "Use Predefined Format"
3. Select format from dropdown:
   - 2-column (word → translation)
   - 3-column (word → example → translation)
   - 4-column (word → example → translation → example)
4. Click "Load Flashcards"

#### Method 2: Manual Column Mapping (Most Flexible)
1. Upload CSV file
2. Click "Select Columns Manually"
3. Modal shows preview of your data
4. Click column headers to assign types:
   - **🌍 Source Word**: Main vocabulary
   - **📝 Source Example**: Extended content
   - **🎯 Target Word**: Translation
   - **📖 Target Example**: Translation example
   - **🚫 Ignore**: Skip this column
5. Click "Apply Mapping"

#### Method 3: Auto-Detection (Let App Decide)
1. Upload CSV file
2. Click "Auto-Detect Format"
3. App analyzes structure
4. Flashcards load automatically

### Handling Multiple Files

You can load multiple CSV files:
- Each file stored separately
- Switch between files via category system
- Progress tracked per file
- Files synchronized across devices (if logged in)

---

## 🌐 Language Selection

### Automatic Language Detection

**How It Works:**
1. Upload your CSV file
2. App analyzes first 20 rows
3. Detects languages based on:
   - Special characters (ä, ö, ü, ñ, ç, etc.)
   - Common words (der, the, el, le, etc.)
4. Pre-selects languages in dropdowns
5. Shows **"✓ Auto-detected"** label in green

**Supported Languages** (15+):
- 🇩🇪 German (de)
- 🇬🇧 English (en)
- 🇪🇸 Spanish (es)
- 🇫🇷 French (fr)
- 🇮🇹 Italian (it)
- 🇵🇹 Portuguese (pt)
- 🇷🇺 Russian (ru)
- 🇯🇵 Japanese (ja)
- 🇰🇷 Korean (ko)
- 🇨🇳 Chinese (zh)
- 🇸🇦 Arabic (ar)
- 🇮🇳 Hindi (hi)
- 🇳🇱 Dutch (nl)
- 🇵🇱 Polish (pl)
- 🇹🇷 Turkish (tr)
- Plus: Swedish, Danish, Norwegian, Finnish

### Manual Language Selection

If auto-detection is incorrect:

1. **Change Source Language**
   - Click "Source Language" dropdown
   - Select correct language
   - Label changes to **"📝 Manually Selected"** (blue)

2. **Change Target Language**
   - Click "Target Language" dropdown
   - Select correct language
   - Label updates automatically

3. **Reload Voices**
   - Voices automatically update for selected languages
   - Best voices selected based on your choice

---

## 📖 Studying Flashcards

### Basic Navigation

#### Using Mouse
- **👁 Show Translation**: Reveals the target language side
- **← Previous**: Go to previous card
- **→ Next**: Move to next card
- **🔊 Speaker Button** (top-left): Pronounce source word
- **🔊 Speaker Button** (bottom): Pronounce target word

#### Using Keyboard
- **→ (Right Arrow)**: Next card
- **← (Left Arrow)**: Previous card
- **Space / Enter**: Show translation
- **P**: Pronounce source word
- **E**: Pronounce target word
- **L**: Mark as learned/unlearned

### Marking Progress

1. **Mark as Learned**
   - Click "✓ Mark Learned" button
   - Or press **L** on keyboard
   - Card tracked in spaced repetition system

2. **Unmark Learned**
   - Click "↺ Unmark Learned" (appears on learned cards)
   - Or press **L** again
   - Card returns to unlearned pool

3. **Filter Unlearned**
   - Toggle "Show Only Unlearned Cards"
   - Focus on words you haven't mastered
   - Learned cards hidden temporarily

### Progress Tracking

- **Card Counter**: Shows "Card X of Y"
- **Progress Indicator**: Visual bar shows completion
- **Learned Count**: Displays number of mastered words
- **Persistence**: Progress saved locally and in cloud (if logged in)

---

## 🎓 Advanced Features

### Auto-Play Mode

Hands-free flashcard review with customizable settings.

#### Enabling Auto-Play
1. Click "▶️ Start Auto-Play"
2. Adjust settings (optional):
   - **Pronounce Target Translation**: Enable/disable
   - **Delay Between Languages**: 0.5s - 3s
   - **Delay Before Next Card**: 1s - 5s
   - **Read Extended Content**: Include examples

#### Auto-Play Controls
- **⏸️ Pause**: Temporarily stop playback
- **▶️ Resume**: Continue from current card
- **⏹️ Stop**: End auto-play session

#### Recording Sessions
1. Enable "📹 Record Session"
2. Start auto-play
3. Grant microphone permission when prompted
4. Audio of your study session records
5. Download recording when done

### Spaced Repetition (SM-2 Algorithm)

**How It Works:**
1. Mark card as "Learned"
2. Card scheduled for future review
3. Review intervals increase over time:
   - 1 day → 3 days → 7 days → 14 days...
4. Algorithm adjusts based on recall success

**Benefits:**
- Optimize learning efficiency
- Focus on challenging words
- Long-term retention improvement

### Study Timers

#### Study Timer
- Set duration: 5-60 minutes
- Visual countdown display
- Stops auto-play when time expires
- Perfect for timed study sessions

#### Sleep Timer
- Set duration: 10-45 minutes
- For bedtime learning
- App stops automatically
- Prevents overnight playback

### Advanced Modes

#### Loop Mode
- **Enable**: Toggle "Loop Mode"
- **Behavior**: Restarts from beginning at end
- **Use Case**: Continuous review sessions

#### Repeat Mode
- **Enable**: Toggle "Repeat Mode"
- **Setting**: Repeat each card 2-5 times
- **Behavior**: Same card shown multiple times before moving
- **Use Case**: Intensive memorization

#### Focus Mode
- **Enable**: Click "Enter Focus Mode"
- **Features**:
  - Full-screen interface
  - Hides distractions
  - Centered flashcard display
  - Minimal UI
- **Exit**: Press **Esc** or click "Exit Focus Mode"

---

## 📂 Category Management

Organize your vocabulary files into categories and subcategories.

### Creating Categories

1. **Click "Manage Categories"**
2. **Enter Category Name**
   - Example: "German A1", "Business Spanish"
3. **Click "Add Category"**
4. Category appears in list

### Creating Subcategories

1. **Hover over parent category**
2. **Click "Add Subcategory"**
3. **Enter subcategory name**
   - Example: "Verbs", "Nouns", "Grammar"
4. Subcategory nested under parent

### Assigning Files to Categories

1. **Load a CSV file**
2. **Click "Assign to Category"** (appears after loading)
3. **Select category from dropdown**
4. **Click "Assign"**
5. File now belongs to category

### Viewing Categories

1. **Click "View All Categories"**
2. See category list with:
   - Category name
   - Number of files
   - Subcategories (if any)
3. **Click category** to filter files

### Benefits

- ✅ Organize hundreds of vocabulary files
- ✅ Quick access to specific topics
- ✅ Track progress by category
- ✅ Sync categories across devices

---

## 🎙️ Voice & Pronunciation

### Voice Types

The app uses three types of voices:

| Type | Icon | Quality | Availability |
|------|------|---------|--------------|
| **Google Voices** | 🔊 | Premium | Chrome, Edge |
| **Microsoft Voices** | 🎙️ | High | Windows, Edge |
| **System Voices** | 🔈 | Good | All browsers |

### Voice Selection

#### Automatic Selection
- App automatically picks best voice for detected language
- Prioritizes Google > Microsoft > System voices

#### Manual Selection
1. **Click "Select Voices"** (in settings panel)
2. **Source Voice Dropdown**:
   - Choose voice for source language
   - Icons indicate voice type (🔊🎙️🔈)
3. **Target Voice Dropdown**:
   - Choose voice for target language
4. **Test Voices**:
   - Click speaker buttons to preview

### Speech Settings

#### Speech Rate
- **Range**: 0.5x (slow) to 1.5x (fast)
- **Default**: 1.0x (normal speed)
- **Adjust**: Use slider in settings
- **Use Case**: Slow down for difficult words

#### Pitch
- **Range**: 0.5 (low) to 2.0 (high)
- **Default**: 1.0 (normal pitch)
- **Adjust**: Use slider in settings
- **Use Case**: Make voice easier to understand

### Voice Troubleshooting

**No voices available?**
1. Check browser supports Web Speech API
2. Reload page (voices load on startup)
3. Try different browser (Chrome recommended)

**Wrong language pronunciation?**
1. Verify language selection is correct
2. Manually select appropriate voice
3. Check voice language matches your content

**Voice cuts off?**
1. Reduce speech rate
2. Shorten example sentences
3. Disable extended content reading

---

## ⌨️ Keyboard Shortcuts

Master these shortcuts for efficient studying:

| Key | Action | Context |
|-----|--------|---------|
| **→** | Next card | Always |
| **←** | Previous card | Always |
| **Space** | Show translation | When hidden |
| **Enter** | Show translation | When hidden |
| **P** | Pronounce source | Always |
| **E** | Pronounce target | Always |
| **L** | Toggle learned status | Always |
| **Esc** | Exit focus mode | In focus mode |

### Pro Tips

1. **Navigation**: Use arrow keys exclusively for fastest navigation
2. **Reveal & Advance**: Space → Right Arrow (quick rhythm)
3. **Audio Review**: P → E → Right Arrow (listen then advance)
4. **Quick Learn**: L → Right Arrow (mark and move on)

---

## 💡 Tips & Best Practices

### For New Users

1. **Start Small**
   - Begin with 20-30 words
   - Master basics before adding more
   - Don't overwhelm yourself

2. **Use Auto-Detection**
   - Let app detect languages first
   - Only override if clearly wrong
   - Saves time on setup

3. **Enable Cloud Sync**
   - Create account early
   - Backs up progress automatically
   - Access from any device

### For Active Learners

1. **Daily Study Routine**
   - Set 15-30 minute study timer
   - Review same deck multiple times
   - Consistency beats duration

2. **Leverage Spaced Repetition**
   - Mark cards as learned
   - Let algorithm schedule reviews
   - Focus on unlearned cards first

3. **Use Categories**
   - Organize by topic (grammar, vocab, phrases)
   - Create subcategories for detail
   - Track progress per category

### For Advanced Users

1. **Optimize Auto-Play**
   - Adjust delays to match learning speed
   - Enable recording for pronunciation practice
   - Use sleep timer for passive learning

2. **Focus Mode Sessions**
   - Eliminate distractions
   - Set study timer
   - Enable repeat mode for intensive review

3. **Multiple Language Pairs**
   - Load different CSV files
   - Switch languages via categories
   - Track progress separately

### Best CSV Practices

1. **Use Examples**
   - 4-column format provides context
   - Examples improve retention
   - Pronunciation more natural

2. **Consistent Formatting**
   - Same separator throughout
   - UTF-8 encoding for special characters
   - No empty rows or columns

3. **Logical Organization**
   - Group by theme (colors, numbers, food)
   - Progressive difficulty (beginner → advanced)
   - Separate files for different topics

### Study Strategies

#### Intensive Learning
```
1. Load new vocabulary (20-30 words)
2. Study normally first pass
3. Mark known words as learned
4. Enable "Show Only Unlearned"
5. Use repeat mode (3x per card)
6. Set 15-minute study timer
7. Take 5-minute break
8. Repeat until all learned
```

#### Passive Review
```
1. Load familiar vocabulary
2. Enable auto-play
3. Set sleep timer (30 minutes)
4. Pronounce target enabled
5. Extended content enabled
6. Listen while commuting/exercising
```

#### Pronunciation Practice
```
1. Enable session recording
2. Start auto-play
3. Pronounce target disabled initially
4. Say translation before reveal
5. Compare with actual pronunciation
6. Review recording after session
```

---

## 🔗 Related Documentation

- [README.md](README.md) - Overview and features
- [QUICK_START.md](QUICK_START.md) - Quick start guide
- [FIREBASE_SETUP.md](FIREBASE_SETUP.md) - Cloud sync technical details
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Common issues and solutions
- [CHANGELOG.md](CHANGELOG.md) - Version history

---

## 📞 Need Help?

- **Common issues**: See [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
- **Feature requests**: Open GitHub issue
- **Bug reports**: Include browser, OS, and steps to reproduce

---

**Last Updated**: January 2025
**App Version**: 3.1
**Guide Version**: 1.0
