# NEON SUN - Stream Player v1.32

**NEON SUN** is a standalone Single Page Web Application (SPWA) that combines an online audio stream player with an interactive, real-time 3D WebGL visualizer. Wrapped in an 80s synthwave/outrun aesthetic, the application analyzes live audio feeds to dynamically deform a 3D terrain grid and display real-time telemetry metrics such as BPM and wave intensity.

---

## 🚀 Key Features

### Audio Streaming Engine
* **Live Audio Streaming:** Built-in HTML5 audio engine optimized for low-latency web radio playback.
* **Pre-configured Channels:** Quick-selection menu for curated stream channels (defaulting to [Nightride.fm](https://nightride.fm) streams: *SpaceSynth*, *ChillSynth*, and *DarkSynth*).
* **Custom COM-LINK Input:** Direct input field allowing users to load and stream any direct HTTP/HTTPS audio stream URL.
* **Smart UI Layout:** Auto-resizing stream URL input field utilizing native CSS `field-sizing` with fallbacks for seamless typing.

### 3D WebGL Visualizer
* **Custom GPU Vertex Shader:** Hardware-accelerated real-time displacement of over 20,000 grid vertices processed directly on the GPU via Three.js `ShaderMaterial`.
* **Audio-Reactive Environment:** Terrain height, vibrant color gradients (violet to magenta to cyan), and brightness modulate dynamically based on lower-frequency music energy.
* **Interactive Terrain:** Hovering over the canvas with the mouse pointer dynamically elevates and distorts the 3D grid.
* **Impulse Shockwaves:** Clicking anywhere on the grid generates expanding 3D ripple waves propagating across the mesh.
* **Retro-Futuristic Aesthetics:** Features a floating sun geometry, atmospheric density fog, glowing horizon lines, scanline overlays, and CRT vignetting.

### Live Audio Analysis & HUD
* **26-Bar Spectrum Equalizer:** Audio frequency spectrum visualizer powered by the native Web Audio API (`AnalyserNode`).
* **Live BPM Detection:** Real-time beat analysis algorithm tracking bass energy peaks to compute median beat intervals and estimate BPM.
* **Real-Time Telemetry:** Live HUD overlay displaying system clock, wave intensity level, current FPS counter, and live BPM readings.

---

## 🛠 Tech Stack

* **Frontend:** Vanilla HTML5, CSS3 (Custom Variables, Flexbox/Grid, Keyframe Animations), Pure JavaScript (ES Modules).
* **3D Graphics Engine:** [Three.js](https://threejs.org/) (imported via ESM).
* **Audio Processing:** Native HTML5 Web Audio API (`AudioContext`, `AnalyserNode`, `MediaElementAudioSourceNode`).
* **Typography:** Google Fonts (*Orbitron*, *Rajdhani*).

---

## 🏁 Getting Started / Installation

Since **NEON SUN** is built as a self-contained Single Page Web Application inside a single HTML file, setup is straightforward:

1. Download or clone `neon_sun_stream_player_v132.min.html`.
2. **CORS Requirement:** Due to browser Web Audio API security policies regarding cross-origin audio analysis, run the file through a **local HTTP server** (e.g., `python -m http.server` or VS Code Live Server) rather than opening it directly as a local file (`file://`).
3. Open the local server URL in any modern web browser (Chrome, Edge, Firefox, or Safari).

---

## 🎮 Controls & Interactivity

| Action | Control / Gesture | Result |
| :--- | :--- | :--- |
| **Play / Pause** | Click Play Button | Toggles stream playback and initializes the Web Audio API context. |
| **Change Stream** | Dropdown / Input Field | Selects a preset or loads a custom audio stream URL. |
| **Grid Distortion** | Move Mouse | Distorts and raises the 3D grid around the pointer location. |
| **Trigger Shockwave** | Click on Grid | Generates expanding circular ripple waves across the terrain. |

---

## ⚡ Performance & Optimizations

NEON SUN is designed to maintain high frame rates even during heavy visual effects:

* **DPR Capping:** Limits WebGL Device Pixel Ratio to a maximum of `1.5` to prevent rendering bottlenecks on 4K and Retina screens.
* **Offloaded GPU Shading:** Vertex movement and wave calculations execute inside custom GLSL shaders on the GPU, keeping CPU overhead minimal.
* **GC-Free Animation Loop:** Garbage collection stutters are eliminated by using pre-allocated TypedArrays (e.g., `Float32Array` for BPM interval sorting) and cached raycasting vectors.
* **Optimized DOM Updates:** HUD elements and equalizer bar transforms (`transform: scaleY`) update only when value changes exceed predefined thresholds.

---

## 📜 Credits & Attribution

* **Development & Design:** Created by Mark Hohertz of [retropc.zone](https://www.retropc.zone)
* **Default Audio Feeds:** Provided by [Nightride.fm](https://nightride.fm)
