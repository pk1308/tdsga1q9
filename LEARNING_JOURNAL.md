# Learning Journal — GA1 Q9: GitHub Pages + CI/CD

## What We Did

Created a GitHub Pages site with CI/CD deployment. The page includes our email address wrapped in Cloudflare obfuscation bypass tags (`<!--email_off-->...<!--/email_off-->`).

## Architecture

```
ga1/9/
├── index.html                          # the page
├── .github/workflows/deploy.yml        # CI/CD pipeline
├── README.md                           # setup instructions
└── LEARNING_JOURNAL.md                 # this file
```

The `deploy.yml` pipeline runs on every push to `main`:
1. `actions/checkout` — clone repo
2. `actions/configure-pages` — set up Pages environment
3. `actions/upload-pages-artifact` — bundle the site
4. `actions/deploy-pages` — deploy to `github.io`

Key config: `permissions: pages: write, id-token: write` and `concurrency: pages` to prevent race conditions between parallel deploys.

## Private vs Public

This repo (`tdst22026`) is private. GitHub Pages on private repos requires a **paid GitHub plan** (Team or Enterprise). The free plan only supports Pages on **public** repos. Solution: create a separate public repo just for this page, copy the files over, and push.

## Cloudflare Email Obfuscation

GitHub Pages sits behind Cloudflare, which auto-obfuscates emails in HTML. The `<!--email_off-->` wrapper tells Cloudflare to skip obfuscation for the enclosed content — required so the grader can see the raw email address in the page source.
