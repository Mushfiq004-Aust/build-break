# Build & Break: Adventure

A browser-playable platform game and level editor. Open `index.html` in a modern browser. Phaser 3.80.1 is loaded from a CDN, so an internet connection is required.

## Mobile experience

- Phone gameplay uses a landscape-oriented game surface. On portrait phones, the complete game UI rotates into a landscape layout automatically, so the player does not need to rotate the physical phone just to use the interface.
- When the player starts a level, the game requests fullscreen and the Screen Orientation API's `landscape` lock where the browser supports them.
- Browser security rules still prevent a website from guaranteeing native device rotation or fullscreen immediately on link navigation. iOS Safari and some embedded browsers do not expose the same fullscreen/orientation APIs; the CSS landscape fallback keeps the game usable in those browsers.
- The mobile editor has a dedicated expandable Level Tools drawer. The level canvas remains clear while the drawer is closed.
- Play is a separate primary action. During gameplay, the header changes to Restart and Editor actions.
- Completion and other dialogs are rendered inside the fullscreen game surface, so the level-complete result remains visible.
- Touch controls support movement, jump, attack, dash, and weapon switching.
- Safe-area insets are respected for notches and home indicators.

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

The default level is playable, and custom levels can be built and shared with level codes. The game saves the current level locally in the browser.
