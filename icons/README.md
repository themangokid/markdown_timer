# Icon Generation Instructions

## Quick Method: Using Online Converter

1. Go to https://www.simpleimageresizer.com/ or https://www.iloveimg.com/resize-image
2. Upload `icon.svg`
3. Generate the following sizes:
   - icon-72.png (72x72)
   - icon-96.png (96x96)
   - icon-128.png (128x128)
   - icon-144.png (144x144)
   - icon-152.png (152x152)
   - icon-192.png (192x192)
   - icon-384.png (384x384)
   - icon-512.png (512x512)

## Using ImageMagick (Command Line)

If you have ImageMagick installed:

```bash
cd icons
for size in 72 96 128 144 152 192 384 512; do
  convert icon.svg -resize ${size}x${size} icon-${size}.png
done
```

## Using generate-icons.html

1. Open `generate-icons.html` in your browser
2. Icons will be displayed with download links
3. Click each "Download" link to save the PNG files
4. Move the downloaded files to the `icons/` directory

## Using Online PWA Icon Generator

Alternative: https://www.pwabuilder.com/imageGenerator
- Upload your icon.svg
- Download the generated icon pack
- Extract to this folder

## Temporary Placeholder

Until you generate proper icons, the app will try to load from `/icons/icon-{size}.png`.
Browsers will show a default icon if files are missing.
