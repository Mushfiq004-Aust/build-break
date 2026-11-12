# Build & Break: Adventure

A browser-playable Phaser 3 platform game with a level editor. Open `index.html` in a modern browser. Phaser 3.80.1 is loaded from a CDN, so an internet connection is required.

## Mobile app experience

- Mobile opens into a dedicated loading splash and main menu instead of dropping players directly into the editor.
- Main menu actions are separated into **Play**, **Level Editor**, **Settings**, and **How to Play**.
- The app requests landscape orientation on load and again from menu interactions. When native orientation locking is unavailable (notably in iOS Safari and some embedded browsers), the complete app surface rotates into a landscape layout so the player does not need to rotate the physical phone.
- Fullscreen is requested from user interaction because browsers generally block automatic fullscreen on initial navigation.
- Play and Level Editor are separate destinations. The mobile editor remains in the immersive app shell and exposes its tools through a slide-out drawer.
- The editor drawer contains building categories, undo/redo, clear, demo level, movement range, pan controls, share/load level codes, character customization, and help.
- The gameplay HUD and touch controls are sized for landscape mobile screens and safe-area insets.
- Level-completion dialogs are mounted at the application level (outside the Phaser canvas wrapper) and use a fixed high-priority overlay, so the victory result is not clipped by the game canvas or fullscreen layout.

## Desktop controls

- Move: A/D or Left/Right arrows
- Jump: Space, W, or Up arrow
- Attack: X or J
- Dash: Shift (when unlocked)
- Switch weapon: Q
- Restart: R
- Return to editor: Esc

## Mobile controls

- Move: on-screen left/right controls
- Jump: JUMP
- Attack: ⚔
- Dash: 💨 (when unlocked)
- Switch weapon: ⇄

## Level editor

- Tap or drag to place objects; choose tools from the Level Tools drawer.
- Use the Erase tool on touch devices.
- Use the Pan tool or directional controls to navigate the level.
- Undo/redo, clear, demo level, movement range, share codes, load codes, character customization, and help are available in the drawer.
- The desktop editor retains its original sidebar and toolbar layout.

The default level is playable, custom levels can be built and shared with level codes, and the current level is saved locally in the browser.

## Browser limitations

A web page cannot guarantee that every mobile browser will physically rotate the device or enter fullscreen immediately when a link is opened. Orientation lock and fullscreen are requested where supported and permitted by browser gesture rules; the CSS landscape fallback handles portrait-only browsers.
