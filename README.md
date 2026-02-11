# RECON — Setup Guide

## What You're Getting

Three files:

| File | What it is | Size |
|------|-----------|------|
| `index.html` | The app itself — all code in one file | ~54 KB |
| `data.json` | Your company database (3,499 companies, 10 countries) + your track record | ~878 KB |
| `README.md` | This guide | — |


## Step 1: Create a GitHub Account (skip if you have one)

1. Go to **https://github.com** and click **Sign up**
2. Follow the prompts — free account is fine
3. Verify your email


## Step 2: Create a Private Repository

1. Log into GitHub
2. Click the **+** button (top right) → **New repository**
3. Fill in:
   - **Repository name**: `recon` (or whatever you like)
   - **Description**: Defence sector prospecting tool
   - **Visibility**: Select **Private** (important — this has your company data)
   - Do NOT tick "Add a README file" (we already have one)
4. Click **Create repository**


## Step 3: Upload Your Files

You'll land on a page that says "Quick setup". The easiest method:

1. On that page, click the link that says **"uploading an existing file"**
2. Drag and drop ALL THREE files onto the upload area:
   - `index.html`
   - `data.json`
   - `README.md`
3. At the bottom, type a commit message like "Initial upload"
4. Click **Commit changes**

You should now see all three files listed in your repository.


## Step 4: Enable GitHub Pages (this makes it a live website)

1. In your repository, click **Settings** (tab along the top)
2. In the left sidebar, scroll down and click **Pages**
3. Under **"Build and deployment"**:
   - **Source**: Select **Deploy from a branch**
   - **Branch**: Select **main** and **/ (root)**
4. Click **Save**
5. Wait 1–2 minutes
6. Refresh the page — you'll see a message: **"Your site is live at..."** with a URL like:
   ```
   https://yourusername.github.io/recon/
   ```
7. Click that link — your app should load with all 3,499 companies

**Note**: Even though the repo is private, GitHub Pages sites are publicly accessible by URL. Nobody will find it unless they have the exact URL, but be aware of this. If this is a concern, see the "Running Locally" section below.


## Step 5: Get an Anthropic API Key (for AI features)

The AI email generation and company intelligence features need an API key:

1. Go to **https://console.anthropic.com**
2. Sign up / log in
3. Go to **API Keys** in the left menu
4. Click **Create Key**
5. Copy the key (starts with `sk-ant-...`)
6. In the RECON app, go to **Settings** (⚙ in the sidebar)
7. Paste your API key and click **Save**

**Cost**: Each AI email or intelligence pull costs roughly $0.01–0.03. Very cheap for occasional use. You'll need to add credit to your Anthropic account (minimum $5).


## Step 6: Start Using It

### Your daily workflow:

1. **Open the app** — you land on **Daily Actions** (your morning queue)
2. **Go to Companies** → search for a target → click into it
3. **Pull News** — click the button in the AI Intelligence panel to get a briefing
4. **Add Decision Makers** — click "+ Add" under the relevant category (MGMT / ENG / HR), paste in name, title, email, phone, LinkedIn URL from your research
5. **Send Outreach** — click **✉ AI Email** next to a contact → the AI drafts a bespoke email using your track record + company intel → edit if needed → click **"Copy & Mark Sent → Follow-up 4 days"** → paste into Outlook and send
6. **Log Calls** — click **☎ Log Call** → select outcome (Spoke / Voicemail / No Answer) → add notes → follow-up auto-created
7. **Next morning** — come back to Daily Actions, work through your follow-ups

### Key features:
- **Auto follow-ups**: Email sent → 4 day follow-up. Call (spoke) → 5 days. Voicemail → 3 days. No answer → 2 days.
- **Status tracking**: Companies auto-move from Prospect → Contacted when you first reach out
- **Call log**: Full history of every call, visible per company
- **Country filters**: Quick-filter your 3,499 companies by country
- **Track Record**: Editable at any time — the AI references it in every email


## Updating Files Later

If I give you an updated `index.html` or `data.json`:

1. Go to your repo on GitHub
2. Click on the file you want to replace (e.g. `index.html`)
3. Click the **pencil icon** (Edit) or the **...** menu → **Delete file** then re-upload
4. Easier method: Click **Add file** → **Upload files** → drop the new file → it will overwrite the old one
5. Commit the change
6. Wait 1–2 minutes for GitHub Pages to rebuild


## Backing Up Your Data

Your contacts, tasks, call logs, and notes are stored in your **browser's localStorage** — NOT on GitHub. This means:

- ✅ Data persists between sessions in the same browser
- ❌ Data does NOT sync across devices or browsers
- ❌ Clearing browser data will wipe your CRM data

**To back up**: Go to **Settings** → **↓ Export** — saves a JSON file to your computer. Do this regularly (weekly at minimum).

**To restore**: Go to **Settings** → **↑ Import** — load a backup file.

**To start fresh with original companies**: Go to **Settings** → **↺ Reset Seed**.


## Running Locally (Alternative to GitHub Pages)

If you don't want it accessible via a URL at all, you can run it on your own machine:

1. Save all three files in the same folder on your computer
2. Open a terminal/command prompt in that folder
3. Run:
   ```
   python -m http.server 8000
   ```
   (or `python3 -m http.server 8000` on Mac/Linux)
4. Open **http://localhost:8000** in your browser

This keeps everything completely local. You need Python installed (comes pre-installed on Mac, download from python.org for Windows).


## Troubleshooting

| Problem | Fix |
|---------|-----|
| App loads but no companies | Make sure `data.json` is in the same directory as `index.html`. Check browser console (F12) for errors. |
| AI features don't work | Check your API key in Settings. Make sure you have credit on your Anthropic account. |
| "API error 401" | API key is wrong or expired. Generate a new one. |
| Changes disappeared | You probably used a different browser or cleared cache. Import your backup. |
| GitHub Pages not working | Make sure you selected `main` branch and `/ (root)` in Pages settings. Wait 2 minutes and refresh. |
