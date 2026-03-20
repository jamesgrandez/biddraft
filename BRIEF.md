# BidDraft AI — Claude Code Deployment Brief

## What This Is
A single-page marketing + lead capture website for **BidDraft AI** — an AI bid-writing tool for South Florida contractors. The site needs to go live on GitHub Pages as a free static website.

## Your Job (Claude Code)
1. **Replace all placeholder values** in `index.html` (listed below)
2. **Wire up the lead capture form** to redirect to the Tally form URL
3. **Create the GitHub repository** and push the site
4. **Enable GitHub Pages** so the site is live at `https://USERNAME.github.io/biddraft`
5. **Test the live URL** and confirm it loads correctly

---

## Step-by-Step Instructions

### Step 1 — Replace Placeholders in index.html

Open `index.html` and find/replace every instance of these placeholders:

| Placeholder | Replace With |
|---|---|
| `YOUR_EMAIL@gmail.com` | The actual Gmail address created for BidDraft AI |
| `(954) YOUR-NUMBER` | The actual phone number to use for follow-ups |
| `YOUR_GITHUB_USERNAME.github.io/biddraft` | Actual GitHub username + `/biddraft` |
| `TALLY_FORM_ID` | The Tally.so form ID (from the Tally form URL) |

**How to find the Tally form ID:**  
The Tally form URL looks like: `https://tally.so/r/XXXXXXX`  
The `XXXXXXX` part is the form ID.

### Step 2 — Wire Up the Form

In `index.html`, find the `handleSubmit` function (search for `function handleSubmit`).

Replace the entire function with this:

```javascript
function handleSubmit(e) {
  e.preventDefault();
  // Collect form data
  const name = e.target.querySelector('input[type="text"]').value;
  const email = e.target.querySelector('input[type="email"]').value;
  const trade = e.target.querySelector('select').value;
  // Redirect to Tally form with pre-filled values
  const tallyUrl = `https://tally.so/r/TALLY_FORM_ID?name=${encodeURIComponent(name)}&email=${encodeURIComponent(email)}&trade=${encodeURIComponent(trade)}`;
  window.open(tallyUrl, '_blank');
  // Show success message
  document.getElementById('bidForm').style.display = 'none';
  document.getElementById('successMsg').classList.add('show');
}
```

Replace `TALLY_FORM_ID` with the actual ID.

### Step 3 — Create GitHub Repository

```bash
# Initialize git in the biddraft-site folder
cd /path/to/biddraft-site
git init
git add .
git commit -m "Initial commit — BidDraft AI landing page"

# Create repo on GitHub (requires GitHub CLI or manual creation)
# Option A: GitHub CLI
gh repo create biddraft --public --source=. --push

# Option B: Manual
# Go to github.com → New Repository → Name: "biddraft" → Public → Create
# Then run:
git remote add origin https://github.com/USERNAME/biddraft.git
git branch -M main
git push -u origin main
```

### Step 4 — Enable GitHub Pages

**Via GitHub CLI:**
```bash
gh api repos/USERNAME/biddraft/pages \
  --method POST \
  --field source[branch]=main \
  --field source[path]=/
```

**Via GitHub website (if CLI doesn't work):**
1. Go to: `https://github.com/USERNAME/biddraft`
2. Click **Settings** tab
3. Click **Pages** in the left sidebar
4. Under "Source" → select **Deploy from a branch**
5. Branch: **main** | Folder: **/ (root)**
6. Click **Save**

The site will be live at: `https://USERNAME.github.io/biddraft` within 2–3 minutes.

### Step 5 — Verify

1. Wait 2–3 minutes after enabling Pages
2. Open `https://USERNAME.github.io/biddraft` in a browser
3. Check that:
   - [ ] Page loads without errors
   - [ ] Nav logo shows "BidDraft AI"
   - [ ] All 5 sample bid tabs work (Roofing, Bathroom, HVAC, Electrical, Deck)
   - [ ] The form fields are visible and functional
   - [ ] On mobile (resize browser) — page is readable
   - [ ] Clicking "Get Free Bid Draft" in nav scrolls to the form
4. If anything is broken, fix and push again:
   ```bash
   git add .
   git commit -m "Fix: [describe what you fixed]"
   git push
   ```
   Pages will update within 60 seconds.

---

## File Structure
```
biddraft-site/
├── index.html      ← The entire site (single file, self-contained)
├── README.md       ← How to update the site
└── BRIEF.md        ← This file (for Claude Code)
```

No build tools. No npm. No dependencies. Just one HTML file. GitHub Pages serves it directly.

---

## What the Site Does

**Sections (top to bottom):**
1. **Fixed nav** — Logo + "South Florida Beta" badge + CTA button
2. **Hero** — Headline, subheadline, 3 stats, sample bid preview (desktop only)
3. **Trust bar** — 6 trades listed
4. **Problem section** — 3 pain points for contractors
5. **How It Works** — 3-step process
6. **Sample Bids** — 5 tabbed bid examples (Roofing, Bathroom, HVAC, Electrical, Deck)
7. **South Florida Specific** — 4 local selling points
8. **Lead Capture Form** — Name, email, phone, trade, job description, job size
9. **Footer** — Contact info, disclaimer

**The form** collects contractor info and redirects to Tally.so where the actual submission is stored and email notifications are sent.

---

## Common Issues & Fixes

**404 on GitHub Pages:**  
Make sure the repo is **public** and Pages source is set to `main` branch, `/ (root)` folder.

**Fonts not loading:**  
The page loads Google Fonts from `fonts.googleapis.com`. This requires internet — works fine on GitHub Pages.

**Form not redirecting:**  
Make sure `TALLY_FORM_ID` was replaced with the real ID. Check the Tally URL format.

**Page looks broken on mobile:**  
The page is responsive. If it looks wrong, check that `<meta name="viewport">` tag is in the `<head>` (it is by default).

---

## After It's Live

Once the URL is confirmed working, the owner will:
1. Print the URL on business cards (via Canva)
2. Share the URL in contractor community posts
3. Text the URL to contractors they meet in person

The Tally form handles all lead collection and email notifications.
