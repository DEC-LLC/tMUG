# tMUG — Tailscale Multiplatform User GUI

<div align="center">

**A lightweight, open-source graphical interface for managing Tailscale VPN connections.**

Connect, disconnect, authenticate, manage exit nodes, and check status — without touching a terminal.

[![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20Windows-lightgrey.svg)]()
[![Status](https://img.shields.io/badge/status-Production%20(Linux)-brightgreen.svg)]()

[Features](#features) · [Install](#install) · [Requirements](#requirements) · [Screenshots](#screenshots) · [Contributing](#contributing)

</div>

---

## What is tMUG?

[Tailscale](https://tailscale.com/) is an excellent mesh VPN — but on Linux and Windows, there's no official GUI. You manage it from the terminal: `tailscale up`, `tailscale status`, `tailscale set --exit-node=...`. For engineers, that's fine. For everyone else on your team — the people who just need to connect to the VPN and get to work — it's a barrier.

**tMUG** puts Tailscale in the system tray with a simple point-and-click interface:

- **Connect / disconnect** with one click
- **Authenticate** through the browser when your session expires
- **Switch exit nodes** from a dropdown instead of memorizing hostnames
- **See connection status** at a glance (connected, disconnected, needs auth)
- **System tray integration** — runs quietly in the background

## Platform Status

| Platform | Status | Notes |
|---|---|---|
| **Linux** | **Production-ready** | GTK-based, tested on Ubuntu 22.04+, Fedora 38+, Rocky 9/10 |
| **Windows** | Built, needs testing | Compiled and functional, not yet validated across Windows versions |
| **macOS** | Not started | Planned for a future release |

## Install

### Linux

```bash
# Clone the repo
git clone https://github.com/DEC-LLC/tMUG.git
cd tMUG

# Install dependencies (Ubuntu/Debian)
sudo apt-get install python3 python3-gi gir1.2-gtk-3.0 gir1.2-ayatanaappindicator3-0.1

# Install dependencies (Fedora/Rocky)
sudo dnf install python3 python3-gobject gtk3 libayatana-appindicator-gtk3

# Run
python3 tmug.py
```

### Windows

```
# Download the latest release from the Releases page
# Run tMUG.exe
# Tailscale must already be installed
```

### Requirements

- **Tailscale** must be installed and configured (`tailscale` CLI available in PATH)
- **Python 3.8+**
- **GTK 3** (Linux) or bundled runtime (Windows)
- **System tray support** (most Linux desktop environments, Windows taskbar)

## How it works

tMUG is a thin GUI wrapper around the `tailscale` CLI. It doesn't modify Tailscale's configuration directly — it calls `tailscale status`, `tailscale up`, `tailscale down`, and `tailscale set` the same way you would from a terminal. The difference is you do it from a tray icon instead of a command prompt.

```
┌─────────────────┐
│  System Tray     │
│  Icon + Menu     │
└────────┬────────┘
         │ calls
┌────────▼────────┐
│  tailscale CLI   │
│  (already on     │
│   your system)   │
└─────────────────┘
```

No daemon. No background service. No network traffic beyond what Tailscale itself sends. tMUG is just the button.

## Why not use the official Tailscale app?

- **Linux has no official GUI** — Tailscale provides CLI only on Linux
- **Windows app is full-featured but heavy** — tMUG is lighter if you just need connect/disconnect/status
- **tMUG is open source** — audit it, modify it, integrate it into your own tooling

## Screenshots

*Coming soon*

## Contributing

Contributions welcome — especially Windows testing and macOS port work. Please open an issue first to discuss what you'd like to change.

## License

Apache License 2.0 — see [LICENSE](LICENSE) for details.

## Author

**DEC-LLC** (Diwan Enterprise Consulting LLC)
[dec-llc.biz](https://dec-llc.biz) · [info@decllc.biz](mailto:info@decllc.biz)
