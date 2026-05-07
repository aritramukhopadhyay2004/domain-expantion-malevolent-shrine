# 🏯 Malevolent Shrine — Domain Expansion Detector

> *"伏魔御廚子" — Fukuma Mizushi*

An **interactive, real-time hand-gesture-activated visual experience** inspired by Ryomen Sukuna's Domain Expansion from *Jujutsu Kaisen*. This browser-based application uses your webcam and **MediaPipe hand-tracking AI** to detect when you perform the iconic **Namaskaram (prayer hands) gesture**, triggering a cinematic "Domain Expansion" sequence with dramatic visual effects — all running entirely in the browser with zero server dependencies.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![MediaPipe](https://img.shields.io/badge/MediaPipe-4285F4?style=for-the-badge&logo=google&logoColor=white)

---

## ✨ Features

### 🖐️ AI-Powered Gesture Recognition
- Real-time **dual-hand landmark detection** using Google's MediaPipe Hands ML model (21 landmarks per hand)
- Custom **Namaskaram / prayer-hands gesture scoring** algorithm based on:
  - Wrist proximity between both hands
  - Fingertip proximity alignment
  - Finger extension detection (fingers pointing upward)
  - Vertical wrist alignment validation
- Hold-to-activate mechanic — maintain the gesture for ~2 seconds to trigger Domain Expansion

### 🎬 Cinematic Domain Expansion Sequence
When the gesture is held long enough, the full activation sequence triggers:
- ⚡ **White flash bang** with instant opacity spike
- 🌊 **Expanding shockwave ring** with red glow radiating from screen center
- 📳 **Screen shake animation** with multi-axis tremor
- 🎥 **Background video swap** — webcam feed seamlessly transitions to a custom Domain Expansion video
- 🔴 **Vignette overlay** darkens the edges for dramatic focus
- 🀄 **Floating kanji characters** (呪, 斬, 術, 魔, etc.) rise and fade across the screen
- ⚔️ **Animated slash effects** — procedural cursed-energy slash lines rendered on a canvas layer
- 📡 **Scan-line overlay** — subtle red scan lines for a corrupted, cursed visual feel
- 🏷️ **Domain name reveal** — "Malevolent Shrine" / "伏魔御廚子" title card fades in

### 🎨 Visual Design
- Cinematic **dark UI with gold accents** (#C9A84C) inspired by cursed energy aesthetics
- Premium typography via **Cinzel Decorative** (headings) and **Noto Sans JP** (Japanese text & UI)
- **Glassmorphism debug bar** with blur backdrop and gradient fade
- Decorative corner brackets and HUD-style status readouts
- Real-time **charge bar** showing gesture-hold progress
- Responsive design — works across screen sizes

### 🔧 Debug & Development Tools
- Toggle-able debug bar (press `D`) showing real-time diagnostics:
  - Hands detected count
  - Wrist delta distance
  - Fingertip delta distance
  - Finger extension counts
  - Gesture score (out of 4)
  - Hold frame counter
  - Domain activation state
  - Video playback state
- Force-activation mode (press `Space`) for testing without a camera

---

## 🚀 Getting Started

### Prerequisites
- A modern browser (Chrome, Edge, Firefox) with **webcam access**
- A local or hosted web server (for camera permissions) — or just open the file directly

### Quick Start
```bash
# Clone the repository
git clone https://github.com/aritramukhopadhyay2004/domain-expantion-malevolent-shrine.git
cd domain-expantion-malevolent-shrine

# Open in browser (any of these work)
# Option 1: Direct file open
start "malevolent shrine.html"      # Windows
open "malevolent shrine.html"       # macOS

# Option 2: Local server (recommended for camera permissions)
npx serve .
# Then navigate to http://localhost:3000
```

### Usage
1. Click **"Open Domain"** to grant camera access
2. Position yourself in front of the webcam
3. Press both palms together in a **Namaskaram / prayer gesture** with fingers pointing upward
4. **Hold the gesture** for ~2 seconds — watch the charge bar fill
5. The Domain Expansion activates with full cinematic effects
6. Release your hands to deactivate

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `D` | Toggle debug diagnostics bar |
| `Space` | Force-activate Domain Expansion (for testing) |

---

## 🏗️ Architecture

```
malevolent-shrine/
├── malevolent shrine.html    # Complete self-contained application (HTML + CSS + JS)
├── domain expansion.mp4      # Background video asset for domain activation
└── README.md                 # This file
```

### Technical Stack
| Layer | Technology |
|-------|-----------|
| Structure | HTML5 with semantic elements |
| Styling | Vanilla CSS with animations, keyframes, gradients, and glassmorphism |
| Logic | Vanilla JavaScript (ES6+) |
| Hand Tracking | [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html) v0.4 via CDN |
| Camera | [MediaPipe Camera Utils](https://google.github.io/mediapipe/solutions/camera_utils.html) via CDN |
| Rendering | HTML5 Canvas 2D (dual-layer: effects + hand skeleton) |
| Typography | Google Fonts (Cinzel Decorative, Noto Sans JP) |

### Rendering Pipeline
The application runs a **60fps render loop** managing multiple visual layers (bottom to top):

1. **Webcam feed** (`<video>`) — live mirrored camera input
2. **Domain video** (`<video>`) — fades in on activation
3. **Effects canvas** (`<canvas>`) — cursed energy overlay, slashes, scan lines
4. **Hand skeleton canvas** (`<canvas>`) — landmark connections and fingertip highlights
5. **Flash / Shockwave / Vignette** (`<div>`) — CSS-driven dramatic effects
6. **Floating Kanji** (dynamic `<div>`) — spawned and animated via CSS keyframes
7. **HUD overlay** — status text, charge bar, domain title reveal

### Gesture Scoring Algorithm
The Namaskaram gesture is evaluated on a **4-point scoring system** every frame:

| Check | Condition | Points |
|-------|-----------|--------|
| Wrist Proximity | Both wrists within 0.35 normalized distance | +1 |
| Fingertip Alignment | Average tip distance < 0.32 | +1 |
| Finger Extension | At least 2 fingers extended upward on each hand | +1 |
| Vertical Alignment | Wrist Y-positions within 0.28 of each other | +1 |

A score of **≥ 2** begins charging. Holding at max charge (**55 frames**) triggers full activation. After release, there's an **80-frame grace period** before deactivation.

---

## 📸 Screenshots

> *Add screenshots or a GIF/video of the project in action here.*

---

## 🎯 Inspiration

This project is a tribute to **Ryomen Sukuna's Domain Expansion: Malevolent Shrine (伏魔御廚子)** from the manga/anime series **Jujutsu Kaisen** by Gege Akutami. The Namaskaram gesture was chosen as the activation seal as a nod to the hand signs used by jujutsu sorcerers to deploy their domains.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

<p align="center">
  <em>"Stand proud. You are strong."</em><br>
  <strong>— Ryomen Sukuna</strong>
</p>
