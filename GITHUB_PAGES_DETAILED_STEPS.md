# GitHub Pages - Detailed Step-by-Step Guide

## Can't Find "Build and deployment"? Follow This:

---

## 🔍 FIRST: Check Repository Visibility

**This is VERY important - GitHub Pages settings look different if repository is private!**

### Step 1: Check if Repository is Public or Private

1. Go to: https://github.com/{username}/Telekom-Projects

2. Look at the top, next to the repository name:
   ```
   {username} / Telekom-Projects    [Public]  or  [Private]
   ```

3. **If it says "Private":**
   - GitHub Pages might not be available or works differently
   - **Solution:** Make it Public first (see instructions below)

---

## 🔓 Make Repository Public (If Needed)

### Step 1: Go to General Settings

1. Go to: https://github.com/{username}/Telekom-Projects/settings

2. You're now in **"General"** settings (default page)

3. Scroll down to the very bottom

4. You'll see a section called **"Danger Zone"** (red background)

### Step 2: Change Visibility

1. In the "Danger Zone", find **"Change repository visibility"**

2. Click the **"Change visibility"** button

3. A popup will appear asking "Change visibility"

4. Select **"Make public"**

5. Type the repository name to confirm: `Telekom-Projects`

6. Click **"I understand, change repository visibility"**

**Now your repository is Public!**

---

## 📄 NOW: Enable GitHub Pages

### Step 1: Navigate to Pages Settings

**Option A: Direct Link (Easiest)**

Click this exact link:
```
https://github.com/{username}/Telekom-Projects/settings/pages
```

This should take you directly to GitHub Pages settings.

**Option B: Manual Navigation**

1. Go to: https://github.com/{username}/Telekom-Projects

2. Click **"Settings"** tab at the top

3. In the **left sidebar**, look for these sections:
   ```
   General
   Access
   Code and automation  ← Look for this section
      ↳ Branches
      ↳ Tags
      ↳ Rules
      ↳ Actions
      ↳ Webhooks
      ↳ Environments
      ↳ Pages  ← Click here!
   ```

4. Click **"Pages"** (under "Code and automation")

---

## 🎯 What You Should See on Pages Settings

### If Repository is Public and Pages NOT Enabled Yet:

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│  GitHub Pages                                                  │
│                                                                │
│  ⓘ GitHub Pages is designed to host your personal, organization, │
│     or project pages from a GitHub repository.                 │
│                                                                │
│  Build and deployment                                          │
│                                                                │
│  Source                                                        │
│  Your GitHub Pages site is currently being built from the      │
│  ┌──────────────────────────────────┐                         │
│  │ None                            ▼│  ← This dropdown        │
│  └──────────────────────────────────┘                         │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### Actions to Take:

1. **Click the "None" dropdown**

2. You'll see options:
   ```
   None
   GitHub Actions
   Deploy from a branch  ← Select this one!
   ```

3. **Select "Deploy from a branch"**

4. Two new dropdowns appear:
   ```
   Branch
   ┌──────────────┐  ┌────────────┐
   │ master      ▼│  │ / (root)  ▼│
   └──────────────┘  └────────────┘

        [ Save ]  ← Click this button
   ```

5. **Click "Save"**

---

## 🔄 Alternative: If You See Different Layout

### Layout 1: GitHub Actions (New UI)

Some repositories show this:

```
Build and deployment

Source
○ GitHub Actions
   Use a suggested workflow or create your own

● Deploy from a branch
   [Branch selection]
```

**If you see this:**
1. Select the radio button: **"Deploy from a branch"**
2. Choose branch: **master**
3. Choose folder: **/ (root)**
4. Click **"Save"**

---

## 📍 Visual Landmarks to Help You Navigate

### When in Settings → General (Wrong Place):

You'll see sections like:
- Repository name
- Default branch
- Features (Issues, Wiki, Projects, etc.)
- Pull Requests
- **Danger Zone** at bottom

This is **NOT the Pages settings!**

### When in Settings → Pages (Correct Place):

You'll see:
- "GitHub Pages" as the main heading
- "Build and deployment" section
- "Source" dropdown
- Possibly "Custom domain" field
- "Enforce HTTPS" checkbox

---

## 🆘 Troubleshooting: Can't Find Pages

### Issue 1: Repository is Private

**Symptom:** No "Pages" option in left sidebar

**Solution:**
1. Make repository Public (see instructions above)
2. Wait 1 minute
3. Refresh Settings page
4. "Pages" should now appear in sidebar

### Issue 2: Different GitHub Plan

**Symptom:** Pages is disabled or unavailable

**Check:**
- GitHub Free: Pages works for Public repositories
- GitHub Pro: Pages works for Public and Private repositories

**Solution:** Make repository Public if on Free plan

### Issue 3: Organization Repository

**Symptom:** Different permissions

**Check:** Are you the owner of the repository?

**Solution:**
1. Go to repository main page
2. Look at top: `{username} / Telekom-Projects`
3. Verify `{username}` is your username
4. If different, you might need owner permissions

---

## ✅ Step-by-Step Checklist

Follow these in order:

**Step 1: Repository Access**
- [ ] Go to: https://github.com/{username}/Telekom-Projects
- [ ] Verify you see "Settings" tab at top
- [ ] Verify you can click Settings tab

**Step 2: Repository Visibility**
- [ ] Check if repository shows "Public" or "Private"
- [ ] If Private, make it Public (Danger Zone → Change visibility)
- [ ] Confirm it now shows "Public"

**Step 3: Access Pages Settings**
- [ ] Method A: Use direct link: https://github.com/{username}/Telekom-Projects/settings/pages
- [ ] OR Method B: Settings → Sidebar → Code and automation → Pages
- [ ] Verify you see "GitHub Pages" heading

**Step 4: Configure Pages**
- [ ] Find "Build and deployment" section
- [ ] Find "Source" dropdown
- [ ] Click "Source" dropdown
- [ ] Select "Deploy from a branch"
- [ ] Select Branch: "master"
- [ ] Select Folder: "/ (root)"
- [ ] Click "Save" button

**Step 5: Wait and Verify**
- [ ] Wait 2-3 minutes
- [ ] Refresh the Pages settings page
- [ ] Look for green message: "Your site is live at..."
- [ ] Copy the URL shown
- [ ] Test the URL in new browser tab

---

## 📱 Quick Test URLs

Once enabled, test these (after waiting 2-3 minutes):

**Test 1: Root redirect**
```
https://{username}.github.io/Telekom-Projects/
```
Should see: Redirect page with flashcard app

**Test 2: Direct to app**
```
https://{username}.github.io/Telekom-Projects/German-Flashcard-App/flashcard.html
```
Should see: Purple gradient flashcard interface

**Test 3: Verify NOT code**
```
https://github.com/{username}/Telekom-Projects
```
This is the repository - should see code (this is normal)

---

## 🎓 Understanding the Page Layout

### Left Sidebar Structure:

```
Settings

General                    ← Default page when clicking Settings

Access
├─ Collaborators
└─ Moderation

Code and automation        ← Expand this section!
├─ Branches
├─ Tags
├─ Rules
├─ Actions
├─ Webhooks
├─ Environments
└─ Pages                   ← THIS IS WHAT YOU NEED!

Security
├─ Code security
└─ Secrets and variables

Integrations
└─ GitHub Apps

Archives
└─ ...
```

---

## 💡 What to Look For

### Key Visual Indicators You're in the Right Place:

1. **URL should be:**
   ```
   github.com/{username}/Telekom-Projects/settings/pages
   ```

2. **Page title at top:**
   ```
   GitHub Pages
   ```

3. **Blue info box:**
   ```
   ⓘ GitHub Pages is designed to host your personal,
     organization, or project pages from a GitHub repository.
   ```

4. **Section headings you'll see:**
   - Build and deployment
   - Custom domain (optional)
   - Enforce HTTPS

---

## 🔄 Alternative Method: Use GitHub Actions

If "Deploy from a branch" doesn't work, try GitHub Actions:

### Step 1: Create Workflow File

Create this file in your repository:
```
.github/workflows/static.yml
```

### Step 2: Use This Content

```yaml
name: Deploy static content to Pages

on:
  push:
    branches: ["master"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v4
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Step 3: Enable in Settings

1. Go to Settings → Pages
2. Under Source, select: **"GitHub Actions"**
3. No need to select branch
4. Push any change to trigger build

---

## 📞 Next Steps

**If you can see "Build and deployment":**
- Continue with enabling Pages
- Select "Deploy from a branch"
- Save and wait

**If you still can't see it:**
- Tell me: Is repository Public or Private?
- Tell me: What do you see in Settings → Pages?
- Tell me: Is there a "Pages" option in left sidebar?
- Send me what you see on the page

I'll help you figure it out! 🚀
