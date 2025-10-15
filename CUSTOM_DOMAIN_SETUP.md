# Custom Domain Setup for Embecta Web App

## Current Site
Your Embecta web application is live at:
**https://witty-forest-015fdda0f.1.azurestaticapps.net**

---

## What We Need From You

To set up your custom domain (e.g., `embecta.yourdomain.com`), please provide:

### 1. Your Desired Subdomain
Choose what subdomain you'd like to use:
- `embecta.yourdomain.com`
- `training.yourdomain.com`
- `learn.yourdomain.com`
- Or any other subdomain of your choice

### 2. DNS Configuration
Have your IT team create a **CNAME record** with these details:

| Field | Value |
|-------|-------|
| **Type** | CNAME |
| **Name/Host** | `[your-subdomain]` (e.g., `embecta`) |
| **Target/Value** | `witty-forest-015fdda0f.1.azurestaticapps.net` |
| **TTL** | 3600 (or default) |

**Example:** For `embecta.yourdomain.com`:
```
CNAME: embecta → witty-forest-015fdda0f.1.azurestaticapps.net
```

### 3. Confirmation
Once your IT team has created the DNS record, please confirm:
- ✅ The exact subdomain configured (e.g., `embecta.yourdomain.com`)
- ✅ That the CNAME record is live

---

## How We Configure It (Azure Portal)

Once we receive confirmation from you:

### Step 1: Navigate to Static Web App
1. Go to [Azure Portal](https://portal.azure.com)
2. Search for **"Static Web Apps"** or navigate to **Resource Groups** → **embecta-rg** → **embecta-web**

### Step 2: Add Custom Domain
1. In the left menu, click **Custom domains**
2. Click **+ Add**
3. Select **Custom domain on other DNS**
4. Enter the custom domain: `embecta.yourdomain.com` (or whatever subdomain they provided)
5. Click **Next**
6. Click **Add** (Azure will validate the CNAME record)

### Step 3: Wait for SSL Certificate
- Azure automatically provisions a **free SSL certificate**
- This takes **5-10 minutes** after domain validation
- Status will change from "Validating" → "Ready"

### Step 4: Verify
- Visit `https://embecta.yourdomain.com` (or their subdomain)
- Confirm HTTPS is working with valid SSL certificate

---

## Alternative: CLI Method

```bash
# Add custom domain
az staticwebapp hostname set \
  --name embecta-web \
  --resource-group embecta-rg \
  --hostname embecta.yourdomain.com

# Verify custom domain
az staticwebapp hostname show \
  --name embecta-web \
  --resource-group embecta-rg \
  --hostname embecta.yourdomain.com
```

---

## Troubleshooting

### DNS Record Not Found
- Have client verify CNAME record is saved and active
- Use `nslookup embecta.yourdomain.com` to confirm DNS propagation
- DNS changes can take up to 48 hours (typically 15-30 minutes)

### SSL Certificate Stuck
- Wait 5-10 minutes for automatic provisioning
- If stuck after 30 minutes, remove and re-add the custom domain

### CNAME Conflicts
- Ensure subdomain doesn't have existing A or CNAME records
- Client may need to delete old records first

---

## Summary Checklist

**Client Tasks:**
- [ ] Choose subdomain name
- [ ] Create CNAME record: `[subdomain] → witty-forest-015fdda0f.1.azurestaticapps.net`
- [ ] Confirm DNS record is live

**Your Tasks:**
- [ ] Receive subdomain confirmation from client
- [ ] Add custom domain in Azure Portal (Custom domains → Add)
- [ ] Wait for SSL certificate (5-10 minutes)
- [ ] Verify site is live at custom domain with HTTPS
