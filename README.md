# Situation Room - Website Deployment Guide

This is the **static website version** of Situation Room. It runs entirely in the browser with no backend required.

## Quick Start (Local Testing)

### Option 1: Using npm (Recommended)
```bash
npm start
```
Opens at http://localhost:8080

### Option 2: Using Python
```bash
# Python 3
python -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080
```
Then open http://localhost:8080

### Option 3: Using Node.js http-server directly
```bash
npx http-server . -p 8080 -o
```

## File Structure

```
situation-room-website/
├── index.html                    # Main entry point
├── orbital-viz-all-sats.html    # Orbital Sentinel tab
├── global-guard.html            # Global Guard tab (NASA GIBS)
├── osint-observer.html          # OSINT Observer tab
├── package.json                 # For local dev server
└── README.md                    # This file
```

## Deployment Options

### 🚀 Option 1: GitHub Pages (FREE, Easy)

**Best for:** Public projects, simple deployment

**Steps:**
1. Create a GitHub repository
2. Push all files to the repo:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/situation-room.git
   git push -u origin main
   ```
3. Go to repo Settings → Pages
4. Source: Deploy from branch `main` / `root`
5. Save and wait ~1 minute
6. Access at: `https://YOUR_USERNAME.github.io/situation-room/`

**Pros:** Free, automatic SSL, GitHub integration
**Cons:** Public only (unless Pro account)

---

### 🌐 Option 2: Netlify (FREE, Best for Web Apps)

**Best for:** Modern web apps, continuous deployment

**Steps:**
1. Sign up at https://netlify.com
2. Drag & drop the entire folder OR connect to GitHub
3. Build settings:
   - Build command: (leave empty)
   - Publish directory: `.`
4. Deploy!

**Features:**
- Automatic HTTPS
- Custom domains
- Instant cache invalidation
- Preview deployments
- Form handling

**Pros:** Fast CDN, great features, free tier generous
**Cons:** Build minutes limited on free tier

**CLI Deployment:**
```bash
npm install -g netlify-cli
netlify login
netlify deploy --prod
```

---

### ⚡ Option 3: Vercel (FREE, Lightning Fast)

**Best for:** Next-gen hosting, serverless functions

**Steps:**
1. Sign up at https://vercel.com
2. Install Vercel CLI:
   ```bash
   npm i -g vercel
   ```
3. Deploy:
   ```bash
   vercel
   ```
4. Follow prompts

**Or use the web UI:**
1. Go to https://vercel.com/new
2. Import your GitHub repo
3. Deploy!

**Pros:** Fastest CDN, serverless support, great DX
**Cons:** Limited to 100GB bandwidth/month on free tier

---

### 🪣 Option 4: AWS S3 + CloudFront (Production Grade)

**Best for:** Enterprise, custom infrastructure

**Steps:**
1. Create S3 bucket
2. Enable static website hosting
3. Upload all files
4. Set bucket policy for public read:
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Sid": "PublicReadGetObject",
       "Effect": "Allow",
       "Principal": "*",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
     }]
   }
   ```
5. (Optional) Add CloudFront CDN for HTTPS and speed

**Pros:** Scalable, full control, enterprise-grade
**Cons:** Costs money (but very cheap ~$0.50/month), more complex

---

### 🔷 Option 5: Cloudflare Pages (FREE, Fast CDN)

**Best for:** Global edge network, DDoS protection

**Steps:**
1. Sign up at https://pages.cloudflare.com
2. Connect GitHub repo
3. Build settings:
   - Build command: (leave empty)
   - Build output: `/`
4. Deploy!

**Pros:** Cloudflare's global CDN, unlimited bandwidth, free
**Cons:** Build time limits

---

### 🐳 Option 6: Docker + Any Host

**Best for:** Custom servers, Docker deployment

**Create Dockerfile:**
```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

**Build and run:**
```bash
docker build -t situation-room .
docker run -p 8080:80 situation-room
```

**Deploy to:**
- DigitalOcean App Platform
- Google Cloud Run
- AWS ECS/Fargate
- Azure Container Instances

---

## Custom Domain Setup

### For GitHub Pages:
1. Add `CNAME` file with your domain:
   ```
   situation-room.yourdomain.com
   ```
2. Add DNS records at your domain provider:
   ```
   Type: CNAME
   Name: situation-room
   Value: YOUR_USERNAME.github.io
   ```

### For Netlify/Vercel/Cloudflare:
1. Go to domain settings in dashboard
2. Add your domain
3. Update DNS records as instructed

---

## Environment Considerations

### CORS (Cross-Origin Resource Sharing)
All external APIs used (NASA GIBS, Celestrak) allow cross-origin requests, so no CORS proxy needed!

### HTTPS Required
Most browsers require HTTPS for:
- Geolocation API
- Some sensor APIs
- Service Workers

**All deployment options above provide free HTTPS automatically!**

### API Limits
- **NASA GIBS:** No authentication, no limits
- **Celestrak TLE data:** Free, no API key needed
- **Leaflet maps:** Free
- **Three.js:** Local, no API

**Result: No backend or API keys needed!**

---

## Optimization Tips

### 1. Enable Gzip Compression
Most hosts do this automatically. For custom servers:
```nginx
# nginx.conf
gzip on;
gzip_types text/html text/css application/javascript;
```

### 2. Add Cache Headers
```nginx
location ~* \.(js|css|html)$ {
    expires 1h;
    add_header Cache-Control "public, must-revalidate";
}
```

### 3. Preload Critical Resources
Add to `<head>` in index.html:
```html
<link rel="preload" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" as="style">
<link rel="preload" href="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js" as="script">
```

### 4. Add Service Worker (PWA)
Make it installable as a Progressive Web App - see PWA.md (if you want this, let me know!)

---

## Troubleshooting

### Issue: Blank white screen
**Solution:** Check browser console (F12) for errors. Usually a missing file.

### Issue: Satellite data not loading
**Solution:** Check network tab - Celestrak might be rate-limiting. Wait a few minutes.

### Issue: NASA GIBS imagery not showing
**Solution:** Check date - GIBS has data from ~2012 onwards. Select a recent date.

### Issue: 404 errors on GitHub Pages
**Solution:** Ensure all filenames are correct (case-sensitive on Linux servers).

### Issue: Localhost CORS errors
**Solution:** Must use a proper web server (http-server, Python, etc.), not `file://` protocol.

---

## Performance Metrics

**Typical Performance:**
- Initial load: ~500KB (with CDN resources)
- TLE data: ~2-3MB (14,000+ satellites)
- NASA imagery tiles: ~50KB per tile
- FPS: 50-60 (with 14,000 satellites)

**Best Practices:**
- Use a CDN for static assets
- Enable HTTP/2
- Compress satellite data
- Lazy load imagery tiles

---

## Security Notes

### No Backend = No Attack Surface
Static sites have minimal security concerns:
- ✅ No SQL injection
- ✅ No server exploits
- ✅ No authentication vulnerabilities

### Client-Side Only Risks:
- XSS (mitigated by CSP headers)
- Dependency vulnerabilities (keep CDN versions updated)

### Recommended CSP Header:
```
Content-Security-Policy: default-src 'self'; 
  script-src 'self' 'unsafe-inline' https://unpkg.com https://cdnjs.cloudflare.com https://cdn.jsdelivr.net; 
  style-src 'self' 'unsafe-inline' https://unpkg.com; 
  img-src 'self' data: https:; 
  connect-src 'self' https://gibs.earthdata.nasa.gov https://celestrak.org https://*.basemaps.cartocdn.com;
```

---

## Monitoring

### Simple Analytics (Privacy-Friendly):
- **Plausible.io** - Privacy-focused, GDPR compliant
- **Umami** - Self-hosted alternative
- **GoatCounter** - Open source, simple

### Add to `<head>`:
```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

---

## Next Steps

1. ✅ Choose a deployment platform
2. ✅ Deploy the site
3. ✅ Test all features
4. ✅ (Optional) Add custom domain
5. ✅ (Optional) Set up analytics
6. ✅ Share with the world!

---

## Support

If you run into issues:
1. Check browser console (F12)
2. Verify all files are uploaded
3. Test locally first
4. Check deployment platform documentation

**Common URLs to test:**
- `/` - Main dashboard
- `/orbital-viz-all-sats.html` - Orbital view
- `/global-guard.html` - Global Guard
- `/osint-observer.html` - OSINT

All should load without errors!
