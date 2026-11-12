# Build & Break — Mobile + Web Update (V6)

## What's fixed and improved

- Rebuilt the mobile level-tools drawer around **one scroll container**. The drawer owns vertical scrolling; the palette and category groups no longer create nested or flex-collapsed scroll areas.
- Tool categories (Build, Obstacles, Hazards, Traps, Bosses, Powerups, Weapons, Helpers and Level) remain in a single vertical list. Every category and its tool buttons contribute to the drawer's natural scroll height.
- Added a portrait-fallback touch-scroll bridge: when the browser cannot rotate the device and the app uses its CSS landscape fallback, ordinary vertical finger swipes are mapped to the drawer's scroll position.
- Kept camera movement on the editor canvas in its dedicated directional pad, separate from the tool list.
- Made editor setup idempotent across Phaser scene restarts so action buttons and tool listeners are not repeatedly wrapped or rebound.
- Added a working, persistent Day/Night appearance switch on the home screen and in Settings. The UI and Phaser background layers change together.
- Refined feedback with animated toasts, ability-acquisition banners and a more celebratory level-completion dialog.
- Preserved the existing level format, editor actions, gameplay mechanics, level validation, and desktop game controls.
- Kept the same landing page on desktop and mobile.

## Run

Serve this folder from a static web server and open `index.html`. Phaser 3.80.1 is loaded from cdnjs, so the browser needs access to that CDN.

## Validation performed

- JavaScript syntax check (`node --check`): passed.
- CSS stylesheet parsing: passed with no parse errors.
- HTML duplicate-ID check: passed.
- ZIP archive integrity: checked after packaging.

A full click-through browser/device test could not be completed in this execution environment. Test the drawer on both a landscape Android browser and a portrait-only iOS browser before production deployment.

## Mobile browser note

Orientation locking and fullscreen are requested from user interactions where supported. Browser restrictions vary; the CSS-rotated landscape fallback remains in place for browsers that do not support orientation locking.
