# 🎓 Student Barcode Scanner & OBS Overlay

A serverless, browser-based tool designed for live event production (graduations, school assemblies, award ceremonies). It allows an operator to scan a student's ID barcode or manually search their name to trigger a broadcast-ready lower-third graphic containing their **Name**, **Group (Kumpulan)**, **Marks (Pencapaian)**, and **Photo**.

![Project Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Technology](https://img.shields.io/badge/Tech-HTML%20%2F%20JS%20%2F%20CSS-blue)

## ✨ Key Features

* **Dual-Window Sync:** Run a "Controller" window for the operator and a clean "Output" window for OBS. They sync instantly using the browser's `BroadcastChannel` API.
* **Zero Backend Required:** Runs entirely in your web browser. No servers, no databases, no installation.
* **USB Barcode Support:** Compatible with standard USB scanners (Keyboard Emulation).
* **CSV Data Import:** Load hundreds of student records instantly via Excel/CSV.
* **Local Photo Mapping:** Automatically matches student IDs to photos in a local folder.
* **Manual Search:** Large, touch-friendly search interface for when barcodes fail.
* **OBS-Ready:** Dedicated "OBS Mode" with specific layout (Vertical Center Left) and Green Screen support.
* **Animations:** Smooth fade-in/fade-out transitions (toggleable).

---

## 🚀 Getting Started

### 1. Installation
There is no installation required.
1.  Download the `scanner.html` file from this repository.
2.  Open it in **Google Chrome** or **Microsoft Edge**.

### 2. Preparing Your Data

**The CSV File:**
Create a `.csv` file using Excel or Notepad with the following header and structure:
```csv
id,name,group,marks
10001,Ahmad Bin Ali,MERAH,95%
10002,Siti Nurhaliza,BIRU,88%
10003,John Doe,HIJAU,92%
