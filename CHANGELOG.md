# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
