# Build & Break — ARGON + Mobile Editor Merge

## Latest fixes (controls layout + boss rework)
- **Controls Position (Below / Over) now works.** The game runs in mode `test`/`play`, but the CSS only targeted `play`, so the "below" layout never applied and the pad always covered the bottom of the screen. In Below mode the canvas now sits above a dedicated control strip; the camera zooms in part-way so the runner stays readable in the smaller window.
- **Editor look-around pad no longer covers the level (touch devices).** In landscape it has its own right-hand gutter with larger 40px buttons; in portrait it sits in a strip under the canvas. The canvas shrinks to fit instead of being overlapped.
- **Canvas double-centering removed** (Phaser autoCenter + flex centering pushed the canvas off-centre after a resize).
- **Bosses can no longer pass through walls.** All six bosses now move through a swept collision step (max 4px per sub-step, per axis). Flying bosses glide toward their pattern positions at a capped speed and stop at walls; Vesper's dive aborts when it hits a wall. Ground bosses use swept gravity with a 900px/s fall cap (no tunnelling, no floating gap). A boss that ever ends up inside a block is pushed to the nearest free spot.
- **Mourna's teleport** only picks free spots that have a clear line to her home position (same chamber) and, when possible, a clear line to you. She then reappears, flickers for ~0.45s, and only then fires, so the volley can be reacted to.
- **Falling-rock attacks** (Grumm stomp, Ignarax fire rain) are skipped when a ceiling is in the way instead of spawning inside it and vanishing.
- Ground bosses only launch an attack from the ground; boss phase/position are re-synced after respawn from a checkpoint.
- Verified in headless Chromium (phone viewport): with a wall between boss and player the original build let bosses 2, 3, 5 and 6 cross it; the fixed build keeps all six on their side with 0 frames inside solid blocks, and 2000 random Mourna teleports never landed inside or beyond a wall.


## Latest stability fixes
- Fixed Storm Serpent (Boss 6) not receiving its AI/update call, which could leave it inactive or broken during gameplay.
- Reworked moving-platform motion to use the analytic velocity of its smooth back-and-forth path instead of per-frame position correction, reducing platform surges and player shaking.
- Clamped Bat Lord tracking interpolation so a slow frame cannot cause a large movement overshoot.


A Phaser 3 pixel-platformer and level editor. This build uses the ARGON version as its base so its animated environments, character effects, boss animations, particle bursts, and level-completion celebration remain intact. It also incorporates the mobile zoom, audio/settings, and interaction improvements from the previous mobile build.

## Editor improvements

- **Select / Move:** Choose the quick action, tap an object, then drag it to a new grid cell. The object moves with the pointer; invalid placements are rejected.
- **Range prompt on placement:** Moving platforms, moving spikes, saws, boulders, and boss flags prompt for their range/number before placement.
- **Edit a placed range:** Select a moving object with Select / Move and use the top-bar `−` / `+` stepper to change its range. Range is clamped to 1–12; boss flags are limited to 1–5. Available map space is enforced.
- **Erase stays visible:** Select / Move and Erase are pinned above the mobile tool categories and at the top of the desktop palette. Erase can be dragged across multiple cells.
- **Undo/redo:** A drag or paint stroke is recorded as one undo action instead of creating partial undo states for every cell.
- **Range validation:** Imported and saved levels are checked for invalid range values; legacy moving-object ranges above the new limit are normalized when loaded.

## Gameplay fixes

- **Jump reliability:** Added a longer jump input buffer and a short coyote-time window, so pressing right and jump together near a block is less likely to lose the jump input.
- **Portal pairing:** Portals are paired in placement order. An unpaired portal does not teleport. After a teleport, the player must leave the portal area before another teleport can trigger, preventing automatic back-and-forth loops.
- **Day ground texture:** Day mode uses a muted earth-and-olive platform texture so the ground no longer blends into the bright green scenery.
- **Mobile camera:** Gameplay camera zoom is increased slightly on touch devices; touch controls are more compact to reduce obstruction of the player.

## Recent fixes

- **Dialog cleanup:** Switching from gameplay to the editor closes any active pause/settings/range dialog and clears the previous toast timer, preventing a popup from remaining over the editor.
- **Compact share codes:** New share codes use a compact LZW-compressed positional level format. The loader remains backward-compatible with the previous Base64-encoded JSON codes.
- **Web layout:** Desktop browsers use the mobile-style top bar and slide-out tool drawer, while retaining mouse and keyboard editing. Touch gameplay controls remain hidden for mouse-first desktop users.
- **Editor visibility:** The editor sidebar is wider, and the Erase quick action has a stronger border, contrast, and background.


## Checkpoint, boss, and movement fixes

- **Full checkpoint snapshots:** Activating a checkpoint now records collected pickups, keys, triggered one-shot hazards, falling-spike state, boss flags/health/awake state, and timed crumble/blink-platform state. Respawning restores that checkpoint snapshot instead of respawning earlier progress.
- **Permanent boss defeats:** Defeated bosses stay defeated after death. Their health bars remain hidden, their flags stay completed, and the HUD no longer reports a defeated boss as ahead. Bosses awakened by a flag remain awake after respawning rather than asking the player to activate the flag again.
- **Mover motion:** Moving platforms now follow their sinusoidal target path using the required frame velocity without the old hard speed clamp, reducing platform lag and player jitter.
- **Portal exit placement:** Teleport destinations are centered on the paired portal, and the exit latch still requires the player to leave the portal area before another teleport can occur.

## Settings and audio

- Sound effects include jumping, collecting keys and power-ups, checkpoints, boss events, damage, level completion, placing/erasing objects, and portals.
- Sound and vibration can be toggled independently in Settings and persist locally.
- Day/night mode is available in Settings and from the desktop/mobile top bar. The redundant More-sheet theme button has been removed.
- Settings can be opened from the desktop bar or mobile top bar and pause active gameplay until closed.

## Run locally

Serve this folder from a static web server and open `index.html`. Phaser 3.80.1 is loaded from the CDN, so an internet connection is required for the engine.

## Validation performed

- JavaScript syntax checked with Node.js.
- HTML parsed successfully.
- CSS parsed successfully.
- Checkpoint, boss-state, mover, and portal changes reviewed for state-reset consistency.
- CSS parsed with no stylesheet syntax errors.
- HTML IDs checked for duplicates.
- ZIP archive integrity checked after packaging.

A full interactive browser/device test could not be completed in this environment because Chromium navigation to the local test server is blocked by the execution environment. Please test the editor drag workflow and touch controls on an actual phone before publishing.


## Update: Creative tools, compact sharing, and weather themes

- Added Storm Serpent boss (boss #6), with a sweeping aerial pattern and five-shot projectile fan.
- Added Mega Trampoline, Wind Vent, and Shock Mine builder tools with gameplay interactions.
- Added Night, Day, Rain, Winter, and Thunder atmosphere modes. Weather effects are lightweight screen-space visuals.
- Replaced newly generated share codes with a compact bit-packed format. Codes are variable length (small/medium levels can fit roughly 50–100 characters); existing LZW and legacy Base64 JSON codes remain readable.

## Update: Mobile layout v2

- **Controls below the screen:** On touch devices the game canvas now gets its own area above a dedicated control strip, so the buttons no longer cover the platforms, sword swings or enemies. Settings → *Controls Position* switches back to floating buttons (⬆ Over).
- **Larger tap targets:** Move buttons are about 54–66px, Jump about 68–82px and Attack is slightly larger. The top bar is 56px tall with 44px buttons and 14.5px labels. Settings → *Button Size* scales the whole pad from 80% to 140%.
- **Left-handed layout:** Settings → *Left-Handed Layout* mirrors the pad.
- **Camera look-ahead:** The camera leans toward the direction of travel so more of the path ahead is visible. In Over mode the player is also lifted higher on screen.
- **Bigger HUD text** for deaths, time and keys.
- Preferences persist in localStorage (`bbctl`, `bbctlsz`, `bblefty`).
- Not yet tested in a real browser or on a device. Please check on a phone.

## Update: Boss fix

- **Slime King (Boss 1) never jumped.** The ground-contact step ran in the same frame the hop was launched and reset its upward velocity, so it only squashed and flickered in place. Hops are now preserved, so it jumps toward you, does a bigger slam hop every third jump (and every hop when enraged), and sends ground shockwaves on landing.
- Verified all six bosses' movement and attack logic in a headless simulation across all three health phases. The other five bosses already behaved as designed.

