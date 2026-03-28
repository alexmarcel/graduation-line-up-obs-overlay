# Graduation Line-Up OBS Overlay

A serverless, single-file browser tool for live graduation ceremony production. An operator scans a student's ID barcode (or searches by name) to instantly trigger a broadcast-ready lower-third graphic in OBS Studio — displaying the student's **Name**, **Group**, **Achievement/Marks**, and **Photo**.

![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Tech](https://img.shields.io/badge/Tech-HTML%20%2F%20CSS%20%2F%20JS-blue)
![No Install](https://img.shields.io/badge/Install-None-lightgrey)

<img width="1430" height="803" alt="Screenshot" src="https://github.com/user-attachments/assets/04e42ad5-cfa8-44f9-afa8-823ad82d89c2" />

**Sample usage:** https://www.facebook.com/ilkkmtawau/videos/1556095438983504

---

## Features

- **Dual-window sync** — Controller window for the operator, clean Output window for OBS. Synced in real time via the browser's `BroadcastChannel` API
- **Zero backend** — Runs entirely in the browser. No server, no database, no installation
- **USB barcode scanner support** — Works with any standard USB scanner in keyboard emulation mode
- **CSV data import** — Load hundreds of student records instantly from Excel/CSV
- **Photo & audio sync to OBS window** — Photos and audio are converted to base64 and stored in browser storage so the OBS window receives them automatically. If storage is full, load them directly in the OBS window using the built-in import buttons
- **Audio announcement** — Load a folder of `.wav`/`.mp3` files named by student ID; plays automatically on scan (toggleable)
- **Student line-up sidebar** — Live scrolling queue showing all students; click any row as a manual fallback if the scanner fails
- **Print barcodes** — Generate and print a full sheet of Code 128 barcode labels (one per student) directly from the browser
- **Manual search** — Search by name or ID with instant results
- **Display card customization** — Toggle avatar visibility, rounded/flat card shape, left/center/right text alignment; all settings sync to the OBS window
- **Accent color picker** — Customize the card's glow/accent color with per-slot swatches + color picker; persists across sessions
- **Chroma key support** — Switch background to any color (green, blue, magenta, custom) for OBS Chroma Key filter
- **Animation toggle** — Smooth slide-in/fade transitions, toggleable
- **OBS Mode** — Hides all controls; one-click exit back to controller

---

## Quick Start

### 1. Download
Download `scanner.html` and open it in **Google Chrome** or **Microsoft Edge**. No installation needed.

### 2. Prepare your CSV

Create a `.csv` file with the following columns:

```
id,name,group,marks
10001,Ahmad Bin Ali,MERAH,95%
10002,Siti Nurhaliza,BIRU,88%
10003,John Doe,HIJAU,92%
```

> Column headers must be exactly `id`, `name`, `group`, `marks`.

### 3. Prepare your photos *(optional)*

Put all student photos in one folder. Name each file after the student ID:

```
10001.jpg
10002.png
10003.jpg
```

### 4. Prepare your audio files *(optional)*

Put `.wav` or `.mp3` announcement files in one folder, named by student ID:

```
10001.wav
10002.mp3
```

---

## Two-Window Workflow

### Controller Window
1. Open `scanner.html` in your browser
2. Click **Import CSV** and select your `.csv` file
3. Click **Import Photos** and select your photos folder — photos are automatically synced to the OBS window via browser storage
4. *(Optional)* Click **Import Audio** and select your audio folder — audio syncs the same way
5. Use the scan input or **Search** button to display students

### Output Window (OBS)
1. Open `scanner.html` in a **new tab or window** (same browser)
2. Click **OBS Mode** — controls disappear, layout shifts to lower-third position
3. In OBS Studio, add a **Window Capture** source and select the output window
4. *(Optional)* Enable **Chroma Key** in OBS and match the background color set in the controller

> **If photos or audio don't appear in the OBS window** (e.g. browser storage is full, or the OBS window was opened before importing), use the **Photos** and **Audio** buttons in the bottom-right corner of the OBS window to load them directly there.

### Reverting from OBS Mode
Click the **Controller Mode** button in the top-right corner of the OBS window to return to the controller.

---

## Controls Reference

### Controller Sidebar

| Control | Description |
|:---|:---|
| **Search** | Open the search modal to find a student by name or ID |
| **View All Students** | Browse all loaded students with photo and audio status |
| **Import CSV** | Load student data from a `.csv` file |
| **Import Photos** | Load a folder of student photos (syncs to OBS window) |
| **Import Audio** | Load a folder of audio announcement files (syncs to OBS window) |
| **Audio: ON/OFF** | Toggle audio playback on scan |
| **Anim: ON/OFF** | Toggle the card slide-in animation |
| **Chroma: ON/OFF** | Toggle chroma key background |
| **OBS Mode** | Switch this window to broadcast output mode |
| **Clear** | Remove the current student card from the screen |
| **Print Barcodes** | Open print preview with a full sheet of student barcode labels |
| **Align buttons** | Set display card text to left / center / right |
| **Show Avatar on Card** | Toggle the student photo on the display card |
| **Rounded Card** | Toggle the pill-shaped left side of the display card |
| **Color swatches** | Change the card accent/glow color |
| **Chroma palette** | Change the chroma key background color |

### OBS Window (bottom-right, visible in OBS mode only)

| Button | Description |
|:---|:---|
| **Photos** | Load photo folder directly into the OBS window |
| **Audio** | Load audio folder directly into the OBS window |

---

## Scanner Fallback (If Barcode Scanner Fails)

If the physical scanner stops working mid-ceremony, the operator has two seamless fallbacks without interrupting the broadcast:

1. **Click any row in the sidebar** — the student line-up panel shows all students; clicking a row immediately puts them on screen
2. **Search button** — type the student name or ID and click the result

Both methods sync to the OBS output window normally.

---

## Photo & Audio Sync Notes

Photos and audio files are converted to base64 data URLs when imported and stored in the browser's `localStorage`. This allows the OBS window (a separate tab/window) to access them without re-importing.

**Limitations:**
- Browser `localStorage` is typically limited to ~5–10 MB. Large photo sets or high-bitrate audio files may exceed this limit
- If storage is full, a toast notification will appear directing you to load files directly in the OBS window using its built-in import buttons
- Both windows must be in the **same browser** (e.g. both in Chrome) for sync to work

---

## Troubleshooting

**Scanner beeps but nothing happens**
Configure your barcode scanner to append an Enter/CR suffix after each scan. This is standard and usually set via a programming barcode in the scanner's manual.

**Photos not showing in OBS window**
Either browser storage is full (check for a toast warning), or the OBS window was opened before photos were imported. Use the **Photos** button in the bottom-right corner of the OBS window to load them directly.

**Audio not playing**
Check that the audio filename matches the student ID exactly and that **Audio: ON** is active. If in the OBS window, use the **Audio** button in the bottom-right to load audio directly. Some browsers require a user interaction before audio is allowed to play.

**Two windows not syncing**
Both windows must be open in the **same browser application** (e.g. both in Chrome). Cross-browser sync is not supported.

**OBS captures the wrong window**
Make sure you clicked **OBS Mode** on the second window. The window title changes to `OBS OUTPUT` — this is what OBS looks for in Window Capture.

---

## Tech Stack

- Vanilla HTML / CSS / JavaScript — no frameworks, no build tools
- [`BroadcastChannel` API](https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel) for cross-window sync
- [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) for photo/audio/settings persistence across windows
- [JsBarcode](https://github.com/lindell/JsBarcode) (CDN) for barcode generation
- [Lucide Icons](https://lucide.dev) (CDN) for UI icons
- [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts
