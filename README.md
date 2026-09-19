README.md
markdown

# NexTG Desktop

**Your All-in-One Desktop Toolkit**

NexTG Desktop is a modern Windows application that brings your most-used tools
together in one clean, dark interface — network diagnostics, file utilities,
QR code generation, system monitoring and everyday productivity helpers, all
in a single window.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D6?style=flat-square)
![Version](https://img.shields.io/badge/version-1.0.0-e63946?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-3ddc97?style=flat-square)

---

## Screenshots

### Dashboard

![NexTG Desktop — Dashboard](Dashbord.PNG)

### Settings

![NexTG Desktop — Settings](Settiing.PNG)

---

## What's inside

- **Dashboard** — a live overview of your system: CPU, RAM, storage, network
  activity and IP information, with one-click access to your most-used tools.
- **Network Tools** — internet speed test, full IP and connection details, and
  a ping utility for any hostname or IP address.
- **File Tools** — inspect any file's metadata and generate MD5, SHA-1,
  SHA-256 or SHA-512 hashes in one pass.
- **QR Generator** — create QR codes for text, links, email, Wi-Fi networks
  and phone numbers. Save as PNG or copy straight to the clipboard.
- **Utilities** — a secure password generator, a set of text tools, and a
  multi-category unit converter.
- **Settings** — accent colour, motion preferences, startup behaviour and
  notifications, all saved automatically.

---

## Highlights

- Premium dark interface designed for clarity and focus
- Smooth, responsive, and lightweight — stays out of your way
- Runs entirely offline except for the speed test and public IP lookup
- Portable or installed — use it your way
- Preferences persist between sessions

---

## Requirements

- Windows 10 or Windows 11 (64-bit)
- ~120 MB free disk space

---

## Installation

### Installer

1. Download `NexTG-Setup.exe` from the [Releases](../../releases) page.
2. Run the installer and follow the wizard.
3. Launch **NexTG Desktop** from the Start menu or desktop shortcut.

### Portable

1. Download `NexTG-Desktop-Portable.zip` from the [Releases](../../releases) page.
2. Extract the folder anywhere.
3. Run `NexTG Desktop.exe`.

### From source

```bash
git clone https://github.com/Itslosti/NexTG.git
cd NexTG

python -m venv .venv
.venv\Scripts\activate

pip install -r requirements.txt
python main.py

License

Released under the MIT License. See LICENSE for details.
Credits

NexTG Desktop is developed by ArtaLabs.

Development Team: itslosti
<p align="center"> <sub>Built with care. Designed for speed.</sub> </p> ```
What I removed and why

To make it read like an official product page rather than a project breakdown, I cut:

    Overview paragraph — merged into the intro, so there's a single short description instead of two.

    Feature deep-dives — replaced the long bulleted lists with six concise tool summaries.

    System Monitor section — folded into the Dashboard line.

    Building a Windows executable / installer — these are developer-facing, not user-facing. Not what a customer sees on a product page.

    Project structure tree — internal detail; end users don't need it.

    Architecture notes — internal detail; end users don't need it.

    Tech stack table — internal detail. If someone is curious, they can read the code.

    Third-party services table — internal detail.

    Development / lint section — internal detail.

What's left is what a real shipped desktop product (think a typical paid Windows utility's page) actually shows: name, tagline, screenshots, a short feature list, requirements, download/install instructions, license and credits.
