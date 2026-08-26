# Deploying goforecreative.com — GitHub + Cloudflare Pages

Everything in this folder is the live site. Upload the folder contents to a repo, connect Cloudflare, point the domain. About 20 minutes total.

## What's in here

| File | What it does |
|---|---|
| `index.html` | The site. Must be named exactly this. |
| `404.html` | Branded "page not found" page. Cloudflare uses it automatically. |
| `og-image.png` | The preview image when someone shares your link on social or in a text. |
| `favicon.svg` | Browser tab icon. |
| `apple-touch-icon.png` | Icon when someone saves the site to a phone home screen. |
| `robots.txt` | Tells search engines they can index the site. |
| `sitemap.xml` | Helps Google find your page. |
| `_headers` | Security headers and caching rules. Cloudflare Pages reads this automatically. |
| `DEPLOY.md` | This file. Safe to delete after setup. |

---

## Step 1 — Put it on GitHub

**Option A: the web (no command line)**

1. Go to github.com and click **New repository**
2. Name it `goforecreative` — set it to **Private** if you don't want the code public
3. Do NOT check "Add a README"
4. On the next screen click **uploading an existing file**
5. Drag in every file from this folder. Don't drag the folder itself — drag the files inside it, so `index.html` sits at the top level of the repo
6. Click **Commit changes**

**Option B: command line**

```bash
cd path/to/fore-site
git init
git add .
git commit -m "Launch FORE Creative Co. site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/goforecreative.git
git push -u origin main
```

**Important:** `index.html` must be at the root of the repo, not inside a subfolder. If GitHub shows you a `fore-site` folder you have to click into to see `index.html`, the deploy will show a blank page.

---

## Step 2 — Connect Cloudflare Pages

1. Log in to Cloudflare → **Workers & Pages** in the left sidebar
2. **Create** → **Pages** → **Connect to Git**
3. Authorize GitHub, pick your `goforecreative` repo
4. On the build settings screen:
   - **Framework preset:** None
   - **Build command:** leave blank
   - **Build output directory:** `/` (just a slash)
5. Click **Save and Deploy**

It builds in under a minute. You'll get a temporary URL like `goforecreative.pages.dev`.

**Test on that URL before pointing your domain at it.** Submit the contact form and confirm the email arrives.

---

## Step 3 — Point your domain at it

You need `goforecreative.com` registered and added to Cloudflare as a site first. If it's registered somewhere else (GoDaddy, Namecheap), you'll change the nameservers at that registrar to the two Cloudflare gives you. That can take a few hours to take effect.

Once the domain is in your Cloudflare account:

1. Open your Pages project → **Custom domains** tab
2. **Set up a domain** → enter `goforecreative.com`
3. Cloudflare adds the DNS record for you. Click through to confirm
4. Repeat for `www.goforecreative.com` so both work

SSL turns on automatically. Give it 5–15 minutes for the certificate.

---

## Step 4 — Confirm it works

- [ ] Site loads at goforecreative.com with the padlock icon
- [ ] www version also loads
- [ ] Contact form submits and the email hits your inbox
- [ ] Phone number and email links work on a real phone
- [ ] Paste the URL into a text message or Slack — the preview image should show
- [ ] Visit goforecreative.com/nothing — you should see the branded 404 page

---

## Making changes later

Edit `index.html` in GitHub (pencil icon on the file), commit, and Cloudflare redeploys in about 30 seconds. No extra steps.

If you'd rather I make the edits, send me the current file and I'll hand it back updated.

---

## Still placeholder content

Fix these before you promote the site:

- **Testimonials** in the Studio section — three fake quotes with fake names. Replace or remove them.
- **"Remote-first · U.S. based"** and **"Mon–Fri · 8a–5p CT"** in the contact block.
- The og-image and sitemap assume the domain is `goforecreative.com`. If you use a different domain, the social preview and canonical tag need updating.

## One nice-to-have

Cloudflare Pages includes free **Web Analytics** — no cookie banner needed, and it doesn't slow the site down. Turn it on under your Pages project settings if you want to see traffic.
