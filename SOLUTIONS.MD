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
