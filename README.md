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
>```id,name,group,marks```
>```10001,Ahmad Bin Ali,MERAH,95%```
>```10002,Siti Nurhaliza,BIRU,88%```
>```10003,John Doe,HIJAU,92%```

> **Note:** The headers must be exactly `id`, `name`, `group`, and `marks`.

### 📸 The Photos
Place all student photos in a single folder on your computer.

* **Naming Convention:** The filename must match the Student ID.
* **Example:** If the ID is `10001`, the photo must be named `10001.jpg` or `10001.png`.

---

## 🖥️ How to Use (The 2-Window Workflow)

To keep the broadcast clean while giving the operator controls, use the **Dual Window** method:

### Step 1: The Operator Window (Controller)
1.  Open `scanner.html` in your browser.
2.  Click **📂 Import CSV** and select your `.csv` file.
3.  Click **🖼️ Load Photo Folder** and select the folder containing your images.
    > **Note:** You must do this *every time* you reopen the browser due to security permissions.
4.  This window will stay in the center of your screen with all controls visible.

### Step 2: The Broadcast Window (Output)
1.  Open `scanner.html` again in a **new tab** or **new window**.
2.  Click the **📺 OBS Mode** button.
3.  The window title will change to `🔴 OBS OUTPUT`, the controls will vanish, and the layout will shift to the **Left Side (Vertically Centered)**.

### Step 3: Setup in OBS Studio
1.  Add a **Window Capture** source.
2.  Select `[chrome.exe]: 🔴 OBS OUTPUT`.
3.  *(Optional)* If you want to remove the background, click **🎨 Green** on the controller and use a **Chroma Key** filter in OBS.

---

## 🎮 Controls

| Button | Function |
| :--- | :--- |
| **🔍 SEARCH NAME** | Opens a large modal to type and search for a student manually. |
| **✨ Anim: ON/OFF** | Toggles the smooth slide-in animation. Default is **ON**. |
| **🎨 Green** | Toggles the background to bright green for Chroma Keying.
