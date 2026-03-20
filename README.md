# BidDraft AI

**AI-powered bid writing for South Florida contractors.**  
Stop spending 3 hours writing bids. Get a professional draft in 2 minutes.

🌐 **Live site:** https://YOUR_GITHUB_USERNAME.github.io/biddraft

---

## What This Is

A single-page landing site for BidDraft AI — a free beta tool that generates professional contractor bid proposals for Broward County / South Florida contractors.

Includes:
- Hero section with sample bid preview
- 5 live sample bids (Roofing, Bathroom Remodel, HVAC, Electrical, Deck)
- South Florida-specific selling points (Broward permits, Miami-Dade NOA, FPL language)
- Lead capture form → Tally.so

---

## How To Update

The entire site is one file: `index.html`.

**To change text or content:**  
Edit `index.html` directly, then:
```bash
git add index.html
git commit -m "Update: [describe change]"
git push
```
Site updates within 60 seconds.

**To change the Tally form URL:**  
Search for `tally.so/r/` in `index.html` and update the form ID.

**To change contact info:**  
Search for `YOUR_EMAIL` and `YOUR-NUMBER` in `index.html`.

---

## Tech Stack

- Plain HTML + CSS + vanilla JavaScript
- No build tools, no npm, no dependencies
- Google Fonts (Barlow Condensed, Barlow, Roboto Mono)
- Hosted free on GitHub Pages

---

## Local Preview

```bash
# Option 1: Python (if installed)
python3 -m http.server 8000
# Open: http://localhost:8000

# Option 2: VS Code Live Server extension
# Right-click index.html → "Open with Live Server"

# Option 3: Just open index.html in a browser
open index.html
```

---

## Deployment

Hosted on GitHub Pages. Any push to `main` branch auto-deploys within ~60 seconds.

To re-enable Pages if it ever gets turned off:  
Settings → Pages → Source: Deploy from branch → main → / (root) → Save

---

Built for South Florida contractors · Sunrise, FL 33323
