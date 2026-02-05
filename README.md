# 🌌 nandtm-dots | CachyOS + Caelestia Rice

This repository contains my personal configuration for a CachyOS-based system using the Hyprland/Caelestia ecosystem. It is designed to be **"Update-Proof"** by isolating my customizations from system-level updates using symlinks and Systemd bind mounts.

## 🏗️ Architecture

Unlike standard dotfile setups, this repo handles both local user configs and system-wide assets:

* **`apps/`**: Direct configurations for applications like Ghostty, Zed, and VS Code.
* **`source-configs/`**: The core logic for Hyprland, Fish, and Starship, extracted from Caelestia defaults.
* **`caelestia-assets/`**: UI assets and Quickshell components that are mirrored to the system via a bind mount.

## 🛡️ The "Fortress" Strategy

To prevent system updates (`pacman -Syu`) from overwriting custom assets, this rice utilizes a **Systemd Mount Unit**. 

Instead of editing files directly in `/etc/xdg/quickshell/caelestia`, the system is instructed to "look" at the `caelestia-assets/` folder inside this repository. This ensures that:
1. All changes are tracked via Git.
2. Updates to the system package don't wipe my changes.
3. No risky `fstab` edits were required on the Btrfs filesystem.

## 🚀 Installation & Sync

### 1. Requirements
- **CachyOS** with the Caelestia desktop.
- **Git**

### 2. Linking standard configs
```bash
# Example for Hyprland
ln -s ~/nandtm-dots/source-configs/hypr ~/.config/hypr
