# Changelog - Recent Updates

## Version 2.1 - GDELT Integration - January 2026

### ✅ Real-Time News Integration

**Global Guard now uses GDELT (Global Database of Events, Language, and Tone)**

#### What is GDELT?
- World's largest open database of human society
- Monitors news from every country in 100+ languages
- Updates every 15 minutes
- Completely free, no API key needed
- Used by researchers, governments, and media worldwide

#### How It Works:
1. **User clicks anywhere on map**
2. **Location detected** via reverse geocoding (country + region)
3. **GDELT API queried** for recent articles about that location
4. **Real news articles displayed** with:
   - Source (extracted from URL)
   - Timestamp (relative: "2h ago", "3d ago")
   - Title
   - Tags (auto-generated: economy, security, politics, etc.)
   - Clickable to open full article

#### Features:
- ✅ **100% Real News** - No more mock data
- ✅ **Global Coverage** - Every country, every region
- ✅ **Real-Time** - GDELT updates every 15 minutes
- ✅ **Free Forever** - No API key, no rate limits
- ✅ **No Backend** - Direct browser API calls
- ✅ **Clickable Articles** - Opens full article in new tab

#### Technical Details:
- **API**: GDELT Doc API v2
- **Endpoint**: `https://api.gdeltproject.org/api/v2/doc/doc`
- **Format**: JSON
- **Rate Limit**: None
- **Authentication**: Not required

---

## Version 2.0 - January 2026

### Name Change
- ✅ **"Orbital Sentinel"** → **"Star Sentinel"**

### Global Guard - Complete Redesign
- ❌ **Removed:** NASA GIBS controls, incident markers, news feed
- ✅ **Added:** Full-screen satellite map with click-for-news

---

## Summary

| Feature | Before (v1.0) | v2.0 | v2.1 (Current) |
|---------|---------------|------|----------------|
| **Name** | Orbital Sentinel | Star Sentinel | Star Sentinel |
| **News Source** | N/A | Mock data | GDELT (Real) |
| **Update Frequency** | N/A | Static | Every 15min |
| **Coverage** | N/A | 50 countries | Global |
| **API Key** | N/A | Not needed | Not needed |
| **Articles Clickable** | N/A | No | Yes |
