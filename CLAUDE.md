# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

EO Player is a time-based image display application that cycles through images based on the current minute. The project uses Create React App but the actual application bypasses React and runs as a vanilla JavaScript app in `public/index.html`.

## Development Commands

```bash
# Start development server (http://localhost:3000)
npm start

# Build for production
npm run build

# Run tests
npm test
```

## Architecture

### Dual Application Structure

This repository contains both a React app (unused) and a vanilla JavaScript image viewer:

1. **Active Application**: `public/index.html`
   - Standalone JavaScript application that loads and displays images
   - Entry point when accessing the app
   - React is NOT used in the active application

2. **Unused React Scaffold**: `src/` directory
   - Standard Create React App structure
   - `src/index.js` has React rendering commented out (lines 7-12)
   - React components exist but are not rendered

### Image Display System

The application uses a URL-based screen selection system:

- URL format: `http://localhost:3000/#<screenId>`
- Images are loaded from `public/img/<screenId>/1.png` through `6.png`
- Example: `#center` loads images from `public/img/center/`

**Image Organization**:
```
public/img/
├── 1.png through 6.png (default/root set)
├── center/    (1-6.png)
├── left/      (1-6.png)
└── right/     (1-6.png)
```

### Display Logic

The core display mechanism in `public/index.html`:

1. **Image Loading** (`loadImages`): Preloads all 6 images for the selected screen into hidden `<img>` tags
2. **Time-Based Display** (`displayImage`): Uses `(new Date()).getMinutes() % imageUrls.length` to select which image to show
3. **Background Setting** (`setBackground`): Sets the selected image as a full-screen background with `background-size: cover`
4. **Update Interval**: Checks every 100ms if images are loaded, then displays the time-appropriate image

### Fixed Dimensions

The application is designed for portrait displays:
- Resolution: 1080×1920 pixels
- Full-screen, no-repeat, centered, fixed background
- No responsive behavior
