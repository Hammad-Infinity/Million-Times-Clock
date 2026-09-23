#  Artistic Clock Visualizations

A beautiful, interactive HTML-based clock displays with animated digit representations.


## Features

 **Real-time Display**
- Shows current time with animated transitions
- 16x8 grid-based digit representation
- Smooth 20-second transitions between time states

 **Customization**
- Multiple color themes
- Adjustable transition speed (1-20 seconds)
- Theme switcher in settings

 **Interactive Controls**
- **F Key** - fullscreen mode / show/hide menu ( If set as wallpaper )
- **Space Key** - Reveal current time
- **M Key** - follow cursor / resume animation
- **R Key** - Change Random Theme
- Settings button in top-right corner

 **Visual Effects**
- Animated hand movements with smooth interpolation
- 12 animations patterns before showing time
- Shadow effects for depth
- Canvas-based rendering at 20 FPS
- Responsive design

##  Usage
1. Open `clock.py` in a web browser
2. Clock displays in center of screen with white background
3. Click settings icon to customize

## Settings

**Theme Colors**
- 6 color theme options available
- 1 custom theme option
- random theme with R Key
- Click color swatches to switch

**Transition Speed**
- Range: 1 - 20 seconds
- Controls animation smoothness between time states

### Modify Colors
Edit these values in code:
```javascript
let backColor   = { r: 255, g: 255, b: 255, a: 1.0 };
let handColor   = { r:   0, g:   0, b:   0, a: 1.0 };
let shadowColor = { r: 200, g: 200, b: 200, a: 0.61 };
```

##  Browser Compatibility

- Chrome/Chromium
- Firefox
- Safari
- Edge
- Any modern browser with Canvas support

##  How It Works

The clock uses a 16x8 grid system to represent time digits:
- Each digit has unique pattern coordinates
- Smooth transitions between digit patterns
- Real-time calculation every 20ms
- SVG icons for control buttons

##  Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `F` | Toggle fullscreen / show/hide menu ( If set as wallpaper ) |
| `M` | Follow Cursor / Resume Animation |
| `R` | Randomize Theme |
| `Space` | Show Current Time |

## Tips

- Use full screen for best experience (F11)
- Adjust transition speed based on preference
- Works great as desktop background preview or as wallpaper

## License 
- The gem GNU Affero General Public License (AGPL).
