# Chandrakanth K — Portfolio Website

Professional portfolio website. Static HTML/CSS/JS — no build step required.

## Project Structure

```
portfolio/
├── index.html                  # Main website
├── vercel.json                 # Vercel deployment config
├── assets/
│   └── Chandrakanth_K_Resume.pdf   # ← place your resume here
└── README.md
```

---

## Step-by-Step Deployment Guide

### Step 1 — Add your resume

Place your resume PDF inside the `assets/` folder and name it exactly:
```
assets/Chandrakanth_K_Resume.pdf
```

---

### Step 2 — Create a GitHub repository

1. Go to https://github.com and sign in
2. Click **New repository** (top right → `+` icon)
3. Name it: `portfolio` (or `chandrakanth-portfolio`)
4. Set it to **Public**
5. Do NOT initialise with README (you already have files)
6. Click **Create repository**

---

### Step 3 — Push your code to GitHub

Open terminal in the `portfolio/` folder and run:

```bash
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/portfolio.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your actual GitHub username.

---

### Step 4 — Deploy to Vercel (recommended)

Vercel gives you a free custom subdomain and automatic HTTPS.

1. Go to https://vercel.com and sign in with GitHub
2. Click **Add New → Project**
3. Select your `portfolio` repository
4. Vercel auto-detects it as a static site — no settings to change
5. Click **Deploy**
6. In ~30 seconds your site is live at:
   `https://portfolio-YOUR_USERNAME.vercel.app`

#### Optional: Connect a custom domain
1. In Vercel dashboard → your project → **Settings → Domains**
2. Add your domain (e.g. `chandrakanth.dev`)
3. Update your domain's DNS with the CNAME Vercel gives you
4. Done — HTTPS is automatic

---

### Step 5 — Embed your Hugging Face chatbot

Once your Gradio chatbot is deployed on Hugging Face Spaces:

1. Go to your HF Space page
2. Click the **Embed** button (or use the direct URL)
3. Copy the Space URL — it looks like:
   `https://YOUR-HF-USERNAME-YOUR-SPACE-NAME.hf.space`
4. Open `index.html` and find this comment near the bottom:
   ```html
   <!-- REPLACE THIS WITH YOUR HUGGING FACE EMBED IFRAME -->
   ```
5. Replace the placeholder div with:
   ```html
   <iframe
     src="https://YOUR-HF-USERNAME-YOUR-SPACE-NAME.hf.space"
     width="100%"
     height="380"
     style="border:none;border-radius:10px"
   ></iframe>
   ```
6. Commit and push:
   ```bash
   git add index.html
   git commit -m "Add chatbot embed"
   git push
   ```
7. Vercel auto-redeploys in ~20 seconds

---

### Step 6 — Auto-deploy on every update

Every time you push to GitHub, Vercel automatically redeploys. Workflow:

```bash
# Make changes to index.html
git add .
git commit -m "Update skills section"
git push
# Site is live in ~30 seconds
```

---

## How to Update the Website

| What to update | Where to edit |
|---|---|
| Your bio / intro text | `index.html` → `#hero` section |
| Skills | `index.html` → `#skills` section |
| Add a new job | `index.html` → `#experience` section, copy a `.timeline-item` block |
| Add a new project | `index.html` → `#projects` section, copy a `.project-card` block |
| Update certifications | `index.html` → `#certifications` section |
| Contact email / LinkedIn | `index.html` → `#contact` section |
| Resume file | Replace `assets/Chandrakanth_K_Resume.pdf` |

After any edit → `git add . && git commit -m "your message" && git push`

---

## Local Preview

No build step needed. Just open the file directly:

```bash
# Option 1 — open directly in browser
open index.html

# Option 2 — use Python's built-in server (recommended, avoids CORS issues)
python -m http.server 3000
# then go to http://localhost:3000
```

---

## Tech Stack

- Pure HTML5 / CSS3 / Vanilla JS — zero dependencies, zero build step
- Fonts: Syne (display) + DM Sans (body) + DM Mono (code labels) via Google Fonts
- Animations: CSS transitions + IntersectionObserver for scroll reveals
- Hosting: Vercel (free tier)
- Chatbot: Hugging Face Spaces embedded via iframe
