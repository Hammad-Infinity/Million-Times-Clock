# A Million Times Clock Art 🕐

An interactive animated clock visualization featuring a 16×8 grid of animated clocks with mesmerizing patterns, themes, and real-time updates.

## 🌟 Features

- **Dynamic Clock Grid**: 128 individual animated clocks displaying current time
- **Multiple Animated Patterns**: 8 unique pattern modes
  - Vector field patterns
  - Circular open patterns
  - Vortex field simulations
  - Real-time digital time display (HH:MM)
  - Custom gradient patterns
- **Theme Support**: 6 beautiful color themes
  - Black on White
  - White on Black
  - Navy
  - Forest (default)
  - Navy on White
  - Gold
- **Responsive Design**: Adapts to different screen sizes and resolutions
- **Smooth Animations**: Hardware-accelerated transitions with configurable speed (1-20 seconds)
- **Low CPU Usage**: FPS capped at 20 for optimal performance
- **Fullscreen Mode**: Immersive viewing experience
- **Accessibility**: ARIA labels and semantic HTML

## 🎮 How to Use

### Opening the Application
1. Simply open the `index.html` file in any modern web browser
2. The application will start automatically with the default Forest theme

### Controls

| Key | Action |
|-----|--------|
| **Settings Button (⚙️)** | Open/close settings panel |
| **Space** | Display current time in digital format (HH:MM) |
| **F** | Toggle fullscreen mode |

### Settings Panel

Once you click the Settings button, you can:

1. **Change Theme**: Click on any color swatch to switch themes
   - Each theme has a unique hand and background color combination
   
2. **Adjust Transition Speed**: Use the slider to control animation duration
   - Range: 1.0s - 20.0s
   - Default: 20.0s

## 🎨 Pattern Modes

The application cycles through 8 different pattern modes automatically:

0. **Vector Field Pattern**: Lines radiating from center to edges
1. **Circle Open (No Spread)**: Open circular pattern with minimal spread
2. **Circle Open (Standard)**: Classic circular pattern with spreading animation
3. **Circle Open (Wide)**: Wide circular spread creating ripple effect
4. **Digital Time Display**: Shows current time in 7-segment style clocks
5. **Vortex Field 1**: Two counter-rotating vortex patterns
6. **Vortex Field 2**: Alternative vortex configuration with different positions
7. **Grid Pattern**: Linear vertical column pattern

Each pattern includes smooth transitions and persists based on the configured transition speed.

## 🔧 Technical Details

### Architecture
- **Pure Vanilla JavaScript**: No external dependencies
- **Canvas-based Rendering**: HTML5 Canvas API for high-performance graphics
- **Requestanimationframe**: Smooth 60fps rendering with 20fps capped display
- **RK4 Numerical Integration**: For vortex field calculations
- **Responsive Grid System**: Dynamically sized cells based on viewport

### Clock Components
- **Hand Animation**: Two hands per clock with interpolated rotation
- **Hand Shadows**: Blur effect with customizable offset
- **Hub**: Central pivot point for both hands
- **Prerendered Face**: Cached clock face for performance

### Performance Optimizations
- **FPS Capping**: Limited to 20 FPS for reduced power consumption
- **Prerendered Clock Faces**: Reduce per-frame draw calls
- **Cached Layout**: Minimal recalculation on static viewport
- **Device Pixel Ratio Support**: Crisp rendering on high-DPI displays

## 📱 Browser Compatibility

- Chrome/Chromium (version 60+)
- Firefox (version 55+)
- Safari (version 11+)
- Edge (version 79+)
- Any browser supporting:
  - HTML5 Canvas
  - ES6 JavaScript
  - `requestAnimationFrame`
  - `setTransform`

## 📁 File Structure

```
index.html
├── HTML Structure
│   ├── Clock Container (Canvas)
│   ├── Controls Panel
│   ├── Settings Modal
│   └── Info Modal
├── CSS Styling
│   ├── Layout & Positioning
│   ├── Controls & Buttons
│   ├── Theme Support
│   ├── Modal Styling
│   └── Responsive Design
└── JavaScript
    ├── Constants & Configuration
    ├── Animation System (Clock class)
    ├── Pattern Generation
    ├── Vortex Field Physics
    ├── Canvas Drawing Functions
    ├── Event Handlers
    └── Main Animation Loop
```

## 🎯 Key Classes & Functions

### Clock Class
Manages individual clock animation with:
- `setTargets()`: Set target angles for both hands with animation duration
- `update()`: Update animation state based on elapsed time

### VortexField Class
Simulates fluid dynamics:
- `vField()`: Calculate velocity field at coordinates
- `rk4Step()`: 4th-order Runge-Kutta integration step
- `getAngleDegrees()`: Derive angle from vector field

### Pattern Functions
- `getPatternAngles()`: Radial tangent spread pattern
- `getPatternAnglesCircleOpen()`: Circular expansion pattern
- `getPatternVector()`: Direct radial vectors
- `getPatternVectorTangent()`: Tangent to radial direction

### Rendering Functions
- `draw()`: Main render loop
- `drawClockFace()`: Prerendered clock background
- `drawHand()`: Individual hand with shadow effects
- `resize()`: Responsive layout calculation

## ⚙️ Configuration

All configuration constants are at the top of the JavaScript section:

```javascript
const Cols = 16;              // Grid columns
const Rows = 8;               // Grid rows
const MAX_FPS = 20;           // Frame rate cap
const HAND_SHADOW_OFFSET = 4; // Shadow position (pixels)
const HAND_SHADOW_BLUR = 8;   // Shadow blur radius
const HAND_SHADOW_ALPHA = 0.30; // Shadow opacity
```

### Themes
Add custom themes in the `themes` array within `setupControls()`:

```javascript
{
  name: 'Theme Name',
  hand: { r: 255, g: 255, b: 255, a: 1.0 },
  back: { r: 0, g: 0, b: 0, a: 1.0 },
  shadow: { r: 50, g: 50, b: 50, a: 0.61 }
}
```

## 🎓 Learning Points

This project demonstrates:
- **Canvas API**: Drawing, transformations, and performance optimization
- **Animation**: Interpolation, easing, and animation loops
- **Physics Simulation**: Vortex field and numerical integration
- **Responsive Design**: Viewport-aware layout
- **Color Science**: Theme-aware text contrast (luminance calculation)
- **Event Handling**: Keyboard and mouse interactions
- **State Management**: Clock state and pattern transitions

## 🚀 Performance Tips

1. **Lower Resolution**: Reduce `Cols` and `Rows` for slower devices
2. **Slower Transitions**: Increase default `TransitionSeconds` for smoother animations
3. **Reduced Patterns**: Comment out unused patterns to skip calculation
4. **Theme Caching**: Currently recalculates on theme change; could be precomputed

## 📝 License

This project is provided as-is for personal and educational use.

## 💡 Tips & Tricks

- **Press Space** while in the app to see the actual time displayed
- **Press F** to enter fullscreen for an immersive experience
- **Adjust transition speed** in settings to create different visual effects
- **Mix and match themes** with different transition speeds for unique combinations
- **Observe patterns**: Each pattern reveals different mathematical concepts

## 🔗 Related Projects

- Inspired by clock art and data visualization
- Uses numerical methods for fluid dynamics simulation
- Combines real-time data with animated visualization

---

**Made with ❤️ using vanilla JavaScript and HTML5 Canvas**