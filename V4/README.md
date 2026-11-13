# Tempo V4: Browser-Neutral Video Speed Control Extension

A high-performance, browser-neutral browser extension (Manifest V3) that regulates video playback speed on any website (YouTube, Vimeo, Netflix, custom players, etc.) using your Numpad keyboard controls.

## Features
- **Browser API handling**: Uses the `chrome.*` or `browser.*` extension API namespace supported by the browser. The extension targets Manifest V3; browser-specific packaging and permission prompts may differ.
- **Global Injections**: Automatically detects HTML5 players on any web page.
- **Numpad Mapping**: Fast, single-keypress speed regulations.
- **Laptop Fallback**: Works on standard laptop keys too.
- **Shadow DOM Overlay**: Premium HUD display inside the page that is protected from website CSS overrides.
- **Responsive Popup Dashboard**: Accessible speed controls, customizable increments, and preset quick actions.
- **On-Screen Display Modes**: Keep the speed badge faintly visible or show it briefly after a numpad action.
- **Per-site speed**: Remembers the selected speed by HTTP/HTTPS hostname and restores it as the locked speed.
- **Custom shortcuts**: Set or disable each playback shortcut from the extension settings page.

---

## Keyboard Controls Reference

| Action | Numpad Key | Standard Laptop Key |
|---|---|---|
| **Speed Up** | `Numpad +` | `+` or `=` |
| **Slow Down** | `Numpad -` | `-` |
| **Reset Speed (1.0x)** | `Numpad *` | `*` |
| **Lock / Unlock Speed** | `Numpad Del` | - |
| **Play / Pause** | `Numpad 5` | - |
| **Seek Backward (5s)** | `Numpad 4` | - |
| **Seek Forward (5s)** | `Numpad 6` | - |

> [!NOTE]
> Keyboard hotkeys automatically disable when typing in text boxes, search fields, or textareas so they won't interfere with typing comments or search queries.

Choose the on-screen display behavior from the settings panel. In **Show after numpad use** mode, the speed badge appears for 2.5 seconds after a supported numpad action.

## V4 settings and storage

Open **Keyboard shortcuts** from the popup to change any action. Click a field and press a key or key combination; use Backspace/Delete to disable it. Assignments must be unique; duplicate shortcuts are reported and cannot be saved. Defaults retain V3's Numpad mappings, including laptop `+`, `=`, `-`, `_`, and `*` aliases for speed controls. Those aliases apply only while the corresponding default binding is selected. Shortcuts do not run while an input, select, textarea, or editable field has focus.

Playback speed is saved under `tempoSiteSpeed:<hostname>` in the extension's local storage. It applies across pages on that hostname, and a restored value is locked by default. **Reset this site's saved speed** removes the hostname preference and resets the current video to 1.0x. If extension storage is unavailable, speed controls continue to work for the current page session but cannot persist preferences. Browser-internal and invalid URLs are excluded by the HTTP/HTTPS hostname check. Shortcut settings use the `tempoShortcuts` storage key.

Storage is browser-profile local and is not synchronized between browsers. Reload already-open tabs after changing shortcuts if they do not receive storage change events. Browser support depends on a browser's Manifest V3 and WebExtensions API implementation; Safari and other browsers beyond current Chrome and Firefox have not been verified for this build.

Some browser or operating-system reserved key combinations may be intercepted before a page receives them, so they may not be usable as shortcuts. Available key names and behavior can also vary by keyboard layout.

---

## How to Install the Extension in Your Browser

Since this is in development format, you can load it directly into your preferred browser:

### For Chromium-Based Browsers (Chrome, Edge, Brave, Opera, Vivaldi)
1. **Open Extension Management Page**:
   - In Chrome, navigate to: `chrome://extensions/`
   - Or click the Extensions menu (puzzle piece icon) and select **Manage Extensions**.
2. **Enable Developer Mode**:
   - Toggle the **Developer mode** switch in the top-right corner of the extensions page.
3. **Load the Extension**:
   - Click the **Load unpacked** button in the top-left corner.
   - Select the V4 folder containing `manifest.json`.
4. **Pin for Easy Access**:
   - Click the extensions puzzle icon in the browser toolbar and pin **Tempo Video Speed Regulator**.

### For Mozilla Firefox (Gecko-Based)
1. **Open Debugging Console**:
   - In Firefox, navigate to: `about:debugging#/runtime/this-firefox`
2. **Load Temporary Add-on**:
   - Click the **Load Temporary Add-on...** button.
3. **Select Manifest File**:
   - Navigate to the V4 folder and choose its `manifest.json` file.
4. **Test & Play**:
   - The extension will instantly load and remain active for your current browser session.

---

## Project Structure

- `manifest.json` – Extension configuration and settings page.
- `content.js` – Per-tab playback, site speed persistence, shortcuts, and video HUD.
- `popup.html`, `popup.css`, `popup.js` – Popup controls and settings entry point.
- `settings.html`, `settings.css`, `settings.js` – Shortcut editor and duplicate validation.
