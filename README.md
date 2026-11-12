# Playback+ — Video Speed Controls

Playback+ is a browser extension for controlling HTML5 video speed with the numpad, keyboard shortcuts, or the on-video controls. The repository keeps each release in its own folder; **V3 is the current version**.

## Features

- Adjust playback speed on pages with HTML5 video, including YouTube and Vimeo.
- Use numpad shortcuts or standard `+`, `=`, `-`, and `*` keys where supported.
- Change speed from the popup dashboard or the on-video badge.
- Lock the selected speed so it carries over when the active video changes. The lock lasts for the current page session.
- Choose how the on-video badge appears:
  - **Always visible (transparent)** keeps the faint badge shown.
  - **Show after numpad use** hides the badge until a supported numpad action, then shows it for 2.5 seconds.
- Adjust speed increments and use preset speeds from the popup.
- The page overlay uses Shadow DOM to avoid most styling conflicts with websites.

## Keyboard Controls

| Action | Numpad key | Standard key |
|---|---|---|
| Speed up | `Numpad +` | `+` or `=` |
| Slow down | `Numpad -` | `-` |
| Reset speed to 1.0× | `Numpad *` | `*` |
| Lock or unlock speed | `Numpad Del` / `Numpad Decimal` | — |
| Play or pause | `Numpad 5` | — |
| Seek backward 5 seconds | `Numpad 4` | — |
| Seek forward 5 seconds | `Numpad 6` | — |

Shortcuts are ignored while a text field, search box, textarea, or editable element is focused.

## Install V3

The extension is not currently published in an extension store. Load it from the repository; no build step is required.

1. Clone the repository or download and extract its ZIP:

   ```bash
   git clone https://github.com/PrinceJoshi312/Playback-Plus.git
   ```

2. In your browser, load the **`V3` folder**—the folder containing `manifest.json`.

   **Chrome, Edge, Brave, Opera, and other Chromium browsers:**
   - Open `chrome://extensions/` (or the browser’s extension management page).
   - Turn on **Developer mode**.
   - Select **Load unpacked** and choose the repository’s `V3` folder.

   **Firefox:**
   - Open `about:debugging#/runtime/this-firefox`.
   - Select **Load Temporary Add-on…** and choose `V3/manifest.json`.

   Firefox removes temporary add-ons when it closes, so load the add-on again for a new session unless you package it for persistent installation.

3. Pin Playback+ from the browser’s extensions menu if you want quick access to the popup.

## Use the Extension

Open a page with a video and use the keyboard controls above or the on-video speed badge. Click the lock icon on the badge, or press **Numpad Del**, to lock or unlock the current speed. The popup lets you set a speed, choose a step size, and use presets.

To change the badge display mode, open the extension popup and select the gear/settings button. The selected mode is remembered by the extension.

When you update the files, refresh the extension from the browser’s extension management page and reload the video tab. In Firefox, reload the temporary add-on from `about:debugging`.

## Versions

- [**V1 — Keyboard controls**](v1/) — the original keyboard-focused extension.
- [**V2 — Keyboard and mouse controls**](v2/) — adds clickable speed controls to the on-video badge.
- [**V3 — Speed lock and display modes**](V3/) — the current version, with Numpad Del speed locking, an adjustable on-screen display, and the popup controls.

Each version folder contains its own extension files. Load the version folder you want to use, rather than the repository root.

## Contributing

Issues and pull requests are welcome. If you find a site where speed control does not work as expected, include the site name and a description of the video player behavior in an issue.
