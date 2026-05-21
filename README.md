# Owl Play With You — owlplaywithyou.com

Static site for the Owl Play With You indie game studio.

## Project Structure

```
owlplaywithyou/
├── index.html       ← main page
├── style.css        ← all styles
├── script.js        ← scroll reveal + nav behavior
├── _redirects       ← Cloudflare Pages routing
├── assets/
│   └── owl.png      ← mascot (replace with any updated version)
└── README.md
```

---

## Before You Deploy — Update Placeholders

Search for `TODO` comments in `index.html` and fill in:
- Your actual Steam store URL for Tether
- Your actual itch.io URL for Tether
- Your actual contact email

---

## Deploy to Cloudflare Pages

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "initial commit"
git remote add origin https://github.com/YOUR_USERNAME/owlplaywithyou.git
git push -u origin main
```

### 2. Create a Cloudflare Pages project

1. Go to [dash.cloudflare.com](https://dash.cloudflare.com)
2. Click **Workers & Pages** → **Create application** → **Pages**
3. Connect your GitHub account and select your repo
4. Build settings:
   - **Framework preset**: None
   - **Build command**: *(leave empty)*
   - **Build output directory**: `/` (or leave as default)
5. Click **Save and Deploy**

### 3. Connect owlplaywithyou.com

1. In your Pages project, go to **Custom domains**
2. Add `owlplaywithyou.com` and `www.owlplaywithyou.com`
3. Cloudflare will auto-configure DNS since you manage the domain there

---

## Redirect kylebrickgames.com → owlplaywithyou.com

Do this in **Cloudflare Dashboard** (not in code):

1. Go to your `kylebrickgames.com` zone
2. **Rules** → **Redirect Rules** → **Create rule**
3. Set:
   - **When**: hostname `kylebrickgames.com` OR `www.kylebrickgames.com`
   - **Then**: Static redirect → `https://owlplaywithyou.com` → **301**
4. Save and deploy

That's it — any visitor to kylebrickgames.com lands on owlplaywithyou.com automatically.

---

## Updating the Site

Edit files locally, then:

```bash
git add .
git commit -m "your update message"
git push
```

Cloudflare Pages auto-deploys on every push. Live in ~30 seconds.
