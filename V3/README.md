# Tempo Video Speed Regulator (V3)

A browser extension for controlling HTML5 video speed with the keyboard or the extension popup. The playback speed lock is enabled by default. Speed changes then remain in effect as the active video changes; use the lock control or `Numpad Decimal` to toggle it.

## Install for development

This folder is an unpacked browser extension; no build step or `npm install` is needed.

### Chrome, Edge, Brave, and other Chromium browsers

1. Open `chrome://extensions` (or `edge://extensions` in Edge).
2. Turn on **Developer mode**.
3. Select **Load unpacked** and choose this `V3` folder (the folder containing `manifest.json`).
4. Reload any tabs that were already open.

### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Select **Load Temporary Add-on…** and choose `V3/manifest.json`.
3. Reload any tabs that were already open. Temporary add-ons must be loaded again after Firefox restarts.

## Controls

| Action | Key |
| --- | --- |
| Increase speed | `Numpad +` or `+` / `=` |
| Decrease speed | `Numpad -` or `-` / `_` |
| Reset to 1× | `Numpad *` or `*` |
| Lock or unlock speed | `Numpad Decimal` (`Numpad Del`) |
| Play or pause | `Numpad 5` |
| Seek back / forward 5 seconds | `Numpad 4` / `Numpad 6` |

Keyboard shortcuts are ignored while typing in an input, select, textarea, or editable field. The popup provides speed controls, step size, presets, and display settings. The injected controls work with HTML5 video; browser-internal pages and some protected or non-HTML5 players may not allow extensions to control playback.

## Files

- `manifest.json` — extension permissions, popup, and content script registration.
- `content.js` — website video detection, keyboard controls, and on-page badge.
- `popup.html`, `popup.css`, `popup.js` — toolbar popup interface and controls.
- `index.html`, `styles.css`, `app.js` — standalone player interface.
