# Graphene Machine - Developer Documentation 🛠️

**Complete technical reference for developers, AI coders, and contributors**

## Table of Contents
- [Quick Start](#quick-start)
- [SVG Architecture](#svg-architecture)
- [Animation System](#animation-system)
- [Color System](#color-system)
- [Version History](#version-history)
- [Design Goals](#design-goals)

---

## QUICK START

### View Locally
```bash
# Clone and open
git clone https://github.com/AtomInnovationTH/GMX.git
cd GMX
open Graphene_Machine_v52.svg

# Or serve locally
python3 -m http.server 8000
# Navigate to http://localhost:8000/Graphene_Machine_v52.svg
```

### File Structure
```
GMX/
├── README.md                    # User-facing docs
├── DEVELOPERS.md                # This file (technical docs)
├── LICENSE                      # MIT License
├── .gitignore                   # Git ignore rules
└── Graphene_Machine_v52.svg     # Main animation
```

---

## SVG ARCHITECTURE

### Canvas Specifications
| Property | Value |
|----------|-------|
| **Dimensions** | 1600 × 780 px |
| **ViewBox** | 0 0 1600 780 |
| **Background** | #0d1117 (dark) |
| **Font** | SF Mono, Monaco, Cascadia Code |

### Component Layout
```
┌─────────────────────────────────────────────────────┐
│  Title Area                                         │
├─────────────┬───────────────────┬───────────────────┤
│             │                   │                   │
│  Left       │   Rotating Drum   │   Right           │
│  Labels     │   (Main View)     │   Specs           │
│             │                   │                   │
├─────────────┴───────────────────┴───────────────────┤
│  Control Buttons / Version Info                     │
└─────────────────────────────────────────────────────┘
```

---

## ANIMATION SYSTEM

### Rotation Cycle
```javascript
// Core timing
Rotation: CW from top view
Period: 27 seconds (0° → 360°)
Angular velocity: 13.33°/s

// All components unified:
// - Outer discs
// - Spokes
// - CVD Blades
// - Weld points  
// - Monel shell
```

### Triple Blade Configuration
| Blade | Phase Angle | Start Opacity | Color |
|-------|-------------|---------------|-------|
| **Blue (B)** | 180° | 1.0 @ 0s | #7aa2f7 |
| **Green (G)** | 60° | 0.70 @ 9s | #06d6a0 |
| **Purple (P)** | 300° | 0.45 @ 18s | #9d7cd8 |

### Helix Pattern
```
Bezier triple helix
├── Segments: 64
├── Depth-aware opacity (1.0 → 0.45)
└── Phase-synchronized with blade rotation
```

---

## COLOR SYSTEM

### CSS Variables
```css
:root {
  /* Material colors */
  --monel-dark: #8b5a2b;
  --monel-mid: #b87333;
  --monel-bright: #d4af37;
  
  --steel-dark: #404040;
  --steel-mid: #606060;
  --steel-light: #707070;
  
  --drum-dark: #303030;
  --drum-mid: #404040;
  --drum-light: #484848;
  
  /* Blade colors */
  --blade1-dark: #4a6aa7;
  --blade1-light: #7aa2f7;
  --blade1-bright: #a8c8ff;
  
  --blade2-dark: #6d4ca8;
  --blade2-light: #9d7cd8;
  --blade2-bright: #c8a8f8;
  
  --blade3-dark: #04a678;
  --blade3-light: #06d6a0;
  --blade3-bright: #40f8c0;
  
  /* Text styles */
  --title-main: #c0caf5;
  --title-section: #c0caf5;
  --subtitle: #7aa2f7;
  --label: #a9b1d6;
  --dim: #c9d1d9;
}
```

### Gradients
```xml
<!-- Monel alloy gradient -->
<linearGradient id="monelGrad">
  <stop offset="0%" stop-color="#8b5a2b"/>
  <stop offset="15%" stop-color="#b87333"/>
  <stop offset="50%" stop-color="#d4af37"/>
  <stop offset="85%" stop-color="#b87333"/>
  <stop offset="100%" stop-color="#8b5a2b"/>
</linearGradient>
```

---

## VERSION HISTORY

```
v52: Bezier triple helix (64-seg) + depth opacity
     Blade θ=180°/60°/300° | Opacity 1.0→0.45
     Phase B(0s)/G(9s)/P(18s)
     
v50: 20mm blades, 24 keyframes

v49: Simple Monel shell
```

---

## DESIGN GOALS

### Machine Specifications
| Parameter | Current | Target |
|-----------|---------|--------|
| **Width** | 9 mm | 100 mm → 10,000 mm |
| **Temperature** | 500°C | 700°C |
| **Layers** | Variable | 100 layers |
| **Strength** | Testing | 100 GPa |
| **Production** | Prototype | 1 km/day → 10,000 km/day |

### Cross-linking Strategy
```
Goal: Prevent van der Waals collapse to graphite

Methods:
├── Covalent carbon bridges
├── Controlled defect introduction
├── Chemical functionalization
└── Ion implantation (optional)
```

### CVD Process
```
Carbon Precursor: Ethanol (C₂H₅OH)
Carrier Gas: Argon → Sealed system (next)
Chamber: Near atmospheric pressure
Growth rate: ~0.1-1 μm/min
```

---

## MODIFYING THE SVG

### Adding New Components
1. Define gradients/styles in `<defs>` section
2. Use existing CSS classes for consistency
3. Synchronize animations to 27-second cycle

### Animation Example
```xml
<animateTransform
  attributeName="transform"
  type="rotate"
  from="0 cx cy"
  to="360 cx cy"
  dur="27s"
  repeatCount="indefinite"/>
```

### Interactive Controls (Optional)
```css
.control-btn { cursor: pointer; }
.control-btn:hover { opacity: 0.8; }
.control-btn rect { fill: #1a1f2e; stroke: #30363d; }
.control-btn text { fill: #7aa2f7; font-size: 11px; }
```

---

## CONTRIBUTING

1. Fork the repository
2. Create feature branch (`git checkout -b feature/improvement`)
3. Test SVG in multiple browsers (Chrome, Firefox, Safari, Edge)
4. Submit pull request

### Areas of Interest
- Animation refinements
- Additional views (cross-section, exploded)
- Interactive controls
- Performance optimization
- Mobile responsiveness

---

## RELATED PROJECTS

- [Space Monkey Game](https://github.com/AtomInnovationTH/SMX) — Uses GMX graphene tether concept
- ISEC Space Elevator research
- Graphene CVD production literature

---

**Version:** v52 | **Date:** 2025 | **Status:** Active Development

**See it in action:** [View Animation](https://atominnovationth.github.io/GMX/Graphene_Machine_v52.svg) 🔬⚙️
