# GA1 Q9 — GitHub Pages Deployment

## Files

- `index.html` — the page showcasing work, with email obfuscation wrapper
- `.github/workflows/deploy.yml` — CI/CD pipeline for GitHub Pages
- `LEARNING_JOURNAL.md` — what we learned

## Setup for a new public repo

1. Create a **public** GitHub repo (private repos need paid plan for Pages)
2. Copy these files to the repo:
   ```
   repo/
   ├── index.html
   └── .github/workflows/deploy.yml
   ```
   The `.github/workflows/` folder must be at the **repo root**.
3. Push to `main`
4. GitHub Pages deploys automatically via the workflow
5. URL: `https://<user>.github.io/<repo>/`

## Email

The email is wrapped in Cloudflare obfuscation bypass tags:
```html
<!--email_off-->23f2000254@ds.study.iitm.ac.in<!--/email_off-->
```
