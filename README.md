README.md
markdown

# NexTG Desktop

**Your All-in-One Desktop Toolkit**

A modern, lightweight Windows desktop application that brings network diagnostics,
file utilities, QR generation and everyday productivity tools together in one
polished, dark-themed interface.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D6?style=flat-square)
![Version](https://img.shields.io/badge/version-1.0.0-e63946?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-3ddc97?style=flat-square)
![Status](https://img.shields.io/badge/status-stable-success?style=flat-square)

---

## Overview

NexTG Desktop is a single-window toolkit built for users who need fast, reliable
utilities without juggling ten different applications. It combines live system
monitoring, network diagnostics, file inspection and everyday productivity tools
under one clean sidebar-driven interface.

- **Premium dark UI** — charcoal background, subtle red accent, smooth motion
- **Fully offline** except for the speed test and public IP lookup
- **Non-blocking** — every long-running operation runs on a background thread
- **Persistent settings** — preferences survive restarts
- **Portable or installed** — runs from a folder or via a Windows installer

---

## Screenshots

> Add your screenshots to `docs/screenshots/` and update the paths below.

| Dashboard | Network Tools |
|-----------|---------------|
| ![Dashboard](docs/screenshots/dashboard.png) | ![Network](docs/screenshots/network.png) |

| File Tools | QR Generator |
|------------|--------------|
| ![File Tools](docs/screenshots/files.png) | ![QR](docs/screenshots/qr.png) |

---

## Features

### Dashboard
Live system overview with six at-a-glance cards:
- Internet speed (last measurement)
- Public + local IP address
- System status with live network throughput
- Storage usage
- CPU usage
- RAM usage

Plus a **Quick Tools** grid for one-click access to the most-used tools.

### Network Tools
- **Internet Speed Test** — ping, download and upload via the public Ookla network
- **IP Information** — public IP, local IP, hostname, connection type, ISP, location
- **Ping Tool** — hostname or IP, up to 20 packets, reports min / avg / max / loss

### File Tools
- **File Information** — name, extension, size, location, created / modified / accessed dates
- **Hash Generator** — MD5, SHA-1, SHA-256, SHA-512 with a single pass over the file

### QR Generator
Create QR codes for **Text**, **URL**, **Email**, **Wi-Fi** and **Phone**. Preview,
save as PNG, or copy straight to the clipboard.

### Utilities
- **Password Generator** — length 4–128, uppercase / lowercase / digits / symbols,
  ambiguous-character filter, live strength scoring
- **Text Tools** — character, word, line and sentence counters, case conversion
  (UPPER, lower, Title, Sentence), remove duplicates, trim whitespace, remove blank lines
- **Unit Converter** — Length, Weight, Temperature, Storage and Time

### Settings
- Accent colour (six presets)
- Animations toggle — full premium motion, or lightweight instant mode
- Start with Windows
- Minimize to tray
- Notifications

### System Monitor
Real-time CPU, RAM, disk and network activity, updated on a background timer so
the UI never blocks.

---

## Requirements

### For end users
- Windows 10 or Windows 11 (64-bit)
- ~120 MB free disk space

### For building from source
- Python 3.11.0
- pip

---

## Installation

### Option 1 — Installer (recommended)

1. Download `NexTG-Setup.exe` from the [Releases](../../releases) page.
2. Run the installer and follow the wizard.
3. Launch **NexTG Desktop** from the Start menu or desktop shortcut.

### Option 2 — Portable build

1. Download `NexTG-Desktop-Portable.zip` from the [Releases](../../releases) page.
2. Extract the folder anywhere.
3. Run `NexTG Desktop.exe`.

### Option 3 — From source

```bash
git clone https://github.com/<your-username>/NexTG.git
cd NexTG

python -m venv .venv
.venv\Scripts\activate

pip install -r requirements.txt
python main.py

Building a Windows executable
bash

pip install pyinstaller

pyinstaller --noconfirm --clean --windowed --onefile ^
  --name "NexTG Desktop" ^
  --add-data "assets;assets" ^
  --add-data "data;data" ^
  --icon "icon.ico" ^
  main.py

The result is dist\NexTG Desktop.exe.

Notes

    --onefile produces a single portable executable (slower first launch).
    Use --onedir for a faster multi-file build.

    icon.ico should be a multi-resolution .ico file (16, 32, 48, 256 px).

    PyInstaller output can trigger antivirus heuristics. Code-sign the executable
    before public distribution.

Building a Windows installer

The recommended tool is Inno Setup.

    Install Inno Setup.

    Open the Script Wizard and point it to dist\NexTG Desktop.exe.

    Fill in the metadata:

        Application name: NexTG Desktop

        Version: 1.0.0

        Publisher: ArtaLabs

        Output file: NexTG-Setup.exe

    Compile.

The installer automatically generates the Start menu entry, an optional desktop
shortcut and an uninstaller.
Project structure
text

NexTG/
├── main.py                     # Application entry point
├── requirements.txt
├── README.md
├── icon.ico
├── app/
│   ├── config/                 # Constants (name, version, branding)
│   ├── ui/                     # Theme, icons, sidebar, title bar, main window
│   ├── pages/                  # One module per navigation page
│   ├── widgets/                # Reusable UI primitives (cards, toasts, toggles)
│   ├── services/               # System monitor, network, file and settings services
│   └── utils/                  # Helpers, signal bus, animation helpers, workers
├── assets/
│   ├── icons/
│   └── images/
└── data/
    └── settings.ini            # Created automatically on first run

Architecture notes

    UI ↔ services separation. Pages never block. Every long-running task
    (speed test, ping, hashing) runs on a QThread worker and reports back
    through Qt signals.

    Signal bus. app.utils.bus.Bus decouples pages from the main window —
    pages emit notify and navigate without holding a reference to the shell.

    Theme manager. ThemeManager is a singleton that owns the accent colour
    and the animation preference. Changing either takes effect immediately, with
    no restart required.

    Centralised animations. app.utils.animations routes every fade, stagger
    and progress animation through one gate, so the "Animations" setting is
    honoured across the entire application.

    Persistent settings. Stored in data/settings.ini and reloaded at startup.

Tech stack
Layer	Choice
Language	Python 3.11
GUI	PySide6 (Qt 6)
System metrics	psutil
HTTP	requests
QR codes	qrcode + Pillow
Speed test	speedtest-cli
Third-party services
Feature	Service	Notes
Public IP / ISP lookup	ipinfo.io	Free tier, no key required. Falls back to api.ipify.org.
Speed test	Ookla Speedtest network	Via speedtest-cli, no key required.
Ping	System ping binary	Falls back to a TCP-connect probe if ICMP is blocked.
Development

Run the app in place:
bash

python main.py

Lint:
bash

pip install ruff
ruff check .

License

Released under the MIT License. See LICENSE for details.
Credits

NexTG Desktop is developed by ArtaLabs.

Development Team: itslosti
