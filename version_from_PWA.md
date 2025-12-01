# PWA Conversion Backup Reference

## Git Commit Before PWA Implementation

**Commit Hash:** `8bb60dfbf6d7ea115a37b9dcc5f2a1f593b7d943`
**Commit Message:** Added info to the task card
**Date:** 2025-12-01

## How to Restore if Something Goes Wrong

```bash
# To see what changed
git diff 8bb60dfbf6d7ea115a37b9dcc5f2a1f593b7d943

# To restore the index.html file to this version
git checkout 8bb60dfbf6d7ea115a37b9dcc5f2a1f593b7d943 -- index.html

# To restore everything to this commit (WARNING: loses all changes)
git reset --hard 8bb60dfbf6d7ea115a37b9dcc5f2a1f593b7d943
```

## Features Being Added in PWA Conversion

### Essential Features:
1. ✅ Web App Manifest (manifest.json) - Makes app installable
2. ✅ Service Worker (sw.js) - Enables offline functionality
3. ✅ Wake Lock API - Keeps device awake during timers
4. ✅ Sound Notifications - Audio alerts on task completion
5. ✅ Vibration API - Haptic feedback on mobile

### Additional Features:
6. ✅ Background Notifications - Alerts even when app is in background
7. ✅ Badge API - Show remaining tasks on app icon
8. ✅ Media Session API - Control from lock screen
9. ✅ App Shortcuts - Quick access to saved routines
10. ✅ Dynamic Theme Colors - Visual feedback based on timer state

### Files Being Created/Modified:
- `index.html` - Modified with PWA features and APIs
- `manifest.json` - NEW - PWA configuration
- `sw.js` - NEW - Service worker for offline support
- `notification.mp3` - NEW - Sound file for alerts
- `icons/` - NEW - App icons (multiple sizes)

## What Each Feature Does:

### Wake Lock
- Prevents screen from sleeping while timer is running
- Automatically releases when timer stops or app closes
- Works on Chrome, Edge, Safari (iOS 16.4+)

### Service Worker
- Caches all app files for offline use
- App works without internet connection
- Updates automatically when new version available

### Notifications
- Browser notifications when tasks complete
- Works even when app is in background/minimized
- Requires user permission (prompted on first use)

### Badge API
- Shows remaining task count on app icon
- Updates in real-time as tasks complete
- Clears when all tasks done

### Media Session
- Control timer from lock screen
- Shows current task in media controls
- Play/pause from notification panel

### Vibration
- Gentle vibration when task completes
- Mobile devices only
- Can be disabled in settings

## Testing After Installation:

1. Open Chrome/Edge and navigate to the app
2. Look for install prompt or use browser menu "Install app"
3. Test offline: Turn off wifi, app should still work
4. Start a timer and lock your phone - screen should stay on
5. Complete a task - should get notification and sound
6. Check app icon for task count badge

## Browser Support:

- **Chrome/Edge (Desktop & Android):** Full support all features
- **Safari (iOS 16.4+):** Wake Lock, notifications, install
- **Firefox (Android):** Partial support, can install
- **Opera:** Full support

## Troubleshooting:

- **No install prompt?** Check if already installed or use browser menu
- **Wake lock not working?** Requires HTTPS (or localhost for testing)
- **No notifications?** Check browser permission settings
- **Sound not playing?** User interaction required first (browser policy)
- **Badge not showing?** Currently Chrome/Edge only

## Notes:

- Wake Lock requires HTTPS in production (works on localhost for development)
- Notifications require user permission
- Some features may not work on all browsers
- The app will gracefully degrade on unsupported browsers
