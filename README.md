# 🎓 OBS Student Barcode Scanner Overlay

A lightweight, browser-based overlay for OBS Studio designed for live events, graduations, or school streams. It allows an operator to scan a student's barcode, which instantly triggers a lower-third style graphic on the live stream showing the student's **Name**, **Group (Kumpulan)**, **Marks (Pencapaian)**, and **Photo**.

The best part? **No web server, database, or backend required.** It runs entirely in your local web browser using CSV files and local folders.

## ✨ Features

* **Dual-Window Sync System**: Open the file twice. One window acts as your **Controller** (with buttons and search), and the other acts as the **OBS Output** (clean graphic). They sync instantly using the browser's native `BroadcastChannel`.
* **USB Barcode Support**: Works out-of-the-box with standard USB barcode scanners (Keyboard emulation with Enter suffix).
* **Local CSV Import**: Easily load hundreds of students using a standard `.csv` file. Data is saved to your browser's Local Storage.
* **Local Photo Import**: Map student IDs to local image files seamlessly.
* **Manual Search**: Built-in modal to manually search and trigger names if a barcode fails to scan.
* **Customizable Animations**: Toggle smooth fade-in/fade-out transitions.
* **Green Screen Ready**: Built-in Chroma Key background toggle for easy OBS integration.

---

## 🚀 Getting Started

### 1. Installation
Because this is a serverless application, installation is incredibly simple:
1. Download or clone this repository.
2. Locate the `scanner.html` file.
3. Open `scanner.html` in Google Chrome, Microsoft Edge, or OBS Browser Source (Note: Chrome/Edge is recommended for the Controller window).

### 2. Prepare Your Data
You need two things to use this system: a CSV file and a folder of photos.

**A. The CSV File (`students.csv`)**
Create a CSV file (e.g., using Excel) with the following exact columns: `id,name,group,marks`.
```csv
id,name,group,marks
10001,John Doe,Class A,85%
10002,Jane Smith,Class B,92%
10003,Alex Johnson,Class A,78%
