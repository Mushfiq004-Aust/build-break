# Build & Break: Adventure

A browser-playable platform game and level editor. Open `index.html` in a modern browser. Phaser 3.80.1 is loaded from a CDN, so an internet connection is required.

## Mobile and responsive support

- Responsive play layout for phones, tablets, laptops, and desktop screens.
- Touch controls for movement, jump, weapon/action, dash, and weapon switching.
- Touch controls support pointer capture and release safely when the app loses focus.
- On supported Android browsers, entering Play requests fullscreen and landscape orientation. Browsers that do not support orientation locking continue normally and show a rotate hint in portrait.
- Mobile editor palette moves below the game view and remains horizontally scrollable; the toolbar also scrolls instead of overflowing.
- Phaser's FIT scaling keeps the 16:9 game view proportional across screen sizes.

**Important browser limitation:** a website cannot force a phone to open a link in landscape or fullscreen before the user interacts with it. The game requests fullscreen/orientation after the user taps Play, where the browser permits it. On iOS Safari and some in-app browsers, users may need to rotate the device manually.

## Controls

### Desktop
- Move: A/D or Left/Right arrows
- Jump: Space, W, or Up arrow
- Attack: X or J
- Dash: Shift (when unlocked)
- Switch weapon: Q
- Restart: R
- Return to editor: Esc

### Mobile
- Use the on-screen left/right controls to move.
- Jump: JUMP
- Attack: ⚔
- Dash: 💨 (when unlocked)
- Switch weapon: ⇄

### Editor
- Click/tap and drag to place objects.
- Right-click to erase on desktop; use the Erase tool on touch devices.
- Use the Pan tool or directional toolbar controls to navigate the level.
- Undo/redo, demo level, share codes, and load codes remain available.

The default level is playable, and custom levels can be built and shared with level codes.
