# Quick Start Guide - Universal Flashcard App

Get up and running with the Universal Flashcard App in under 5 minutes!

---

## ⚡ 60-Second Quick Start

1. **Open** `flashcard.html` in your browser
2. **Skip Login** (or create account for cloud sync)
3. **Upload** a CSV file with your vocabulary
4. **Start Learning** with arrow keys (← →) and Space

That's it! 🎉

---

## 🎯 5-Minute Complete Setup

### Step 1: Open the App (15 seconds)

- **Double-click** `flashcard.html`
- **Or**: Right-click → "Open with" → Choose your browser
- Works on: Chrome, Edge, Safari, Firefox

### Step 2: Cloud Sync Setup (60 seconds) - Optional

#### Option A: Create Account (Recommended)
```
👤 Click "Sign Up"
📝 Username: your_username
🔒 Password: ******** (8+ characters)
✅ Click "Sign Up"
```

**Benefits**: Multi-device access, automatic backup, progress sync

#### Option B: Skip Login
```
⏭️ Click "Skip Login"
```

**Use Case**: Offline-only, privacy-focused, testing

### Step 3: Prepare Your CSV (30 seconds)

Need a sample file? Create `test.csv`:

```csv
Source,Target
Hello,Hola
Goodbye,Adiós
Thank you,Gracias
Please,Por favor
Yes,Sí
No,No
```

**Or use an existing CSV** with any of these formats:
- 2 columns: `Word,Translation`
- 3 columns: `Word,Example,Translation`
- 4 columns: `Word,Example,Translation,Example`

### Step 4: Load Vocabulary (45 seconds)

1. **Click** "📁 Choose Vocabulary File"
2. **Select** your CSV file
3. **Wait** for auto-detection:
   - ✓ Languages detected automatically
   - ✓ Format recognized
4. **Click** "Use Predefined Format" → Select format → "Load Flashcards"
   - **Or** let "Auto-Detect Format" do it for you

### Step 5: Start Learning! (30 seconds)

**Basic Controls:**
- **→** Next card
- **←** Previous card
- **Space** Show translation
- **P** Hear source pronunciation
- **E** Hear target pronunciation
- **L** Mark as learned

**You're ready to learn!** 🚀

---

## 📚 Common Scenarios

### Scenario 1: Learning Spanish Vocabulary

```
1. Open app → Skip Login
2. Upload Spanish-English CSV
3. App detects: Source=Spanish, Target=English
4. Use arrow keys + Space to study
5. Press L to mark words you know
```

**Time**: 2 minutes to start studying

### Scenario 2: Multi-Device Language Learning

```
Day 1 (Computer):
1. Open app → Sign Up (username + password)
2. Upload vocabulary
3. Study 30 minutes
4. Close browser (progress auto-saved)

Day 2 (Phone):
1. Open app → Login (same credentials)
2. Vocabulary loads automatically
3. Continue where you left off
```

**Time**: 3 minutes initial setup, instant sync thereafter

### Scenario 3: Passive Learning Before Sleep

```
1. Load familiar vocabulary
2. Click "▶️ Start Auto-Play"
3. Enable settings:
   ✅ Pronounce Target Translation
   ✅ Read Extended Content
   ⏰ Sleep Timer: 30 minutes
4. Lie back and listen
```

**Time**: 1 minute to configure

---

## 🎨 Sample CSV Files

### Beginner: Basic Greetings (2-Column)

**File: `greetings.csv`**
```csv
English,Spanish
Hello,Hola
Good morning,Buenos días
Good afternoon,Buenas tardes
Good evening,Buenas noches
Goodbye,Adiós
See you later,Hasta luego
Thank you,Gracias
You're welcome,De nada
Please,Por favor
Excuse me,Perdón
```

### Intermediate: With Examples (4-Column)

**File: `common_phrases.csv`**
```csv
English,EnglishExample,Spanish,SpanishExample
How are you?,How are you doing today?,¿Cómo estás?,¿Cómo estás hoy?
I'm fine,I'm fine thanks,Estoy bien,Estoy bien gracias
What's your name?,What's your name?,¿Cómo te llamas?,¿Cuál es tu nombre?
My name is...,My name is John,Me llamo...,Me llamo Juan
Nice to meet you,Nice to meet you too,Encantado de conocerte,Igualmente
```

### Advanced: Themed Vocabulary

**File: `food.csv`**
```csv
Category,English,German,Example
Fruit,Apple,Apfel,Ich esse einen Apfel
Fruit,Banana,Banane,Die Banane ist gelb
Vegetable,Carrot,Karotte,Karotten sind gesund
Meat,Chicken,Hähnchen,Hähnchen mit Reis
Drink,Water,Wasser,Ein Glas Wasser bitte
```

---

## ⚙️ Essential Settings

### Voices (For Better Pronunciation)

```
1. Upload CSV
2. Languages auto-detected
3. Best voices selected automatically
4. Click speaker buttons (🔊) to test

Optional: Manually select voices
→ Settings → Source Voice / Target Voice
```

### Auto-Play (For Hands-Free Learning)

```
▶️ Start Auto-Play

Settings to adjust:
├─ Pronounce Target Translation: ON
├─ Delay Between Languages: 1.5s
├─ Delay Before Next Card: 2s
└─ Read Extended Content: OFF (for speed)
```

### Display Options

```
✅ Show Only Unlearned Cards: Focus on words you don't know
✅ Loop Mode: Restart from beginning at end
✅ Repeat Mode: Repeat each card 2-3 times
```

---

## 🔑 Essential Keyboard Shortcuts

Learn these 5 shortcuts for 10x faster studying:

| Key | Action | Why It's Essential |
|-----|--------|-------------------|
| **→** | Next card | Fast navigation |
| **Space** | Show translation | Quick reveal |
| **P** | Pronounce source | Hear correct pronunciation |
| **E** | Pronounce target | Practice speaking |
| **L** | Mark learned | Track progress |

**Pro tip**: Use this rhythm for speed studying:
```
Space → P → E → L → →
(Reveal → Hear Source → Hear Target → Mark Learned → Next)
```

---

## 💡 First Session Tips

### Do This ✅

1. **Start small**: 20-30 words maximum
2. **Use examples**: 4-column format helps retention
3. **Mark progress**: Use "Mark Learned" as you go
4. **Enable auto-play**: Try hands-free after first manual pass
5. **Set a timer**: 15 minutes focused study beats 1 hour distracted

### Avoid This ❌

1. ❌ Loading 500+ words on day 1
2. ❌ Skipping language verification
3. ❌ Ignoring pronunciation (clicking too fast)
4. ❌ Not marking progress (you'll forget what you learned)
5. ❌ Studying without breaks (take 5 min breaks every 20 min)

---

## 🆘 Quick Troubleshooting

### "CSV won't load"

**Fix:**
- Check separator (comma, semicolon, tab, or pipe)
- Ensure UTF-8 encoding
- Remove empty rows
- Verify at least 2 columns

### "No voices available"

**Fix:**
- Reload page (voices load on startup)
- Try Chrome (best voice support)
- Check browser settings → Accessibility → Text-to-Speech

### "Language detection wrong"

**Fix:**
- Simply change dropdown manually
- App remembers your selection
- Voices reload automatically

### "Can't login"

**Fix:**
- Username is case-sensitive
- Check password (8+ characters)
- Try "Skip Login" if forgot password
- Check internet connection

---

## 🎓 Next Steps

### After Your First Session

1. **Review Progress**
   - Check how many words marked as learned
   - Note which words are difficult

2. **Explore Features**
   - Try Auto-Play mode
   - Test different voice settings
   - Create categories for organization

3. **Expand Vocabulary**
   - Load additional CSV files
   - Organize into categories
   - Set daily study goals

### Recommended Learning Path

```
Week 1: Basic Features
├─ Manual navigation (arrow keys)
├─ Pronunciation (P and E keys)
├─ Mark as learned (L key)
└─ Simple CSV files (2-3 columns)

Week 2: Advanced Features
├─ Auto-play mode
├─ Category organization
├─ Spaced repetition
└─ Study timers

Week 3: Optimization
├─ Custom voice selection
├─ Focus mode for deep study
├─ Session recording
└─ Multi-device sync (if using cloud)
```

---

## 📖 Full Documentation

For detailed information, see:

- **[README.md](README.md)** - Complete features overview
- **[USER_GUIDE.md](USER_GUIDE.md)** - Comprehensive user manual
- **[FIREBASE_SETUP.md](FIREBASE_SETUP.md)** - Cloud sync details
- **[TROUBLESHOOTING.md](TROUBLESHOOTING.md)** - Problem solving
- **[CHANGELOG.md](CHANGELOG.md)** - Version history

---

## 🎯 Study Goals Template

Copy this and track your progress:

```
📅 Study Plan - [Your Name]

Week 1:
├─ Monday: Load Spanish basics (30 words) ✅
├─ Tuesday: Review + add 20 words ✅
├─ Wednesday: Auto-play review 20 min ⏳
├─ Thursday: Mark all learned words ⏳
├─ Friday: New category: Verbs ⏳
├─ Weekend: Rest day ⏳
└─ Total Goal: 50 words learned

Week 2:
├─ Monday: Grammar phrases (20 words)
├─ Tuesday: Review all previous
├─ Wednesday: Auto-play 30 min
└─ ...
```

---

## ✅ Quick Reference Card

Print this or keep it handy:

```
═══════════════════════════════════════════
    UNIVERSAL FLASHCARD APP CHEAT SHEET
═══════════════════════════════════════════

KEYBOARD SHORTCUTS:
→ ← : Navigate cards
Space : Show translation
P : Pronounce source
E : Pronounce target
L : Mark as learned

MOUSE CLICKS:
📁 : Load CSV file
👁 : Show translation
🔊 : Pronounce word
✓ : Mark learned
▶️ : Start auto-play

FIRST-TIME SETUP:
1. Open flashcard.html
2. Skip Login or Sign Up
3. Choose CSV file
4. Start with → ← Space

ESSENTIAL SETTINGS:
⚙️ Auto-Play: Hands-free review
📂 Categories: Organize files
🎙️ Voices: Select pronunciation
⏰ Timers: Set study duration

SUPPORT:
📖 USER_GUIDE.md
🐛 TROUBLESHOOTING.md
💬 GitHub Issues

═══════════════════════════════════════════
```

---

## 🚀 You're Ready!

You now have everything you need to start learning languages effectively with the Universal Flashcard App.

**Remember:**
- Consistency beats intensity
- Mark your progress
- Use pronunciation features
- Take breaks
- Have fun learning! 🌍

**Happy Learning!** 📚

---

**Last Updated**: January 2025
**App Version**: 3.1
