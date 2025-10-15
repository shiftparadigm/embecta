# Custom Domain Setup for Embecta Web App

## Overview
Your Embecta web application is currently live at:
**https://witty-forest-015fdda0f.1.azurestaticapps.net**

To make it accessible via your own custom domain (e.g., `embecta.yourdomain.com`), please follow the steps below.

---

## Step 1: Choose Your Subdomain

Decide what subdomain you'd like to use. Common options include:
- `embecta.yourdomain.com`
- `training.yourdomain.com`
- `learn.yourdomain.com`
- Or any other subdomain of your choice

**Please confirm with us what subdomain name you'd like to use.**

---

## Step 2: Access Your DNS Management

You'll need access to your domain's DNS management panel. This is typically found through:
- Your domain registrar (GoDaddy, Namecheap, Google Domains, etc.)
- Your hosting provider
- Your IT department (if managed internally)

If you're unsure where your DNS is managed, contact your domain registrar or IT support.

---

## Step 3: Create a CNAME Record

Once you have access to your DNS management panel, create a new **CNAME record** with the following details:

### DNS Record Details:

| Record Type | Name/Host | Value/Target | TTL |
|-------------|-----------|--------------|-----|
| CNAME | `[your-chosen-subdomain]` | `witty-forest-015fdda0f.1.azurestaticapps.net` | 3600 (or default) |

### Example:
If you chose `embecta.yourdomain.com`:

- **Type:** CNAME
- **Name:** `embecta`
- **Value:** `witty-forest-015fdda0f.1.azurestaticapps.net`
- **TTL:** 3600 seconds (or leave as default)

### Important Notes:
- Some DNS providers use `Name` or `Host`, while others use `Alias` for the subdomain field
- Some DNS providers automatically append your domain name, so you may only need to enter the subdomain part (e.g., just `embecta` instead of `embecta.yourdomain.com`)
- DNS changes can take 24-48 hours to propagate, though they often complete within 15-30 minutes

---

## Step 4: Save and Confirm

After creating the CNAME record:

1. **Save** your DNS changes
2. **Notify us** with the exact subdomain you configured (e.g., `embecta.yourdomain.com`)
3. We will then add your custom domain to the Azure Static Web App and enable HTTPS

---

## Step 5: Wait for Propagation

Once we've added your custom domain on our end:
- DNS propagation typically takes **15-30 minutes** but can take up to **48 hours**
- Azure will automatically provision a free SSL certificate for HTTPS
- SSL certificate provisioning takes **3-5 minutes** after DNS propagation

---

## Verification

To verify your DNS record is configured correctly, you or we can run:

```bash
nslookup embecta.yourdomain.com
```

It should return the Azure Static Web App hostname: `witty-forest-015fdda0f.1.azurestaticapps.net`

---

## Common DNS Provider Instructions

### GoDaddy
1. Log in to GoDaddy
2. Go to **My Products** > **DNS**
3. Click **Add** under DNS Records
4. Select **CNAME** type
5. Enter your subdomain name and target

### Cloudflare
1. Log in to Cloudflare
2. Select your domain
3. Go to **DNS** tab
4. Click **Add record**
5. Select **CNAME**, enter name and target
6. **Important:** Set proxy status to **DNS only** (gray cloud, not orange)

### Google Domains
1. Log in to Google Domains
2. Select your domain
3. Click **DNS** in the left menu
4. Scroll to **Custom resource records**
5. Add CNAME record with subdomain and target

### Namecheap
1. Log in to Namecheap
2. Go to **Domain List** > **Manage**
3. Click **Advanced DNS**
4. Click **Add New Record**
5. Select **CNAME Record**, enter host and target

---

## Need Help?

If you encounter any issues:
- Take a screenshot of your DNS management panel
- Note any error messages
- Contact us with your subdomain choice and screenshots

We're here to help guide you through the process!

---

## Summary Checklist

- [ ] Choose subdomain name
- [ ] Access DNS management panel
- [ ] Create CNAME record pointing to `witty-forest-015fdda0f.1.azurestaticapps.net`
- [ ] Save DNS changes
- [ ] Notify us with your chosen subdomain
- [ ] Wait for DNS propagation (15-30 minutes)
- [ ] We'll add custom domain to Azure and enable HTTPS
- [ ] Wait for SSL certificate provisioning (3-5 minutes)
- [ ] Your site is live on your custom domain! 🎉
