# ArchLinux desktop configuration for Hyprland Wayland compositor with supporting tools.

## Core Components

| Component | Config File | Description |
|-----------|-------------|-------------|
| **Hyprland** | `hypr/hyprland.lua` | Dynamic tiling Wayland compositor (Lua config) |
| **Hyprpaper** | `hypr/hyprpaper.conf` | Wallpaper daemon |
| **Waybar** | `waybar/config.jsonc`, `waybar/style.css` | Status bar with system modules |
| **Kitty** | `kitty/kitty.conf`, `kitty/mocha.conf` | GPU-accelerated terminal with Catppuccin Mocha theme |
| **Wofi** | `wofi/config`, `wofi/style.css` | Application launcher (drun mode) |
| **Starship** | `hypr/starship.toml` | Cross-shell prompt with git, language versions |

## Key Packages & Dependencies

### Window Management
- `hyprland` - Wayland compositor
- `hyprpaper` - Wallpaper management
- `hyprctl` - Hyprland CLI control
- `hyprshutdown` - Session management

### Bar & UI
- `waybar` - Status bar (JSONC config + CSS styling)
- `wofi` - App launcher (GTK-based)
- `ttf-jetbrains-mono-nerd` - Icon font for Waybar/Wofi

### Terminal
- `kitty` - Terminal emulator
- `catppuccin-mocha` - Color theme (included in `kitty/mocha.conf`)

### Shell & Prompt
- `starship` - Prompt with git, nodejs, rust, go, php modules

### System Utilities
- `wireplumber` / `pipewire` - Audio (`wpctl` for volume)
- `brightnessctl` - Screen brightness
- `playerctl` - Media playback control
- `bluez` / `bluetoothctl` - Bluetooth management
- `networkmanager` / `nmcli` - WiFi/network
- `btop` / `htop` - System monitoring
- `pavucontrol` - PulseAudio volume control
- `grim` - Screenshots
- `xdg-desktop-portal-hyprland` - Desktop portal
- `hyprpm` - Hyprland plugin manager

### Applications
- `dolphin` - File manager (primary in Hyprland)
- `chromium` - Browser (calendar link)

### Legacy/XFCE (fallback)
- `xfce4-panel` - Panel with whiskermenu, tasklist, cpugraph, systray, genmon (VPN IP), pulseaudio, clock, actions
- `thunar` - File manager

## Keybindings (Hyprland)

| Key | Action |
|-----|--------|
| `SUPER + Q` | Open Kitty terminal |
| `SUPER + X` | Close window |
| `SUPER + M` | Shutdown menu |
| `SUPER + E` | Open Dolphin |
| `SUPER + V` | Toggle float |
| `SUPER + SPACE` | Open Wofi launcher |
| `SUPER + P` | Toggle pseudo-tile |
| `SUPER + J` | Toggle split (dwindle) |
| `SUPER + L` | Suspend |
| `SUPER + Arrows` | Focus windows |
| `SUPER + 1-0` | Switch workspace |
| `SUPER + SHIFT + 1-0` | Move window to workspace |
| `SUPER + S` | Toggle scratchpad |
| `SUPER + F1/F2/F3` | Mute/Vol Down/Vol Up |
| `XF86Audio*` | Volume/Brightness/Media keys |

## Autostart (Hyprland)
- `hyprpaper` - Wallpaper
- `waybar` - Status bar

## Theming
- **Color Scheme**: Catppuccin Mocha (kitty, waybar, wofi, starship)
- **Font**: JetBrains Mono Nerd Font
- **Border Radius**: 10-15px rounded corners throughout
- **Blur**: Enabled in Hyprland with vibrancy

## Installation Notes
1. Install all packages listed above via your package manager
2. Symlink configs to `~/.config/`
3. Install Nerd Font: `sudo pacman -S ttf-jetbrains-mono-nerd` (Arch)
4. Ensure `hyprland.desktop` or equivalent is available for login manager

## Git Ignore
Excludes browser configs, IDE settings, VM configs, and session data (see `.gitignore`).