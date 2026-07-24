# Dell Vostro 15 GRUB2 Theme

This repository contains a GRUB2 theme installer for a Dell Vostro 15 system with an Intel Core i7 11th Gen CPU style theme.

## Overview

The installer script copies the bundled `Intel` theme into the system GRUB themes directory, updates `/etc/default/grub` to use the theme, and regenerates the GRUB configuration.

## Files

- `install.sh` – installs and activates the GRUB2 theme
- `Intel/` – theme assets, including `theme.txt`, background graphics, icons, and font resources
- `LICENSE` – project license

## Requirements

- Linux system with GRUB2 installed
- Root privileges
- A supported GRUB configuration tool available on the system:
  - `update-grub`
  - `grub-mkconfig`
  - `grub2-mkconfig`

## Installation

Run the script as root:

```bash
sudo ./install.sh
```

If the script is not already running with root privileges, it will prompt for the root password and retry with `sudo`.

## What the script does

1. Creates the GRUB themes directory if it does not exist.
2. Removes any previous `Intel` theme installation and reinstalls the bundled assets.
3. Back up `/etc/default/grub` to `/etc/default/grub.bak`.
4. Adds the following GRUB settings:
   - `GRUB_THEME="/usr/share/grub/themes/Intel/theme.txt"`
   - `GRUB_TIMEOUT=8`
   - `GRUB_SAVEDEFAULT=true`
   - `GRUB_TERMINAL_OUTPUT="gfxterm"`
   - `GRUB_GFXMODE=1920x1080`
5. Regenerates the GRUB configuration using the available package tool.

## Notes

- The theme is configured for a `1920x1080` display mode.
- The installer is targeted toward systems using the GRUB2 theme directory structure under `/usr/share/grub/themes`.
- After installation, reboot the system to see the new GRUB theme.

## License

This project is distributed under the terms of the included license file.
