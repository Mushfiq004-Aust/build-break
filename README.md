# Build & Break — Responsive Game Build

## What's included

- Shared home/landing screen used as the default entry point on desktop and mobile.
- Home actions for Play, Level Editor, Settings, and How to Play.
- Play starts the current saved level; the editor opens the existing Phaser level editor.
- Desktop toolbar includes a Home action so players can return to the landing screen.
- Mobile editor keeps its tools in the slide-out drawer and retains a separate Play action.
- Home screen layout is compact and non-scrollable on mobile, including short landscape viewports and the portrait-device rotated-layout fallback.
- Mobile fullscreen and landscape orientation are requested when entering the game; browser support and gesture restrictions still apply.
- Existing Phaser gameplay, level format, and saved levels are retained.

## Run

Serve this folder from any static web server and open `index.html` in a modern browser. Phaser 3.80.1 is loaded from cdnjs, so the browser needs access to that CDN.

## Mobile browser note

A web page cannot universally force a browser to enter fullscreen or lock orientation on initial navigation. Build & Break requests these capabilities after a user gesture and uses its CSS landscape fallback where supported. Test on the target Android and iOS browsers before production deployment.
