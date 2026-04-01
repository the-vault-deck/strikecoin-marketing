# DEPLOYMENT DIRECTIVE — CHROME CLAUDE
## Connect strikecoin-marketing to thestrikecoin.com via Cloudflare Pages

**Repo:** https://github.com/the-vault-deck/strikecoin-marketing
**Domain:** thestrikecoin.com
**Cloudflare Account:** Emailmainstsolutions@gmail.com

---

### STEP 1 — CREATE CLOUDFLARE PAGES PROJECT

1. Navigate to https://dash.cloudflare.com
2. In the left sidebar, click **Workers & Pages**
3. Click **Create** (or **Create application**)
4. Select the **Pages** tab
5. Click **Connect to Git**
6. Select **GitHub** as the provider
7. Authorize Cloudflare to access the GitHub account if prompted
8. Select the repository: **the-vault-deck/strikecoin-marketing**
9. Configure the build:
   - **Project name:** `strikecoin-marketing`
   - **Production branch:** `main`
   - **Framework preset:** None
   - **Build command:** (leave blank — static site, no build step)
   - **Build output directory:** `/` (root — index.html is at the root)
10. Click **Save and Deploy**
11. Wait for the first deployment to complete

---

### STEP 2 — ADD CUSTOM DOMAIN

1. After deployment succeeds, go to the **strikecoin-marketing** Pages project
2. Click the **Custom domains** tab
3. Click **Set up a custom domain**
4. Enter: `thestrikecoin.com`
5. Click **Continue**
6. Cloudflare will auto-configure DNS if the domain is already on this Cloudflare account
   - If it shows a CNAME record to add, confirm/approve it
7. Also add `www.thestrikecoin.com` as a second custom domain (optional but recommended)
8. Wait for SSL certificate to provision (usually under 5 minutes)

---

### STEP 3 — VERIFY

1. Navigate to https://thestrikecoin.com
2. Confirm the page loads with:
   - "THE STRIKE COIN" header
   - "APPEND-ONLY REALITY TESTING" subtitle
   - Five module blocks
   - "INACTION IS RECORDED" section
   - Single CTA button: "INITIALIZE SYSTEM AUDIT"
3. Click the CTA — confirm it redirects to https://strikecoin.ai/start
4. Check https://www.thestrikecoin.com redirects or also serves the page

---

### DNS NOTE

If thestrikecoin.com is already on this Cloudflare account (same account: 488d64730876c2425890bd23baada1ff), the DNS records will be auto-configured when you add the custom domain in Step 2.

If the domain is on a different Cloudflare account or external registrar, you will need to manually add:
- **CNAME** `thestrikecoin.com` → `strikecoin-marketing.pages.dev`
- **CNAME** `www` → `strikecoin-marketing.pages.dev`

---

### FAILURE CHECKS

- If build fails: verify build output directory is `/` not `dist` or `public`
- If domain shows Cloudflare default page: DNS propagation may need a few minutes
- If SSL error: wait for certificate provisioning (up to 15 minutes)
