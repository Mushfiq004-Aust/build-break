# Build & Break — Mobile polish update

This package contains the updated standalone Phaser 3 game.

## Updates in this build
- Slightly increased mobile gameplay camera zoom (desktop zoom remains unchanged).
- Reduced the size/visual weight of touch controls and kept them anchored to the lower corners.
- Moved toast and ability notifications into a consistent top notification lane so they avoid the player and touch controls.
- Added lightweight synthesized sound effects for notifications, pickups, abilities, jumping, attacks, damage and level completion.
- Added Sound and Vibration switches in Settings, with preferences saved locally. Vibration depends on browser/device support for the Vibration API.
- Added a Day/Night control to the in-game bar and Settings; removed the duplicate home-menu theme button.
- Replaced free-typing movement range with bounded minus/plus controls (minimum 1, maximum 12) on mobile and desktop.

## Run
Open `index.html` in a modern browser with internet access (Phaser 3.80.1 is loaded from cdnjs).

## Validation note
The inline JavaScript syntax, stylesheet parsing, duplicate element IDs, and ZIP integrity were checked. Automated browser/device interaction testing was unavailable in this environment, so please test on an actual phone before publishing.
