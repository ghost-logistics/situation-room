# 🚀 Star Sentinel Deployment Guide

**Simple deployment for satellite tracking (no configuration required!)**

---

## 📋 Prerequisites

### Required
- Modern web browser

### Optional
- Web hosting account (GitHub Pages, Netlify, or Vercel)

---

## ⏱️ Time Required

- **Download/Clone:** 1 minute
- **Deploy to Hosting:** 5-10 minutes
- **Or Use Locally:** 0 minutes (just open the file!)

**Total:** 5-10 minutes (or instant for local use)

---

## 🎯 Option 1: Use Locally (Instant)

The simplest way to use Star Sentinel:

1. **Extract the ZIP** file
2. **Open `index.html`** in your browser
3. **Done!** Start tracking satellites

No configuration, no deployment, no hassle.

---

## 🌐 Option 2: Deploy to Web (Recommended)

Deploy to free hosting for permanent access from any device.

### Option A: GitHub Pages

#### 2A.1: Create Repository
1. Go to https://github.com/new
2. Repository name: `star-sentinel`
3. Select "Public"
4. Check "Add a README file"
5. Click "Create repository"

#### 2A.2: Upload Files
1. Click "Add file" → "Upload files"
2. Drag all project files into upload area
3. Click "Commit changes"

#### 2A.3: Enable Pages
1. Go to "Settings" tab
2. Click "Pages" (left sidebar)
3. Under "Source": Select "main" branch
4. Click "Save"
5. Wait 1-2 minutes
6. Refresh page
7. Your site URL will appear: `https://YOUR-USERNAME.github.io/star-sentinel/`

---

### Option B: Netlify

#### 2B.1: Create Account
1. Go to https://app.netlify.com/signup
2. Sign up (can use GitHub account)

#### 2B.2: Deploy
1. Click "Add new site" → "Deploy manually"
2. Drag entire project folder into upload area
3. Wait for deployment (30-60 seconds)
4. Your site is live! Copy the URL

---

### Option C: Vercel

#### 2C.1: Install Vercel CLI
```bash
npm install -g vercel
```

#### 2C.2: Deploy
```bash
cd star-sentinel
vercel deploy
```

---

## ✅ Verification

### Test Basic Functionality

1. Open your site (or local file)
2. Wait for satellites to load (2-3 seconds)
3. You should see:
   - 3D Earth with colored dots (satellites)
   - Stats showing "~14,000 satellites tracked"
   - Time slider at bottom
4. Try clicking a satellite
5. Try dragging the time slider

**If this works, deployment is successful!** ✅

---

## 🐛 Troubleshooting

### Issue: Satellites don't load

**Solution:**
- Check internet connection
- Wait 10 seconds (large TLE file downloading)
- Refresh page (Ctrl+F5 or Cmd+Shift+R)
- Check browser console (F12) for errors

### Issue: Site doesn't load

**Solution (GitHub Pages):**
- Wait 5 minutes for deployment to complete
- Check deployment status in repository Settings → Pages

**Solution (Netlify/Vercel):**
- Check deployment logs for errors
- Try redeploying

### Issue: Time slider doesn't work

**Solution:**
- Make sure satellites have loaded first
- Try refreshing the page
- Check browser console for JavaScript errors

---

## 📚 That's It!

No configuration needed. No API keys. No accounts.

Just deploy and track!

---

## 🎓 Advanced: Custom Domain

### GitHub Pages
1. Go to repository Settings → Pages
2. Under "Custom domain", enter your domain
3. Configure DNS at your registrar
4. Wait for DNS propagation

### Netlify
1. Go to Site Settings → Domain Management
2. Click "Add custom domain"
3. Follow DNS instructions

---

## 🔧 Optional Configuration

You can edit `orbital-viz-all-sats.html` to customize:

### Line ~862: CONFIG Object
```javascript
const CONFIG = {
  TLE_REFRESH_INTERVAL: 30 * 60 * 1000,  // 30 minutes
  ENABLE_MANEUVER_DETECTION: true,
  ENABLE_DEBUG_LOGGING: false,
  // etc...
};
```

**Most users won't need to change anything!**

---

## 📊 Monitoring & Maintenance

### Check Usage
No monitoring needed - it's just a static site!

### Update Satellite Data
TLE data auto-updates every 30 minutes. No manual action needed.

---

## 🔄 Updates & Upgrades

### Updating the Application
1. Download latest version
2. Replace old files with new files
3. Re-deploy to hosting

That's it!

---

## ✨ Success!

You now have Star Sentinel deployed!

**Next steps:**
- Open your site
- Track satellites in real-time
- Explore the time travel feature
- Click satellites to see details

**🛰️ Happy Tracking! 🛰️**
