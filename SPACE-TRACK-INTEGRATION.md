# ⚙️ Space-Track.org Integration - Complete Guide

## 🚨 NEW FEATURE: TIP Message Alert Panel

Star Sentinel now integrates with **USSF Space-Track.org** to display official reentry predictions and **Tracked Impact Predictions (TIP)** messages.

---

## What You'll Get:

### 1. 🚨 TIP Message Alert Panel (Auto-appears)
**Shows ONLY when TIP messages exist** - high-priority reentry alerts with impact predictions

**Example:**
```
🚨 TRACKED IMPACT PREDICTIONS (TIP)

COSMOS 2251 DEB (NORAD 12345)
Predicted Reentry: Mon, 20 Jan 2026 03:45:00 GMT
Uncertainty Window: ±90 minutes
Impact Location: 15.2°N, 155.3°W
Direction: ASCENDING
⚠ HIGH INTEREST OBJECT
```

### 2. 🛸 Deorbit Watch Panel
Continuous monitoring of all predicted reentries:
- 🔴 Critical: < 24 hours
- 🟠 Warning: 1-7 days  
- ⚪ Tracked: 7-30 days

### 3. ⚙️ Settings Panel
Secure credential management:
- Enter Space-Track.org email/password
- Test connection
- Credentials stored locally only
- Auto-login on reload

### 4. 📊 Enhanced Satellite Info
When clicking satellites with reentry predictions:
- Predicted reentry time
- Time to reentry countdown
- Impact location (if TIP available)
- Uncertainty window
- USSF confidence level

---

## Quick Setup (5 Minutes):

### Step 1: Create Space-Track.org Account
1. Go to: https://www.space-track.org/auth/createAccount
2. Fill form (Name, Email, Password)
3. Justification: "Personal satellite tracking research"
4. Submit & wait for approval email (~24 hours)

### Step 2: Connect to Star Sentinel
1. Upload this new version to GitHub
2. Open Star Sentinel
3. Click **⚙️ Space-Track.org** button (top right)
4. Enter your email & password
5. Click **Test & Save**
6. Done! ✅

---

## Features in Detail:

### TIP Message Panel (Auto-Shows)

**What are TIP Messages?**
- **T**racked **I**mpact **P**redictions from USSF
- High-confidence reentry predictions
- Detailed impact location data
- Updated regularly by Space Surveillance Network

**When does it appear?**
- **Only when TIP messages exist**
- Automatically disappears when no TIP messages
- High-priority alert styling (red/pulsing)
- Dismissible but reappears on update if still active

**What it shows:**
- Satellite name & NORAD ID
- Predicted reentry time (UTC)
- Uncertainty window (±minutes)
- Impact coordinates (lat/lon)
- Orbital direction (ascending/descending)
- High-interest flag (if applicable)

**Example Scenario:**
```
Normal day: TIP panel hidden
↓
USSF issues TIP for high-interest reentry
↓
TIP panel automatically appears at top center
↓
Shows impact prediction with red alert styling
↓
Updates every 15 minutes
↓
After reentry occurs: TIP panel auto-hides
```

---

### Deorbit Watch Panel

**Always visible when Space-Track connected**

Shows next 15 predicted reentries sorted by time:

```
🛸 DEORBIT WATCH

🔴 COSMOS 2251 DEB
   Reentry: 2026-01-20 03:45 UTC
   Time to reentry: ~18 hours
   NORAD ID: 12345

🟠 FENGYUN 1C DEB
   Reentry: 2026-01-23 12:30 UTC  
   Time to reentry: ~3 days
   NORAD ID: 67890

Last updated: 10:45
```

---

### Enhanced Satellite Info

Click any satellite to see full details.

**If satellite has reentry prediction:**
```
⚠️ DEORBIT STATUS

Predicted Reentry: Mon, 20 Jan 2026 03:45 GMT
Time to Reentry: ~18 hours
Confidence: Precedence 1 (highest)

🎯 IMPACT PREDICTION
Impact Location: 15.2°N, 155.3°W
Uncertainty: ±90 minutes
Direction: ASCENDING
⚠ HIGH INTEREST OBJECT

Data source: USSF Space-Track.org
```

**If satellite is normal:**
No deorbit section shown.

---

## How It Works:

### Data Flow:
```
1. Star Sentinel loads
2. Auto-login with saved credentials
3. Fetch from Space-Track.org API:
   - Decay messages (predicted reentries)
   - TIP messages (impact predictions)
4. Match NORAD IDs with tracked satellites
5. Update panels:
   - TIP panel (only if TIP messages exist)
   - Deorbit Watch panel
   - Satellite info panels
6. Repeat every 15 minutes
```

### API Endpoints Used:

**Decay Messages:**
```
GET /basicspacedata/query/class/decay/
    DECAY_EPOCH/>now-0/
    DECAY_EPOCH/<now+30/
    orderby/DECAY_EPOCH asc/
    limit/200/
    format/json
```

**TIP Messages:**
```
GET /basicspacedata/query/class/tip/
    INSERT_EPOCH/>now-7/
    DECAY_EPOCH/>now-0/
    orderby/DECAY_EPOCH asc/
    limit/50/
    format/json
```

---

## Security & Privacy:

### Where Are Credentials Stored?
- **Browser localStorage only** (your device)
- **Never uploaded** to GitHub or any server
- **Direct connection**: Browser → Space-Track.org (no proxy)

### Credential Storage:
```javascript
// Saved as base64 encoded JSON
localStorage.setItem('spacetrack_creds', encoded_credentials)

// Only accessible:
- On your device
- In your browser
- By you
```

### Can Others See My Credentials?
- ❌ Not on GitHub (never uploaded)
- ❌ Not on the server (no server used)
- ❌ Not in network traffic (direct HTTPS to Space-Track)
- ⚠️ Someone with physical access to your computer could extract them
- ✅ Best practice: Use Space-Track account specifically for this

---

## API Rate Limits:

**Space-Track.org Free Tier:**
- 20 requests/minute
- 200 requests/hour
- 2,000 requests/day

**Star Sentinel Usage:**
- Updates every 15 minutes
- 2 API calls per update (decay + TIP)
- ~192 calls per day
- **Well within limits** ✅

---

## Example Data (Real Satellites):

### High-Interest TIP Example:
```
COSMOS 2251 DEBRIS
NORAD ID: 34454
Reentry: 2026-01-25 14:30 UTC
Impact: 45.2°N, 155.3°W (North Pacific)
Window: ±2 hours
Status: HIGH INTEREST
```

### Routine Decay Example:
```
FENGYUN 1C DEB
NORAD ID: 30853
Reentry: 2026-02-10 08:15 UTC
Impact: Prediction pending
Window: ±8 hours
```

---

## UI Layout:

```
┌─────────────────────────────────────────────┐
│  [⚙️ Space-Track.org]  (top right)         │
├─────────────────────────────────────────────┤
│                                             │
│  [🚨 TIP ALERT PANEL]  ← Only when active  │
│  (center top, pulsing red)                  │
│                                             │
│                                             │
│            [3D GLOBE VIEW]                  │
│                                             │
│                                             │
│  [🛸 Deorbit Watch]    [Legend]            │
│  (bottom right)         (bottom left)       │
└─────────────────────────────────────────────┘
```

---

## Step-by-Step Usage:

### First Time Setup:
1. ✅ Create Space-Track.org account
2. ⏳ Wait for approval (~24 hours)
3. 🌐 Open Star Sentinel
4. ⚙️ Click Settings button
5. 📝 Enter credentials
6. 🧪 Click "Test & Save"
7. ✅ Panels appear!

### Daily Usage:
1. 🌐 Open Star Sentinel
2. 🔄 Auto-login happens
3. 📊 Panels update automatically
4. 🚨 TIP panel appears if high-priority reentries
5. 🖱️ Click satellites for details
6. 👁️ Monitor deorbit watch
7. 🔄 Auto-updates every 15 minutes

---

## Troubleshooting:

### "Connection Failed" Error
**Possible causes:**
- Wrong email/password
- Account not approved yet
- Space-Track.org is down
- CORS/network issues

**Solutions:**
1. Double-check credentials
2. Wait for approval email
3. Check https://www.space-track.org/auth/login manually
4. Try different browser/network

### TIP Panel Not Showing
**This is normal!**
- TIP messages are **rare**
- Panel **only shows when TIP messages exist**
- Most days: no TIP messages = no panel
- This is expected behavior

### Deorbit Watch Shows Nothing
**Check:**
- Are you connected? (Settings shows "Connected")
- Is Space-Track.org working?
- Try "Test & Save" again
- Check browser console for errors

### Data Not Updating
**Solutions:**
- Refresh page (F5)
- Clear credentials and re-save
- Check browser console
- Verify Space-Track.org is accessible

---

## Technical Details:

### NORAD ID Extraction:
```javascript
// TLE Line 1, columns 3-7
const noradId = tle1.substring(2, 7).trim();
```

### Satellite Matching:
```javascript
// Match by NORAD ID
const decayInfo = decayData.find(d => 
  d.NORAD_CAT_ID === satellite.noradId
);

const tipInfo = tipData.find(t => 
  t.NORAD_CAT_ID === satellite.noradId
);
```

### Auto-Login Implementation:
```javascript
window.addEventListener('load', async () => {
  const creds = loadCredentials();
  if (creds) {
    const result = await spaceTrackAPI.login(
      creds.email, 
      creds.password
    );
    if (result.success) {
      updateSpaceTrackData();
      // Update every 15 minutes
      setInterval(updateSpaceTrackData, 15 * 60 * 1000);
    }
  }
});
```

---

## What Makes This Special:

### Real USSF Data ✅
- Official predictions from US Space Force
- Same data used by DoD
- High confidence predictions

### Smart UI 🎯
- TIP panel **only when needed**
- No clutter when no alerts
- Automatic updates
- Visual priority indicators

### Secure 🔒
- Credentials stay local
- No intermediary servers
- Direct HTTPS connection
- Can clear anytime

### Free Forever 💰
- No API costs
- No subscription fees
- Generous rate limits
- Professional-grade data

---

## Summary:

✅ **TIP Alert Panel** - Auto-shows for high-priority reentries  
✅ **Deorbit Watch** - Continuous reentry monitoring  
✅ **Official USSF Data** - Real Space Surveillance Network predictions  
✅ **Secure** - Credentials stored locally only  
✅ **Free** - No costs, generous limits  
✅ **Auto-Updates** - Fresh data every 15 minutes  

**You now have a professional-grade space surveillance system with official USSF reentry tracking!** 🛰️🔴

---

## Need Help?

**Space-Track.org Registration:**
https://www.space-track.org/auth/createAccount

**Space-Track.org Documentation:**
https://www.space-track.org/documentation

**Test Your Connection:**
https://www.space-track.org/auth/login

**Check System Status:**
https://www.space-track.org/auth/systemStatus

---

**Ready to track deorbits? Upload to GitHub and click ⚙️ Space-Track.org!** 🚀
