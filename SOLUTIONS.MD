# Solutions Log

## 2026-03-03 - Migrate PattyKuzbida Wix Site To GitHub Pages

### Problem
- `www.pattykuzbida.com` was still on Wix DNS/hosting and currently returned a Wix 404 page.
- The original content existed in archived snapshots but not in a deployable repository.
- Shutting down Wix without a migration path would break all public routes.

### Solution
- Created a new standalone static website project (`pattykuzbida-site`) with the original route structure from the archived Wix sitemap:
  - `/`
  - `/about-me`
  - `/avamcollection`
  - `/otherworks`
  - `/thewall`
  - `/videos`
  - `/blog`
  - `/post/calm-in-the-chaos`
  - `/post/copy-of-passing-through-town`
  - `/post/the-arctic-experience`
  - `/post/pay-phones`
  - `/post/passing-through-town`
  - `/post/the-mailbox-project`
- Rebuilt each route as a clean static page with shared layout and responsive CSS.
- Downloaded and bundled Wix-hosted media assets locally into `assets/images/` so the site is no longer dependent on Wix-hosted image URLs.
- Added GitHub Pages deployment and custom-domain artifacts:
  - `.github/workflows/deploy-pages.yml`
  - `CNAME` (`www.pattykuzbida.com`)
  - `.nojekyll`
  - `robots.txt`
  - `sitemap.xml`
- Wired contact form submission on `/about-me` using FormSubmit for static hosting compatibility.

### Outcome
- The Patty Kuzbida site is now repository-based and GitHub Pages-ready.
- Core Wix routes are preserved on static hosting.
- The site can be cut over by updating DNS records and then Wix billing can be retired.

## 2026-03-03 - Fix First-Run GitHub Pages Deployment

### Problem
- The first GitHub Actions deploy failed at `actions/configure-pages@v5` because Pages was not enabled yet for the new repository.

### Solution
- Updated `.github/workflows/deploy-pages.yml` to use:
  - `with: enablement: true` under `actions/configure-pages@v5`.
- This allows the workflow to enable Pages automatically on first run before artifact upload/deploy.

### Outcome
- New repositories can deploy without manual Pages pre-configuration.
