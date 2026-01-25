# 🌟 Star Sentinel Features Guide

**Complete guide to satellite tracking features**

---

## 🎯 Core Features

### 1. Real-Time Satellite Tracking

**What it does:**
Tracks 14,000+ active satellites in real-time using official TLE (Two-Line Element) data from CelesTrak.

**How to use:**
- Satellites appear as colored dots on 3D globe
- **Blue** = LEO (Low Earth Orbit) < 2,000 km
- **Pink** = MEO (Medium Earth Orbit) 2,000-35,000 km
- **Yellow** = GEO/HEO (Geostationary/High) > 35,000 km

**Controls:**
- **Rotate:** Click and drag
- **Zoom:** Mouse wheel or pinch gesture
- **Select:** Click any satellite point

---

### 2. Time Travel (7-Day History)

**What it does:**
Rewind time to see where satellites were up to 7 days ago.

**How to use:**
1. Look at bottom of screen - time slider with day markers
2. Drag slider left to go back in time
3. Drag right to return to present
4. Watch satellites move to historical positions
5. Earth rotation matches selected time

**Use cases:**
- Verify satellite pass timing
- Analyze orbital maneuvers
- Study constellation deployment
- Educational demonstrations

**Technical details:**
- Uses TLE propagation (SGP4/SDP4)
- Accurate within ±2 weeks of TLE epoch
- Updates satellite AND Earth rotation

---

### 3. Satellite Information Panel

**What it does:**
Shows detailed orbital parameters for any satellite.

**How to use:**
1. Click any satellite
2. Panel appears (bottom left)
3. Scroll to see all data

**Data shown:**

#### Basic Info
- Satellite name
- NORAD catalog ID
- Maneuver status (if detected)

#### Current Position
- Latitude / Longitude
- Altitude (instantaneous)

#### Orbital Elements
- Semi-Major Axis
- Eccentricity
- Inclination
- RAAN (Right Ascension of Ascending Node)
- Argument of Perigee
- Mean Anomaly

#### Derived Parameters
- Perigee altitude
- Apogee altitude
- Mean altitude
- Orbital period
- Mean motion

---

### 4. Maneuver Detection

**What it does:**
Identifies satellites that changed their orbit between TLE updates.

**How it works:**
- Compares current TLE with previous TLE
- Detects significant orbital parameter changes
- Flags maneuvered satellites

**Indicators:**
- Maneuver count in stats panel
- "⚠️ MANEUVER DETECTED" in satellite info
- Red text in info panel

**Use cases:**
- Track active satellites
- Identify constellation adjustments
- Monitor satellite operations
- Study station-keeping maneuvers

---

### 5. Statistics Dashboard

**What it shows:**

#### Satellite Data Panel
- **Satellites Tracked** - Total count (~14,000)
- **Maneuvers Detected** - Since last TLE update
- **Avg. Altitude** - Mean across all satellites
- **Inclination Range** - Min to max values

#### Mission Time Panel
- **UTC Time** - Current universal time
- **Jerusalem Time** - Israel local time
- **Washington DC Time** - US Eastern time
- **Last TLE Update** - When data was refreshed

**Auto-updates:**
- Clocks update every second
- Satellite count updates on TLE refresh (30 min)
- Maneuver count updates on comparison

---

## 🗺️ Additional Modules

### OSINT Observer

**What it does:**
Monitors social media for space-related intelligence.

**Status:** Mock data mode (demo purposes)

---

### Global Guard

**What it does:**
Tracks geopolitical incidents globally.

**Status:** Mock data mode (demo purposes)

---

## 🎮 Controls & Navigation

### Mouse Controls
- **Left Click + Drag** - Rotate globe
- **Mouse Wheel** - Zoom in/out
- **Click Satellite** - Show info panel
- **Click Panel X** - Close panel

### Keyboard Shortcuts
- **Escape** - Close modals/panels
- **F12** - Open developer console (for debugging)

### Touch Controls (Mobile)
- **One Finger Drag** - Rotate globe
- **Pinch** - Zoom in/out
- **Tap Satellite** - Show info
- **Tap X** - Close panels

---

## 📊 Data Sources

### CelesTrak (TLE Data)
- **Source:** Dr. T.S. Kelso / CelesTrak
- **URL:** celestrak.org
- **Update Frequency:** Every 30 minutes
- **Coverage:** All active satellites
- **Authentication:** Not required (public API)
- **Cost:** Free

### Data Accuracy
- **TLE Propagation:** ±2 weeks of epoch
- **Time Travel:** Accurate within 7-day window
- **Position:** Sub-kilometer accuracy for most satellites

---

## 🎓 Educational Use Cases

### For Students
- Learn orbital mechanics
- Understand satellite types
- Study orbital decay
- Track ISS and science satellites

### For Researchers
- Analyze constellation deployment
- Study orbital maneuvers
- Track debris populations
- Verify pass predictions

### For Amateur Astronomers
- Plan satellite observations
- Track visible satellites
- Identify unknown objects

### For Space Enthusiasts
- Follow launch deployments
- Track favorite satellites
- Monitor space stations
- Learn about space operations

---

## 🚀 Advanced Tips

### Performance Optimization
- Close unused browser tabs
- Disable other extensions
- Use hardware acceleration
- Reduce browser zoom level
- Clear browser cache periodically

### Finding Specific Satellites

**ISS (International Space Station):**
- Look for LEO (blue) satellites
- Near 51.6° inclination
- ~400 km altitude
- Moves fast across globe

**Starlink Constellations:**
- Recently launched Starlinks are close together
- Look for clusters of LEO satellites
- Same orbital plane (similar RAAN)
- ~550 km altitude
- Gradually spread out over weeks

**GPS Satellites:**
- Look for MEO (pink) satellites
- 55° inclination
- ~20,200 km altitude

**Geostationary Satellites:**
- Look for yellow satellites
- 0° inclination
- 35,786 km altitude
- Appear stationary over equator

---

## 📈 Performance Metrics

### Typical Performance
- **FPS:** 60 fps smooth animation
- **Memory:** ~150 MB RAM
- **CPU:** 5-15% single core
- **Network:** 500 KB per 30 min

### Optimizations Applied
- Efficient satellite rendering (GPU-accelerated)
- Throttled position updates
- Cached TLE data
- Minimal DOM updates
- WebGL hardware acceleration

---

## 🔮 Upcoming Features (Roadmap)

### Version 1.1 (Planned)
- ⏳ Satellite search by name/NORAD ID
- ⏳ Ground station tracking
- ⏳ Pass predictions for your location
- ⏳ Custom satellite groups/filters

### Version 1.2 (Planned)
- ⏳ Orbit path visualization
- ⏳ Conjunction warnings
- ⏳ Export satellite data (CSV/JSON)
- ⏳ Screenshot/share features

### Version 2.0 (Future)
- ⏳ Mobile apps (iOS/Android)
- ⏳ Real-time collision alerts
- ⏳ Augmented reality mode

---

## 💡 Tips & Tricks

### Best Viewing Experience
- Use fullscreen mode (F11)
- Dark room environment
- Adjust monitor brightness

### Understanding Colors
- More **blue** dots = Active LEO zone
- Cluster patterns = Satellite constellations
- Isolated **yellow** dots = High-altitude satellites

### Interesting Patterns
- **Starlink trains** - Recently launched satellites in close formation
- **Sun-synchronous orbits** - Satellites that maintain constant angle to sun
- **Geostationary belt** - Ring of satellites at 35,786 km

---

## 📞 Support & Feedback

### Getting Help
- Read this guide thoroughly
- Check DEPLOYMENT.md for setup issues
- Review browser console for errors
- Check GitHub issues

### Reporting Bugs
Include:
- Browser type and version
- Screenshot of issue
- Console error messages
- Steps to reproduce

### Feature Requests
- Describe use case
- Explain expected behavior
- Note if similar features exist elsewhere

---

**🛰️ Explore, Learn, Track! 🛰️**
