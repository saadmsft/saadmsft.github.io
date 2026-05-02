# Personal Site Deployment Guide

## Status: ✅ Deploying to GitHub Pages

**Hosting:** GitHub Pages (free, automated deployment via GitHub Actions)

**Site URL:** Will be `https://<username>.github.io/<repo-name>` (can add custom domain later)

---

## Deployment Process

### 1. GitHub Repository Setup

The site is configured for GitHub Pages deployment with automated builds:

- ✅ Git repository initialized
- ✅ GitHub Actions workflow created (`.github/workflows/deploy.yml`)
- ⏳ Push to GitHub repository (in progress)
- ⏳ Enable GitHub Pages in repository settings

### 2. Automated Deployment

Once pushed, GitHub Actions will automatically:
1. Build the site on every push to `main`
2. Deploy to GitHub Pages
3. Site will be live at `https://<username>.github.io/<repo-name>`

### 3. Custom Domain (Optional - Can Add Later)

To use a custom domain (e.g., `saadmahmood.com`):

1. **Purchase domain** (options: Namecheap, Cloudflare, Google Domains)
   - Cost: ~$12-15/year for .com

2. **Add to GitHub Pages:**
   - Go to repo Settings → Pages → Custom domain
   - Enter domain: `saadmahmood.com`
   - This creates a `CNAME` file in repo

3. **Configure DNS at registrar:**
   - Add A records pointing to GitHub Pages IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Or add CNAME record: `<username>.github.io`

4. **Enable HTTPS** (auto-provisioned by GitHub)

### 4. Post-Launch Verification

After deployment:
- [ ] Site is live and accessible
- [ ] Run Lighthouse audit (target: SEO score 95+)
- [ ] Submit sitemap to Google Search Console
- [ ] Validate schema.org in Google Rich Results Test
- [ ] Monitor Google indexing (7-day target)

---

## 4. Known Gaps (v2 Scope)

- **OG image:** Need professional headshot or branded graphic (1200x630px)
- **Content:** Placeholder text awaiting baseline audit results ([SAAA-2](/SAAA/issues/SAAA-2))
- **LinkedIn integration:** No cross-posting yet (future feature)
- **Analytics:** No tracking installed (add Google Analytics post-launch)

---

## 5. Cost Summary

| Item | Annual Cost |
|------|------------|
| Domain (saadmahmood.com) | $12-15 |
| Hosting (Vercel free tier) | $0 |
| SSL Certificate | $0 (auto) |
| **Total** | **$12-15/year** |

Under budget ($20/year threshold).

---

## Next Actions

**CEO:**
1. Approve domain: saadmahmood.com (or alternative)
2. Choose hosting platform: Vercel (recommended) or Cloudflare Pages
3. Authorize domain purchase (provide registrar preference: Namecheap, Cloudflare, Google Domains)

**FoundingEngineer (me):**
1. Purchase domain (after CEO approval)
2. Push to GitHub
3. Deploy to approved platform
4. Configure DNS
5. Submit to Google Search Console
6. Monitor indexing
7. Update content from SAAA-2 results when ready
