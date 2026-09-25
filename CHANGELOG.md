# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.4.5] - 2026-09-25

### Added
- Added a pause button long-press interaction (holding for 2 seconds) to toggle the reactive mesh and grid pulsing on or off.
- Added an animated circular SVG progress ring around the play/pause button to provide visual feedback during long-press actions.

### Changed
- Updated typography by replacing the `Orbitron` font with `Michroma` for the application loader and main title elements.
- Refined audio beat detection configuration: increased `ABSOLUTE_MIN_GATE` from 100 to 110 and `BEAT_COOLDOWN_MS` from 340ms to 400ms for more accurate kick recognition.
- Updated HUD statistics styling and layout, featuring larger stat values styled in `Rajdhani` with a vibrant magenta accent color (`--magenta2`).
- Expanded and updated the user interaction hint text in the bottom overlay to document the new long-press toggle functionality.

### Fixed
- Improved DOM structure around the player controls by introducing a dedicated container (`.player-btn-wrap`) to cleanly layer overlay indicators over the play button.

## [1.4.4] - 2026-06-06

### Added
- Added a dedicated low-pass biquad filter with a 120 Hz cutoff frequency for precise kick drum frequency isolation.
- Introduced a separate `beatAnalyser` node featuring a smaller FFT size and faster smoothing time constant specifically optimized for beat tracking.

### Changed
- Refactored the Web Audio API processing pipeline to use parallel routing for independent visual spectrum analysis and beat detection.

## [1.4.3] - 2026-09-24

### Added
- Centralized `AUDIO_CONFIG` configuration object for tuning audio reactivity, thresholds, smoothing factors, and decay rates.
- SEO description meta tag for improved search engine snippet generation.
- Mobile web app capability meta tags and `viewport-fit=cover` for edge-to-edge mobile display support.
- Explicit `sizes="180x180"` attribute on the Apple touch icon link reference.

### Changed
- Overhauled beat and kick detection with strict multi-gate verification (`MIN_OVERALL_VOLUME`, `ABSOLUTE_MIN_GATE`, and cooldown lockout periods).
- Upgraded live BPM estimation with dynamic threshold boosting, smooth decay, and automatic half-tempo correction for detected tempos above 180 BPM.
- Enhanced mesh wave reactivity to combine persistent baseline waviness with dynamic sub-bass impulse scaling.
- Bumped application title and version display to v1.43.

### Fixed
- Prevented false positive beat triggers and erratic visual pulsing during quiet audio passages by enforcing global volume and sub-bass energy gates.

## [1.4.2] - 2026-09-24

### Changed
- Reordered script tag hierarchy by moving the `<script type="importmap">` tag above preloading directives to ensure optimal specifier resolution during module parsing.
- Refactored Google Fonts embedding to use asynchronous, non-blocking stylesheet preloading with `<noscript>` fallbacks to improve First Contentful Paint (FCP).
- Optimized 3D WebGL context initialization by configuring the `powerPreference: 'high-performance'` hint on `THREE.WebGLRenderer`.
- Improved input responsiveness during interactive grid manipulation by adding passive event listening to `pointermove` events.
- Updated UI text branding to display version v1.42.

## [1.4.1] - 2026-09-24

### Changed
- Refactored `three.js` import structure to selective named exports targeting ES2022 to optimize bundle delivery.
- Added preconnect (`https://esm.sh`) and `modulepreload` links for Three.js v0.170.0 to improve initial load performance.
- Updated application UI version display to v1.41.

## [1.4.0] - 2026-09-24

### Added
- Added a loading screen (`#loader`) with a pulsing "INITIALIZING" animation.
- Implemented smooth CSS fade-in transitions (`transition: opacity 1.5s`) to reveal essential UI and scene elements (`.sun`, `#scene`, `#horizon`, `.frame`, `.stats`, `.bottom`) after loading.
- Added the `is-loading` CSS class to the HTML body to manage element visibility and user interactions during initial setup.

### Changed
- Updated the displayed version in the HTML title and subtitle tags from v1.32 to v1.40.
- Switched the horizon animation (`@keyframes glow`) from transparency adjustment (`opacity`) to CSS brightness filters (`filter: brightness()`).
- Switched the sun animation (`@keyframes sunfloat`) from transparency adjustment (`opacity`) to CSS brightness filters (`filter: brightness()`).
- Updated `will-change` properties for `.sun` and `#horizon` from `opacity` to `filter` for performance optimization with the new animations.
- Shortened the time display format (`#clock`) to hide seconds (`00:00` instead of `00:00:00`).
- Reduced the wave value (`#wave`) formatting from two decimal places to one (`.toFixed(1)`).
