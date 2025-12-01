# Quick Start Guide

## Test the PWA Right Now (3 steps)

### 1. Generate Icons
Open `generate-icons.html` in your browser and download all icons to the `icons/` folder.

Or use this quick command if you have ImageMagick:
```bash
cd icons && for size in 72 96 128 144 152 192 384 512; do convert icon.svg -resize ${size}x${size} icon-${size}.png; done && cd ..
```

### 2. Start Local Server
```bash
# Python 3
python3 -m http.server 8000

# Or Python 2
python -m SimpleHTTPServer 8000

# Or Node.js
npx http-server -p 8000

# Or PHP
php -S localhost:8000
```

### 3. Open in Browser
Navigate to: **http://localhost:8000**

You should see an install prompt in the bottom right!

## What to Test

1. **Click "Install Now"** - App installs to your device
2. **Create timers** with the # syntax:
   ```
   # Morning Routine
   5 min: Meditation
   10 min: Breakfast
   2 min: Stretch
   ```
3. **Start the timer** - Notice your screen stays awake
4. **Wait for completion** - You'll hear a beep, get a notification, and feel vibration (on mobile)
5. **Check app icon** - Should show a badge with remaining task count

## Features You Can Use

- 📱 **Install to home screen** (mobile/desktop)
- 🔒 **Screen stays awake** during timers
- 🔔 **Notifications** when tasks complete
- 📳 **Vibration** feedback (mobile)
- 🔢 **Badge count** on app icon
- 🎵 **Sound alerts** for completion
- 📴 **Works offline** after first visit
- 🎮 **Media controls** from lock screen
- ⚡ **Quick shortcuts** from app icon

## Backup Information

**Original version saved at:**
- Git commit: `8bb60dfbf6d7ea115a37b9dcc5f2a1f593b7d943`
- See `version_from_PWA.md` for restoration instructions

## Need Help?

- Full documentation: `PWA_README.md`
- Icon generation: `icons/README.md`
- Troubleshooting: Check browser console (F12)

## Deploy

Once tested locally, deploy to any of these for free:
- **GitHub Pages** (automatic HTTPS)
- **Netlify** (drag & drop)
- **Vercel** (one command: `vercel`)

Enjoy your PWA! 🚀
