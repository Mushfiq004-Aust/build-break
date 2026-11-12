# Build & Break — Mobile Editor Layout Fix

## Changes in this build

- Mobile editor categories are stacked vertically in the drawer.
- Build pieces, helpers, hazards and traps are presented as full-width vertical lists with readable touch targets and icons.
- Removed the camera movement controls from the tool drawer.
- Added a compact on-canvas camera D-pad at the right side of the editor, with press-and-hold movement in all four directions.
- Kept camera controls visible only while editing; they do not appear during gameplay.
- Preserved the shared home screen, gameplay, editor, settings, level format and desktop layout.

## Run

Serve this folder from a static web server and open `index.html`. Phaser 3.80.1 is loaded from cdnjs, so the browser needs access to that CDN.

## Mobile browser note

Orientation locking and fullscreen are requested when supported. Browser restrictions vary, so verify on target Android and iOS browsers before production release.
