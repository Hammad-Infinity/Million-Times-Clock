# ⏰ Artistic Clock Visualizations

Two beautiful, interactive HTML-based clock displays with animated digit representations.

## 📁 Files

| File | Theme | Description |
|------|-------|-------------|
| **clock.py** | Light | Clean white background with modern styling |
| **wallpaper.py** | Dark | Dark theme with custom wallpaper support |

## ✨ Features

✅ **Real-time Display**
- Shows current time with animated transitions
- 16x8 grid-based digit representation
- Smooth 20-second transitions between time states

✅ **Customization**
- Multiple color themes
- Adjustable transition speed (1-20 seconds)
- Theme switcher in settings

✅ **Interactive Controls**
- **F Key** - Show/Hide Settings panel
- **Space Key** - Reveal current time
- Settings button in top-right corner

✅ **Visual Effects**
- Animated hand movements with smooth interpolation
- Shadow effects for depth
- Canvas-based rendering at 20 FPS
- Responsive design

## 🚀 Usage

### For `clock.py` (Light Theme)
1. Open `clock.py` in a web browser
2. Clock displays in center of screen with white background
3. Click settings icon or press `F` to customize

### For `wallpaper.py` (Dark Theme)
1. Open `wallpaper.py` in a web browser
2. Place your wallpaper image as `wallpaper.jpg` in same directory
3. Dark theme clock displays over wallpaper
4. Press `F` for settings

## ⚙️ Settings

**Theme Colors**
- 9 color theme options available
- Click color swatches to switch

**Transition Speed**
- Range: 1 - 20 seconds
- Controls animation smoothness between time states

## 🎨 Customization

### Change Wallpaper (wallpaper.py)
```css
background-image: url('your-image.jpg');
```

### Modify Colors
Edit these values in code:
```javascript
let backColor   = { r: 255, g: 255, b: 255, a: 1.0 };
let handColor   = { r:   0, g:   0, b:   0, a: 1.0 };
let shadowColor = { r: 200, g: 200, b: 200, a: 0.61 };
```

## 📋 Browser Compatibility

- Chrome/Chromium ✅
- Firefox ✅
- Safari ✅
- Edge ✅
- Any modern browser with Canvas support

## 🎯 How It Works

The clock uses a 16x8 grid system to represent time digits:
- Each digit has unique pattern coordinates
- Smooth transitions between digit patterns
- Real-time calculation every 20ms
- SVG icons for control buttons

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `F` | Toggle Settings |
| `Space` | Show Current Time |

## 💡 Tips

- Use full screen for best experience (F11)
- Choose colors that contrast with your wallpaper
- Adjust transition speed based on preference
- Works great as desktop background preview

---

**Built with Canvas API & Vanilla JavaScript**
