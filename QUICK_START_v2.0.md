# Quick Start Guide - Version 2.0

## 🚀 What's Different in v2.0?

### Main Improvements:
1. **Smart Format Detection** - CSV columns auto-detected (German/English order doesn't matter!)
2. **Extended Content** - Add example sentences for better learning
3. **Flexible Auto-Play** - Choose to read words only or full sentences

---

## 📋 CSV Format Examples

### Format 1: Simple (2 columns)
```csv
Hallo,Hello
Wasser,Water
```
**OR reversed:**
```csv
Hello,Hallo
Water,Wasser
```
✅ Both work! Auto-detected.

### Format 2: With Notes (3 columns)
```csv
Hallo,Hello,Common greeting
Wasser,Water,Beverage
```

### Format 3: Extended - NEW! (4 columns)
```csv
Hallo,Ich sage hallo zu Freunden,Hello,I say hello to friends
Wasser,Ich trinke kaltes Wasser,Water,I drink cold water
```

Structure: `Word, Example Sentence, Word, Example Sentence`

### Format 4: With Headers (Optional)
```csv
German,English,Notes
Hallo,Hello,Greeting
Wasser,Water,Drink
```
Headers automatically skipped!

---

## 🎯 How to Use Extended Content

### Step 1: Create CSV with Extended Format
```csv
Haus,Ich wohne in einem großen Haus,House,I live in a big house
Auto,Mein Auto ist schnell,Car,My car is fast
```

### Step 2: Upload the File
- Click "📁 Upload CSV File"
- Select your CSV

### Step 3: See Extended Content
- Extended sentences appear in the detail section
- Look for the 📝 icon

### Step 4: Enable in Auto-Play (Optional)
1. Click "⚙️ Settings & Options"
2. Open "👁️ Display Options"
3. Check "📖 Read Extended Examples/Sentences in Auto-Play"
4. Start Auto-Play

**Result:**
- ❌ **Unchecked**: Reads "Haus" → "House"
- ✅ **Checked**: Reads "Ich wohne in einem großen Haus" → "I live in a big house"

---

## 🎓 Learning Strategies

### Beginner Strategy
1. Start with simple 2-column format
2. Focus on word-only pronunciation
3. Add extended examples for hard words only

**CSV Example:**
```csv
Hallo,Hello
Danke,Thank you
Haus,Ich wohne in einem Haus,House,I live in a house
```
Mix basic and extended!

### Intermediate Strategy
1. Use 4-column format for all cards
2. Keep extended reading OFF initially
3. Enable it after learning basic words
4. Use for context practice

### Advanced Strategy
1. Create comprehensive sentence-based cards
2. Always enable extended reading
3. Use for immersion and natural speech patterns
4. Add grammar notes in 5th column

---

## 🔄 Version Management

### Files in Your Folder:

1. **flashcard.html** - Version 2.0 (current/enhanced)
2. **flashcard_v1.0_backup.html** - Original version (backup)
3. **sample_vocabulary.csv** - Original simple examples
4. **sample_vocabulary_extended.csv** - NEW! Extended format examples

### To Use Old Version:
Simply open `flashcard_v1.0_backup.html` instead of `flashcard.html`

### To Use New Version:
Open `flashcard.html` (default)

---

## 🎨 Feature Comparison

| Feature | v1.0 | v2.0 |
|---------|------|------|
| Basic German/English | ✅ | ✅ |
| Fixed column order | ✅ | ❌ |
| Auto language detection | ❌ | ✅ |
| Reversed columns support | ❌ | ✅ |
| Header row support | ❌ | ✅ |
| Extended sentences | ❌ | ✅ |
| Contextual examples | ❌ | ✅ |
| Flexible auto-play | ❌ | ✅ |
| Backward compatible | - | ✅ |

---

## 💡 Pro Tips

### Tip 1: Test Format Detection
Try this CSV to see smart detection:
```csv
Hello,Hallo
Water,Wasser
Good morning,Guten Morgen
```
Despite being English-first, it's correctly detected!

### Tip 2: Mix Formats in One File
```csv
Hallo,Hello
Wasser,Ich trinke Wasser jeden Tag,Water,I drink water every day
Brot,Bread,Food item
```
Different formats per row work fine!

### Tip 3: Use Extended Content Strategically
- Difficult words → Add example sentence
- Easy words → Keep simple
- Verbs → Add conjugation example
- Nouns → Add article (der Hund, die Katze)

### Tip 4: Auto-Play Workflow
1. First pass: Extended reading OFF (learn words)
2. Second pass: Extended reading ON (learn context)
3. Third pass: Extended reading OFF (test recall)

---

## 🐛 Troubleshooting

### Extended content not showing?
- Check CSV has 4 columns
- Ensure commas separate all columns
- Verify sentences are longer than 3 words

### Language detection wrong?
- Add German articles (der, die, das)
- Use German characters (ä, ö, ü)
- Include common German words (und, ich, ist)

### CSV not loading?
- Check file encoding is UTF-8
- Ensure commas (not semicolons) separate columns
- Remove empty lines at end of file

### Want old behavior?
- Use `flashcard_v1.0_backup.html`
- Or use simple 2-column CSV format

---

## 📚 Sample Use Cases

### Use Case 1: Exam Prep
```csv
German Word,Example in Context,English,Translation
der Apfel,Der Apfel ist rot und süß,apple,The apple is red and sweet
```
Enable extended reading for exam context questions!

### Use Case 2: Casual Learning
```csv
Hallo,Hello
Danke,Thank you
Bitte,Please
```
Simple format, no extended content needed.

### Use Case 3: Immersion Practice
```csv
Guten Morgen,Guten Morgen! Wie geht es Ihnen heute?,Good morning,Good morning! How are you today?
```
Full sentences for natural conversation practice.

---

## ⚡ Quick Commands

| Action | Steps |
|--------|-------|
| Upload basic CSV | Upload → Use as normal |
| Upload extended CSV | Upload → Check in Display Options |
| Enable sentence reading | Settings → Display Options → Check box |
| Switch to old version | Open flashcard_v1.0_backup.html |
| Test auto-detection | Upload sample_vocabulary_extended.csv |

---

## 📞 Need Help?

1. **Check this guide** - Common issues covered above
2. **Review VERSION_2.0_CHANGELOG.md** - Detailed feature explanation
3. **Try sample files** - Test with included samples first
4. **Revert to v1.0** - Use backup if issues persist

---

**Happy Learning! 🎉**

Version 2.0 gives you the power to learn your way - simple words or full context!
