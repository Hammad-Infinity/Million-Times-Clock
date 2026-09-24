#  Artistic Clock Visualizations

A beautiful, interactive HTML-based clock display with animated hand and digit representations.

## Features

 **Real-time Display**
- Shows current time with animated transitions
- Dynamic grid-based clock display
- Smooth transitions between time and pattern states
- Optional day and date display when space allows

 **Customization**
- Dark and Light themes
- Adjustable transition speed (1–20 seconds)
- Adjustable clock grid size (columns and rows)
- 24-hour and 12-hour format toggle
- Pattern navigation: Previous, Next, and Show time
- Theme switcher in settings
- Mouse follow mode
- Fullscreen toggle

 **Interactive Controls**
- Settings button in top-right corner
- Draggable settings panel
- Fullscreen button
- Mouse follow checkbox
- Theme buttons: Dark / Light
- Pattern buttons: Previous / Next / Show time
- Click the canvas to add a ripple effect

 **Visual Effects**
- Animated hand movements with smooth interpolation
- Multiple abstract pattern animations before showing time
- Scrolling letters pattern
- Ripple effects on click
- Shadow effects for depth
- Responsive design

##  Usage
1. Open `Million Times Clock.html` in a web browser
2. Clock displays in the center of the screen with the default dark theme
3. Click the settings icon to customize
4. Click the canvas to create a ripple effect

## Settings

**Theme Colors**
- Dark and Light themes are available
- Theme preference is remembered
- Use the theme buttons in Settings to switch

**Transition Speed**
- Range: 1 - 20 seconds
- Step: 0.2 seconds
- Controls animation smoothness between time and pattern states

**Clock Grid**
- Columns: 8 - 24
- Rows: 3 - 14
- Adjust the grid to change the level of detail
- Grid preference is remembered

**Hour Format**
- Toggle between 24-hour and 12-hour display

**Mouse Follow**
- When enabled, the clock hands follow the cursor

**Fullscreen**
- Toggle fullscreen from the settings panel

**Patterns**
- Use Previous and Next to browse patterns
- Use Show time to jump to the current time display

### Modify Colors
- Use the theme switcher in Settings for Dark or Light mode
- Additional color customization can be done by editing the theme definitions in the file

##  Browser Compatibility

- Chrome/Chromium
- Firefox
- Safari
- Edge
- Any modern browser with Canvas support

##  How It Works

The clock uses a grid of miniature clocks:
- Each grid cell contains animated clock hands
- Hand positions are determined by patterns or by the current time
- The display cycles through multiple abstract patterns and time displays
- When the time is shown, digits and optional day/date information are formed by the grid
- The time display updates continuously while active
- The scrolling-letter pattern moves across the grid
- Clicking the canvas creates a ripple effect across the grid
- Rendering is handled with HTML Canvas for smooth performance

##  Keyboard Shortcuts

The current version uses on-screen controls. The following shortcuts are not active in this build.

| Key | Action |
|-----|--------|
| `F` | Toggle fullscreen / show/hide menu |
| `M` | Follow Cursor / Resume Animation |
| `R` | Randomize Theme |
| `Space` | Show Current Time |

## Tips

- Use full screen for best experience (F11 or the Fullscreen button)
- Adjust transition speed based on preference
- Works great as desktop background preview or as wallpaper
- Increase grid size for more detail; decrease it for simpler visuals
- Click the canvas to trigger a ripple effect

## License 
- The GNU Affero General Public License (AGPL).
