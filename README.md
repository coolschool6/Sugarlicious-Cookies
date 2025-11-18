# Sugarlicious Cookies Website

A modern, mobile-first portfolio website showcasing handcrafted sugar cookies with an interactive image lightbox.

## Image Optimization Guide

### Current Setup
- All images use `loading="lazy"` for deferred loading
- `decoding="async"` for non-blocking image decoding
- CSS optimizations for smoother rendering

### Recommended Image Optimization

To improve load times and performance, compress your images:

#### Option 1: Online Tools (Easiest)
1. Visit [TinyJPG](https://tinyjpg.com/) or [Squoosh](https://squoosh.app/)
2. Upload your JPG files from the `images/` folder
3. Download the compressed versions (typically 40-70% smaller)
4. Replace the original files

#### Option 2: PowerShell Batch Conversion
If you have ImageMagick installed:

```powershell
cd "images"
Get-ChildItem -Filter *.jpg | ForEach-Object {
    magick convert $_.Name -quality 85 -strip "optimized_$($_.Name)"
}
```

#### Option 3: Modern WebP Format
Convert to WebP for even better compression (with HTML fallback):

```powershell
# Using cwebp (from WebP tools)
Get-ChildItem -Filter *.jpg | ForEach-Object {
    cwebp -q 85 $_.Name -o "$($_.BaseName).webp"
}
```

### Target Image Sizes
- **Logo**: ~50KB (optimized at display size)
- **Product images**: 100-200KB each (currently may be larger)
- **Total page weight target**: Under 1MB for fast mobile loading

### Favicon
The logo is currently used as favicon. For best results:
1. Export logo as 512×512 PNG
2. Use [Favicon Generator](https://realfavicongenerator.net/)
3. Add generated files to root and update HTML

## File Structure
```
Sugarlicious-Cookies/
├── index.html
├── css/
│   └── styles.css
├── images/
│   ├── Logo.jpg
│   ├── Pink Christmas.jpg
│   ├── Santa's Toy shop.jpg
│   ├── Paint your Own Cookie.jpg
│   └── Personalized Gingerboy and Snowman.jpg
└── README.md
```

## Features
- Mobile-first responsive design
- Interactive image zoom lightbox
- Smooth animations and transitions
- Accessible with keyboard navigation
- Pink/white watercolor aesthetic
- Device-frame presentation

## Browser Support
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile-optimized with safe-area insets
- Accessible with ARIA labels

## Performance
- Lazy-loaded images
- Preconnected fonts
- GPU-accelerated animations
- Optimized CSS variables
