# Deployment Guide

## ✅ Current Status: DEPLOYED

**Live Site:** https://saadmsft.github.io/

**Repository:** https://github.com/saadmsft/saadmsft.github.io

---

## Hosting: GitHub Pages (Free)

The site is hosted on GitHub Pages with automated deployment via GitHub Actions.

### How It Works

1. Push to `main` branch
2. GitHub Actions runs build workflow
3. Site deploys automatically to `saadmsft.github.io`
4. Live within 1-2 minutes

### Monitoring Deployments

- View workflow runs: https://github.com/saadmsft/saadmsft.github.io/actions
- Latest deployment shows green checkmark when successful
- Click on any run to see build logs

---

## Adding a Custom Domain (Optional)

Currently using: `saadmsft.github.io`

To use a custom domain (e.g., `saadmahmood.com`):

### Step 1: Purchase Domain

**Cost:** ~$12-15/year for `.com`

**Recommended Registrars:**
- Namecheap (good UI, competitive pricing)
- Cloudflare (best DNS, domain transfer only)
- Google Domains / Squarespace (now merged)

### Step 2: Configure GitHub Pages

1. Go to: https://github.com/saadmsft/saadmsft.github.io/settings/pages
2. Under "Custom domain", enter your domain: `saadmahmood.com`
3. Check "Enforce HTTPS" (wait 24hrs for cert)
4. Save

This creates a `CNAME` file in the repo.

### Step 3: Configure DNS at Registrar

**Option A: A Records (Apex domain)**

If using `saadmahmood.com`:

```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

**Option B: CNAME (www subdomain)**

If using `www.saadmahmood.com`:

```
Type: CNAME
Name: www
Value: saadmsft.github.io
```

**TTL:** 3600 (1 hour) or default

### Step 4: Update Site Config

Edit `astro.config.mjs`:

```javascript
export default defineConfig({
  site: 'https://saadmahmood.com', // Change from saadmsft.github.io
  integrations: [sitemap()],
  // ...
});
```

Commit and push:

```bash
git add astro.config.mjs
git commit -m "Update site URL to custom domain"
git push
```

### Step 5: Verify

- DNS propagation: 5-60 minutes
- HTTPS certificate: up to 24 hours
- Check status: GitHub repo Settings → Pages

---

## SEO Setup

### Google Search Console

1. Go to: https://search.google.com/search-console
2. Add property: `https://saadmsft.github.io` (or custom domain)
3. Verify ownership (DNS or HTML file)
4. Submit sitemap: `https://saadmsft.github.io/sitemap-index.xml`

### Bing Webmaster Tools

1. Go to: https://www.bing.com/webmasters
2. Import from Google Search Console (easiest)
3. Or manually add and verify

### Lighthouse Audit

Run in Chrome DevTools:

1. Open site in Chrome
2. DevTools → Lighthouse tab
3. Select "SEO" category
4. Run audit
5. **Target:** 95+ score

### Schema.org Validation

Validate structured data:

1. Go to: https://validator.schema.org/
2. Enter URL: `https://saadmsft.github.io/`
3. Check for errors
4. Or use: https://search.google.com/test/rich-results

---

## Content Updates

### Direct Editing on GitHub

1. Go to: https://github.com/saadmsft/saadmsft.github.io
2. Navigate to file (e.g., `src/pages/index.astro`)
3. Click pencil icon to edit
4. Make changes
5. Commit directly to `main`
6. Site auto-deploys in 1-2 minutes

### Local Development

```bash
# Clone repo
git clone https://github.com/saadmsft/saadmsft.github.io.git
cd saadmsft.github.io

# Install dependencies
npm install

# Start dev server
npm run dev
# Visit: http://localhost:4321

# Make changes, then:
git add .
git commit -m "Update content"
git push
```

---

## Maintenance

### Monitoring

- **Uptime:** GitHub Pages has 99.9%+ uptime
- **Status:** https://www.githubstatus.com/
- **Analytics:** Add Google Analytics if needed

### Updates

**Astro Framework:**

```bash
npm update astro @astrojs/sitemap
npm run build  # Test locally
git commit -am "Update Astro"
git push
```

**Dependencies:**

GitHub Dependabot is enabled and will create PRs for updates.

---

## Cost Summary

| Item | Annual Cost |
|------|-------------|
| GitHub Pages hosting | $0 |
| GitHub Actions (build) | $0 (free tier) |
| Custom domain (optional) | $12-15 |
| SSL Certificate | $0 (auto) |
| **Total** | **$0-15/year** |

---

## Troubleshooting

### Site not updating after push

1. Check Actions tab: https://github.com/saadmsft/saadmsft.github.io/actions
2. Look for failed workflows (red X)
3. Click on run to see error logs
4. Common issues:
   - Build error (check Node.js version)
   - Syntax error in code
   - Missing dependency

### 404 errors

1. Clear browser cache
2. Check GitHub Pages settings enabled
3. Verify `index.html` exists in `dist/` after build
4. Wait 5-10 minutes for DNS propagation

### Custom domain not working

1. Verify DNS records at registrar
2. Check CNAME file exists in repo
3. Wait for DNS propagation (up to 48hrs, usually <1hr)
4. Check GitHub Pages status for SSL cert

### Build failures

1. Check Node.js version in workflow (should be 22+)
2. Test build locally: `npm run build`
3. Check for syntax errors
4. Review Actions logs

---

## Support

- **GitHub Pages Docs:** https://docs.github.com/en/pages
- **Astro Docs:** https://docs.astro.build/
- **GitHub Issues:** Create issue in repo for bugs

---

Last updated: 2026-05-02
