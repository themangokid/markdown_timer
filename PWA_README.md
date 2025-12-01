# MD-Timer PWA Setup Guide

## What's Been Added

MD-Timer is now a fully functional Progressive Web App (PWA) with the following features:

### ✅ Implemented Features

1. **Installable App**
   - Add to home screen on mobile
   - Install as desktop app on Chrome/Edge
   - Runs in standalone mode (no browser UI)

2. **Offline Support**
   - Works completely offline after first visit
   - Service worker caches all assets
   - Automatic updates when online

3. **Wake Lock**
   - Keeps screen awake during active timers
   - Prevents device from sleeping
   - Auto-releases when timer stops

4. **Sound Notifications**
   - Audio beep when tasks complete
   - Generated using Web Audio API
   - No external sound files needed

5. **Push Notifications**
   - Browser notifications when tasks finish
   - Works even when app is in background
   - Shows remaining task count

6. **Vibration**
   - Haptic feedback on task completion
   - Mobile devices only
   - Gentle double-pulse pattern

7. **Badge API**
   - Shows remaining task count on app icon
   - Updates in real-time
   - Clears when all tasks complete

8. **Media Session**
   - Control timer from lock screen
   - Shows current task in media controls
   - Play/pause/skip functionality

9. **App Shortcuts**
   - Right-click app icon for quick actions
   - "Start Timer" shortcut
   - "View Routines" shortcut

10. **Install Prompt**
    - Friendly prompt to install app
    - Can be dismissed
    - Remembers user preference

## Setup Instructions

### 1. Generate Icons

Icons are required for the PWA to work properly. You have several options:

#### Option A: Using generate-icons.html
```bash
# Open in browser
open generate-icons.html

# Download each generated icon
# Move downloaded files to icons/ folder
```

#### Option B: Using ImageMagick
```bash
cd icons
for size in 72 96 128 144 152 192 384 512; do
  convert icon.svg -resize ${size}x${size} icon-${size}.png
done
```

#### Option C: Online Tool
1. Visit https://www.pwabuilder.com/imageGenerator
2. Upload `icons/icon.svg`
3. Download generated icon pack
4. Extract to `icons/` folder

### 2. Serve with HTTPS

PWA features require HTTPS (except on localhost):

#### For Development (localhost):
```bash
# Using Python
python3 -m http.server 8000

# Using Node.js http-server
npx http-server -p 8000

# Using PHP
php -S localhost:8000
```

Then visit: http://localhost:8000

#### For Production:
- Deploy to any HTTPS-enabled host
- GitHub Pages (free, automatic HTTPS)
- Netlify (free, automatic HTTPS)
- Vercel (free, automatic HTTPS)

### 3. Test the PWA

1. **Open in Chrome/Edge:**
   - Navigate to your app URL
   - Look for install icon in address bar
   - Or use menu: "Install MD-Timer"

2. **Test Features:**
   - ✅ Create some timers
   - ✅ Start a timer
   - ✅ Verify screen stays awake
   - ✅ Wait for task to complete
   - ✅ Check for notification and sound
   - ✅ Look for badge on app icon
   - ✅ Lock device and check media controls

3. **Test Offline:**
   - Open the app
   - Turn off wifi/data
   - Reload the page - should still work!
   - Create timers - should work offline
   - Turn on wifi - app updates automatically

## Browser Support

| Feature | Chrome | Edge | Safari | Firefox |
|---------|--------|------|--------|---------|
| Install | ✅ | ✅ | ✅ (iOS 16.4+) | ⚠️ Android only |
| Offline | ✅ | ✅ | ✅ | ✅ |
| Wake Lock | ✅ | ✅ | ✅ (iOS 16.4+) | ❌ |
| Notifications | ✅ | ✅ | ✅ | ✅ |
| Sound | ✅ | ✅ | ✅ | ✅ |
| Vibration | ✅ | ✅ | ✅ | ⚠️ Android only |
| Badge | ✅ | ✅ | ❌ | ❌ |
| Media Session | ✅ | ✅ | ⚠️ Partial | ✅ |

## File Structure

```
markdown_timer/
├── index.html              # Main app (PWA-enabled)
├── manifest.json           # PWA configuration
├── sw.js                   # Service worker (offline support)
├── generate-icons.html     # Icon generator utility
├── notification.mp3        # Placeholder (Web Audio used instead)
├── icons/
│   ├── icon.svg           # Source SVG icon
│   ├── icon-72.png        # Generated (72x72)
│   ├── icon-96.png        # Generated (96x96)
│   ├── icon-128.png       # Generated (128x128)
│   ├── icon-144.png       # Generated (144x144)
│   ├── icon-152.png       # Generated (152x152)
│   ├── icon-192.png       # Generated (192x192)
│   ├── icon-384.png       # Generated (384x384)
│   ├── icon-512.png       # Generated (512x512)
│   └── README.md          # Icon generation guide
├── PWA_README.md          # This file
└── version_from_PWA.md    # Restoration guide
```

## How It Works

### Service Worker
- Caches HTML, CSS, JS, and CDN assets
- Serves cached content when offline
- Updates cache when new version available
- Cache-first strategy for performance

### Wake Lock
- Requested when timer starts
- Keeps screen on during active countdown
- Released when timer stops or pauses
- Handles visibility changes automatically

### Notifications
- Requests permission on first timer start
- Shows notification when task completes
- Includes remaining task count
- Clickable to focus app window

### Media Session
- Updates metadata for each task
- Shows task name and routine
- Provides playback controls
- Works on lock screen

### Badge
- Updates on task start
- Shows remaining task count
- Updates as tasks complete
- Clears when all done

## Customization

### Change App Colors
Edit `manifest.json`:
```json
{
  "background_color": "#111827",  // Dark gray
  "theme_color": "#10b981"        // Green
}
```

### Change App Name
Edit `manifest.json`:
```json
{
  "name": "Your Timer Name",
  "short_name": "Timer"
}
```

### Add More Shortcuts
Edit `manifest.json` shortcuts array:
```json
{
  "shortcuts": [
    {
      "name": "Quick 5min",
      "url": "/index.html?quick=5"
    }
  ]
}
```

### Customize Notification Sound
Replace the Web Audio beep in `index.html`:
```javascript
// Current: Simple sine wave beep
// Change frequency, duration, or use audio file
oscillator.frequency.value = 800; // Change pitch
```

## Troubleshooting

### Install Prompt Not Showing
- Clear browser cache
- Ensure all icons exist
- Check manifest.json is valid
- Must use HTTPS (or localhost)
- Some browsers suppress repeat prompts

### Wake Lock Not Working
- Requires HTTPS in production
- Must be in active tab
- Doesn't work in background
- Check browser support

### Notifications Not Showing
- Check browser permissions (Settings > Notifications)
- Must explicitly grant permission
- May be blocked by OS settings
- Check "Do Not Disturb" mode

### Sound Not Playing
- Requires user interaction first
- Check device volume
- May be muted by browser policy
- Check console for errors

### Badge Not Updating
- Only works on Chrome/Edge desktop
- Requires app to be installed
- May not work on all OS versions

### Offline Not Working
- Service worker may not be registered
- Check browser console for errors
- Try hard refresh (Cmd/Ctrl + Shift + R)
- Clear cache and reload

## Testing Checklist

- [ ] App installs on Chrome desktop
- [ ] App installs on Chrome Android
- [ ] App installs on Safari iOS
- [ ] Works offline after installation
- [ ] Screen stays on during timer
- [ ] Sound plays when task completes
- [ ] Notification appears when task done
- [ ] Badge shows task count (Chrome/Edge)
- [ ] Media controls work on lock screen
- [ ] App shortcuts work (right-click icon)
- [ ] Service worker updates correctly
- [ ] Install prompt can be dismissed
- [ ] App runs in standalone mode

## Deployment

### GitHub Pages
1. Push code to GitHub
2. Enable GitHub Pages in repo settings
3. Select main branch
4. Access at: `https://username.github.io/repo-name`

### Netlify
1. Connect GitHub repo
2. Set build command: (none)
3. Set publish directory: `/`
4. Deploy!

### Vercel
```bash
npm i -g vercel
vercel
```

## Resources

- [PWA Builder](https://www.pwabuilder.com/) - Test and enhance PWA
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - PWA audit tool
- [MDN PWA Guide](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [Web.dev PWA](https://web.dev/progressive-web-apps/)

## Support

If something doesn't work:
1. Check browser console for errors
2. Verify all icons are generated
3. Ensure serving over HTTPS
4. Check browser compatibility table
5. Review troubleshooting section above

The app gracefully degrades - if a feature isn't supported, the app still works without it!
