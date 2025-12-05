# Railway.app Deployment Guide

## Quick Deployment Steps

### 1. Push to GitHub (if you want to use GitHub integration)

```bash
git add .
git commit -m "Add Railway deployment configuration"
git push origin main
```

### 2. Deploy to Railway

**Option A: Deploy from GitHub (Recommended)**
1. Go to https://railway.app/new
2. Sign in with GitHub
3. Click "Deploy from GitHub repo"
4. Select your forked `ai-strategy-factory` repository
5. Railway will auto-detect the configuration

**Option B: Deploy from Local (Using Railway CLI)**
1. Install Railway CLI: `npm install -g @railway/cli`
2. Login: `railway login`
3. Initialize: `railway init`
4. Deploy: `railway up`

### 3. Set Environment Variables

In Railway Dashboard → Your Project → Variables tab, add:

```
PERPLEXITY_API_KEY=your-perplexity-api-key-here
GEMINI_API_KEY=your-gemini-api-key-here
```

### 4. Connect Your Hostinger Domain

#### In Railway Dashboard:
1. Go to Settings → Domains
2. Click "Custom Domain"
3. Enter your domain (e.g., `strategyfactory.yourdomain.com`)
4. Railway will show you DNS records to add

#### In Hostinger DNS:
1. Log in to Hostinger
2. Go to Domains → Manage → DNS Records
3. Add the CNAME record provided by Railway:
   - **Type**: CNAME
   - **Name**: strategyfactory (or @ for root domain)
   - **Value**: [Railway provides this, e.g., `your-app.up.railway.app`]
   - **TTL**: 3600

### 5. SSL Certificate

Railway automatically provisions SSL certificates for custom domains. Your site will be accessible via HTTPS within a few minutes.

## Deployment Files Created

- **Procfile** - Tells Railway how to start the app
- **railway.json** - Railway-specific configuration
- **runtime.txt** - Specifies Python version
- **.railwayignore** - Files to exclude from deployment

## Costs

Railway offers:
- **Free tier**: $5 of credit per month (usually enough for small projects)
- **Pro plan**: $20/month with $5 included credit

Your app should run well within the free tier for moderate usage.

## Troubleshooting

**Build fails?**
- Check the build logs in Railway dashboard
- Ensure all dependencies are in requirements.txt

**App crashes on startup?**
- Check environment variables are set
- Review the deployment logs

**Domain not working?**
- DNS changes can take 1-48 hours to propagate
- Verify CNAME record is correct in Hostinger

## Support

- Railway Docs: https://docs.railway.app
- Railway Discord: https://discord.gg/railway
