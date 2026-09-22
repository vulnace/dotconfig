# ArchLinux Desktop Configuration for Hyprland Wayland Compositor

A complete, production-ready dotfiles setup for Hyprland with supporting tools (Waybar, Kitty, Wofi, Starship, Hyprpaper, Hyprlock, Hypridle).

---

## Repository Structure

```
.config/
├── hypr/
│   ├── hyprland.lua      # Main Hyprland config (Lua)
│   ├── hyprpaper.conf    # Wallpaper daemon
│   ├── hyprlock.conf     # Lock screen
│   └── hypridle.conf     # Idle daemon
├── waybar/
│   ├── config.jsonc      # Status bar configuration
│   └── style.css         # Status bar styling (Catppuccin Mocha)
├── kitty/
│   ├── kitty.conf        # Terminal config
│   └── mocha.conf        # Catppuccin Mocha theme
├── wofi/
│   ├── config            # App launcher config
│   └── style.css         # Launcher styling
├── starship.toml         # Cross-shell prompt
├── vlc/                  # VLC media player configs
├── xfce4/                # XFCE fallback configs
└── .gitignore            # Ignored files
```

---

## Core Components

| Component | Config File | Description |
|-----------|-------------|-------------|
| **Hyprland** | `hypr/hyprland.lua` | Dynamic tiling Wayland compositor (Lua config) |
| **Hyprpaper** | `hypr/hyprpaper.conf` | Wallpaper daemon with IPC support |
| **Hyprlock** | `hypr/hyprlock.conf` | Lock screen with blur, time, user display |
| **Hypridle** | `hypr/hypridle.conf` | Idle management (lock at 5min, suspend at 10min) |
| **Waybar** | `waybar/config.jsonc`, `waybar/style.css` | Status bar with system modules |
| **Kitty** | `kitty/kitty.conf`, `kitty/mocha.conf` | GPU-accelerated terminal with Catppuccin Mocha |
| **Wofi** | `wofi/config`, `wofi/style.css` | Application launcher (drun mode) |
| **Starship** | `starship.toml` | Cross-shell prompt with git, language versions |

---

## Complete Dependencies List

### Core Window Management (Hyprland Ecosystem)
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `hyprland` | Wayland compositor | `sudo pacman -S hyprland` |
| `hyprpaper` | Wallpaper management | `sudo pacman -S hyprpaper` |
| `hyprlock` | Lock screen | `sudo pacman -S hyprlock` |
| `hypridle` | Idle daemon | `sudo pacman -S hypridle` |
| `hyprctl` | Hyprland CLI control | Included with hyprland |
| `hyprshutdown` | Session management | Included with hyprland |
| `hyprpm` | Hyprland plugin manager | Included with hyprland |

### Bar & UI
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `waybar` | Status bar (JSONC config + CSS styling) | `sudo pacman -S waybar` |
| `wofi` | App launcher (GTK-based) | `sudo pacman -S wofi` |
| `ttf-jetbrains-mono-nerd` | Icon + programming font for Waybar/Wofi/Kitty/Hyprlock/Starship | `sudo pacman -S ttf-jetbrains-mono-nerd` |

### Terminal
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `kitty` | GPU-accelerated terminal emulator | `sudo pacman -S kitty` |
| Catppuccin Mocha theme | Color theme (built into `kitty/mocha.conf`) | Included |

### Shell & Prompt
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `starship` | Cross-shell prompt with git, nodejs, rust, go, php, python, lua, haskell, ruby, docker, aws modules | `sudo pacman -S starship` |

### Fonts
| Font | Used By | Install Command |
|------|---------|-----------------|
| **JetBrainsMono Nerd Font** | Kitty terminal, Hyprlock labels | `sudo pacman -S ttf-jetbrains-mono-nerd` |
| **JetBrainsMono Nerd Font Propo** | Waybar CSS (`font-family: JetBrainsMono Nerd Font Propo`) | Included in `ttf-jetbrains-mono-nerd` |
| Nerd Font Symbols | All UI icons (Waybar, Wofi, Starship, Hyprlock) | Included in `ttf-jetbrains-mono-nerd` |

> **Note**: After installing fonts, run `fc-cache -fv` to refresh font cache.

### System Utilities
| Package | Purpose | Used By | Install Command |
|---------|---------|---------|-----------------|
| `wireplumber` | Session manager for PipeWire | Audio management | `sudo pacman -S wireplumber` |
| `pipewire` | Audio/video processing | Audio backend | `sudo pacman -S pipewire` |
| `brightnessctl` | Screen brightness control | Hyprland media keys, Waybar | `sudo pacman -S brightnessctl` |
| `playerctl` | Media playback control | Hyprland media keys, Waybar | `sudo pacman -S playerctl` |
| `bluez` | Bluetooth stack | Waybar bluetooth module | `sudo pacman -S bluez` |
| `bluez-utils` | `bluetoothctl` CLI | Waybar bluetooth module | `sudo pacman -S bluez-utils` |
| `networkmanager` | Network management | Waybar network module | `sudo pacman -S networkmanager` |
| `nmcli` | NetworkManager CLI | Waybar network module | Included with networkmanager |
| `btop` | System monitor (preferred) | Waybar CPU click action | `sudo pacman -S btop` |
| `htop` | System monitor (fallback) | Waybar Memory click action | `sudo pacman -S htop` |
| `pavucontrol` | PulseAudio volume control | Waybar volume click action | `sudo pacman -S pavucontrol` |
| `grim` | Screenshot utility | Hyprland Print keybinds | `sudo pacman -S grim` |
| `slurp` | Region selection for grim | Hyprland Print keybinds | `sudo pacman -S slurp` |
| `wf-recorder` | Screen recording | Hyprland SUPER+R keybind | `sudo pacman -S wf-recorder` |
| `xdg-desktop-portal-hyprland` | Desktop portal for screen sharing | Hyprland permissions | `sudo pacman -S xdg-desktop-portal-hyprland` |
| `wl-clipboard` | Wayland clipboard (`wl-copy`, `wl-paste`) | Hyprland screenshot copy | `sudo pacman -S wl-clipboard` |
| `libnotify` | `notify-send` for notifications | Waybar battery alert | `sudo pacman -S libnotify` |

### Applications
| Package | Purpose | Keybinding | Install Command |
|---------|---------|------------|-----------------|
| `dolphin` | File manager (primary) | `SUPER + E` | `sudo pacman -S dolphin` |
| `chromium` | Browser (calendar link) | Waybar clock click | `sudo pacman -S chromium` |
| `code` (VS Code) | Editor | `SUPER + V` | `sudo pacman -S code` OR AUR: `visual-studio-code-bin` |

### Legacy/XFCE Fallback (Optional)
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `xfce4-panel` | Panel with whiskermenu, tasklist, cpugraph, systray, genmon, pulseaudio, clock, actions | `sudo pacman -S xfce4-panel` |
| `thunar` | File manager | `sudo pacman -S thunar` |
| `xfce4-whiskermenu-plugin` | Application menu | `sudo pacman -S xfce4-whiskermenu-plugin` |
| `xfce4-cpugraph-plugin` | CPU graph | `sudo pacman -S xfce4-cpugraph-plugin` |
| `xfce4-genmon-plugin` | Generic monitor (VPN IP) | `sudo pacman -S xfce4-genmon-plugin` |
| `xfce4-pulseaudio-plugin` | Audio control | `sudo pacman -S xfce4-pulseaudio-plugin` |

### AUR / Optional Packages
| Package | Purpose | Install Command |
|---------|---------|-----------------|
| `hyprland-qtutils` | Qt theming for Hyprland | `yay -S hyprland-qtutils` |
| `qt5ct` / `qt6ct` | Qt configuration | `sudo pacman -S qt5ct qt6ct` |
| `nwg-look` | GTK theme configurator | `yay -S nwg-look` |
| `catppuccin-gtk-theme-mocha` | GTK Catppuccin theme | `yay -S catppuccin-gtk-theme-mocha` |

---

## Hyprland Configuration Details (`hypr/hyprland.lua`)

### Monitors
- Auto-detection for primary monitor
- External monitor: HDMI-A-1 at 1920x1080@60Hz, position 0x0, scale 1

### Programs
- Terminal: `kitty`
- File Manager: `dolphin`
- Menu/Launcher: `wofi`

### Autostart
```lua
hyprpaper & waybar & hypridle
```

### Environment Variables
- `XCURSOR_SIZE=24`
- `HYPRCURSOR_SIZE=24`

### Permissions (screencopy)
- `grim` - screenshots
- `wf-recorder` - screen recording
- `xdg-desktop-portal-hyprland` - screen sharing

### Look & Feel
- **Gaps**: inner 5px, outer 7px
- **Border**: 1px, gradient active border (cyan→green, 45°), inactive gray
- **Rounding**: 10px, power 2
- **Opacity**: 1.0 (both active/inactive) - no transparency
- **Shadow**: disabled
- **Blur**: enabled, size 2, 1 pass, vibrancy 0.1696
- **Animations**: enabled with custom bezier curves and springs

### Animations
| Animation | Speed | Curve/Style |
|-----------|-------|-------------|
| global | 10 | default |
| border | 5.39 | easeOutQuint |
| windows | 4.79 | spring "easy" |
| windowsIn | 4.1 | spring "easy", popin 87% |
| windowsOut | 1.49 | linear, popin 87% |
| fadeIn | 1.73 | almostLinear |
| fadeOut | 1.46 | almostLinear |
| fade | 3.03 | quick |
| layers | 3.81 | easeOutQuint |
| layersIn | 4 | easeOutQuint, fade |
| layersOut | 1.5 | linear, fade |
| fadeLayersIn | 1.79 | almostLinear |
| fadeLayersOut | 1.39 | almostLinear |
| zoomFactor | 7 | quick |

*Workspace animations commented out for smooth switching*

### Layouts
- **Dwindle**: `preserve_split = true`
- **Master**: `new_status = "master"`
- **Scrolling**: `fullscreen_on_one_column = true`

### Input
- Keyboard: US layout
- Follow mouse: enabled (1)
- Touchpad: natural scroll enabled
- 3-finger horizontal swipe: workspace switch
- Mouse device "epic-mouse-v1": sensitivity -0.5

### Window Rules
- Suppress maximize events for all apps
- Fix XWayland drag issues (no_focus)
- Float `hyprland-run` at bottom of monitor

---

## Keybindings (Hyprland)

### Main Modifier: `SUPER` (Windows key)

| Key | Action |
|-----|--------|
| `SUPER + Q` | Open Kitty terminal |
| `SUPER + X` | Close window |
| `SUPER + M` | Shutdown menu (hyprshutdown or exit) |
| `SUPER + E` | Open Dolphin file manager |
| `SUPER + V` | Open VS Code (`/opt/VSCode-linux-x64/code`) |
| `SUPER + SPACE` | Open Wofi launcher |
| `SUPER + P` | Toggle pseudo-tile |
| `SUPER + J` | Toggle split (dwindle layout) |
| `SUPER + L` | Lock screen (hyprlock) |
| `SUPER + Arrows` | Focus windows (left/right/up/down) |
| `SUPER + 1-0` | Switch workspace (1-10) |
| `SUPER + SHIFT + 1-0` | Move window to workspace |
| `SUPER + S` | Toggle scratchpad (special:magic) |
| `SUPER + SHIFT + S` | Move window to scratchpad |
| `SUPER + Scroll` | Switch workspaces |
| `SUPER + LMB` | Drag window |
| `SUPER + RMB` | Resize window |

### Media/Audio Keys (XF86)
| Key | Action |
|-----|--------|
| `XF86AudioRaiseVolume` | Volume up 5% (max 100%) |
| `XF86AudioLowerVolume` | Volume down 5% |
| `XF86AudioMute` | Toggle mute |
| `XF86AudioMicMute` | Toggle mic mute |
| `XF86MonBrightnessUp` | Brightness up 5% |
| `XF86MonBrightnessDown` | Brightness down 5% |
| `XF86AudioNext` | Next track |
| `XF86AudioPause` | Play/Pause |
| `XF86AudioPlay` | Play/Pause |
| `XF86AudioPrev` | Previous track |

### SUPER + Function Keys (Audio)
| Key | Action |
|-----|--------|
| `SUPER + F1` | Toggle mute |
| `SUPER + F2` | Volume down 5% |
| `SUPER + F3` | Volume up 5% (max 100%) |

### Screenshots & Recording
| Key | Action |
|-----|--------|
| `Print` | Select area → save to `~/Pictures/screenshot-<timestamp>.png` + copy to clipboard |
| `SUPER + Print` | Full screen → save to `~/Pictures/screenshot-<timestamp>.png` + copy to clipboard |
| `SUPER + R` | Start/stop screen recording to `~/Videos/recording-<timestamp>.mp4` |

---

## Waybar Configuration (`waybar/config.jsonc`)

### Layout
- **Layer**: top
- **Height**: 30px
- **Margins**: top 6px, left/right 10px
- **Modules Left**: Hyprland workspaces
- **Modules Center**: Clock
- **Modules Right**: Submap, Network speed, Battery alert, Bluetooth, Network, Volume group, CPU, Memory, Battery, Power

### Modules

#### Workspaces (`hyprland/workspaces`)
- Format: icon only
- Active: highlighted, Default: dimmed

#### Battery
- Interval: 60s
- Format: `{capacity}% {icon}`
- Icons for 0-100% (discharging) and charging states

#### Battery Alert (Custom)
- Checks every 60s
- Notifies at ≤20% when discharging (once until charging)
- Uses `notify-send -u critical`

#### Bluetooth
- Format: `󰂯` (disabled), `󰂱 {device} {battery}%` (connected)
- Left-click: toggle connect/disconnect first paired device
- Right-click: scan + Wofi menu to select device
- Requires `bluetoothctl`, `AutoEnable=true` in `/etc/bluetooth/main.conf`

#### CPU
- Interval: 10s
- Format: `󰻠 {usage}%`
- Click: opens `kitty -e top` (btop)

#### Memory
- Interval: 30s
- Format: `󰘚 {percentage}%`
- Tooltip: `{used}G/{total}G used`
- Click: opens `ghostty -e htop`

#### Power Menu (Custom)
- Click: Wofi menu (Shutdown, Reboot, Logout, Hibernate, Suspend)

#### Network
- WiFi format: `{essid}`, disconnected: `󰤭`
- Left-click: toggle connect/disconnect wlan0
- Right-click: rescan + Wofi menu to connect (handles saved/open/WPA networks)

#### Network Speed
- Interval: 1s
- Format: `↓ {down} ↑ {up}`
- Min width: 110px

#### Clock
- Format: `󰥔 {day, date time}`
- Tooltip: calendar (today highlighted in cyan)
- Click: opens Google Calendar in Chromium app mode

#### Volume Group (PulseAudio + Slider)
- PulseAudio: format `{volume}% {icon}`, muted: `󰝟`
- Scroll: ±1%
- Ignored sinks: "Easy Effects Sink"
- Click: opens `pavucontrol`
- Horizontal slider (0-100%)

---

## Waybar Styling (`waybar/style.css`)

### Color Palette (Catppuccin Mocha)
```css
@define-color highlight   rgba(117, 241, 250, 1);  /* cyan */
@define-color dark-9      rgba(24, 24, 27, 1);     /* base */
@define-color dark-8      rgba(39, 39, 42, 1);     /* mantle */
@define-color dark-7      rgba(63, 63, 70, 1);     /* crust */
@define-color dark-6      rgba(82, 82, 91, 1);     /* surface0 */
@define-color dark-5      rgba(113, 113, 122, 1);  /* surface1 */
```

### Styles
- **Window**: dark-9 background, white text, 12px border-radius
- **Workspaces**: 8px font, 6px radius, active = highlight bg + black text + bold
- **Modules** (submap, battery, bluetooth, network, cpu, memory, volume, power): dark-8 bg, 10px radius, padding 1px 6px
- **Urgent workspace**: red background
- **Volume slider**: dark-7 trough, highlight fill, 6px height, 60px min-width
- **Tooltip**: dark-9 bg, 10px radius, white text
- **Network speed**: 110px min-width
- **Font**: `JetBrainsMono Nerd Font Propo`, 12px

---

## Kitty Configuration (`kitty/kitty.conf` + `kitty/mocha.conf`)

### General
- Font: `JetBrainsMono Nerd Font`, 11pt
- Auto bold/italic fonts
- Cursor: block, hide after 2s
- URL: cyan color, dotted underline
- No close confirmation
- Background opacity: 0.95

### Catppuccin Mocha Colors
| Color | Hex | Role |
|-------|-----|------|
| Foreground | `#CDD6F4` | Text |
| Background | `#1E1E2E` | Background |
| Selection FG | `#1E1E2E` | Selected text |
| Selection BG | `#F5E0DC` | Selection background |
| Cursor | `#F5E0DC` | Cursor |
| Cursor Text | `#1E1E2E` | Cursor text |
| Active Border | `#B4BEFE` | Active window border |
| Inactive Border | `#6C7086` | Inactive window border |
| Bell Border | `#F9E2AF` | Bell border |

### Terminal Colors (16-color)
- **Black**: `#45475A` / `#585B70`
- **Red**: `#F38BA8`
- **Green**: `#A6E3A1`
- **Yellow**: `#F9E2AF`
- **Blue**: `#89B4FA`
- **Magenta**: `#F5C2E7`
- **Cyan**: `#94E2D5`
- **White**: `#BAC2DE` / `#A6ADC8`

### Tab Bar
- Active: `#CBA6F7` bg, `#11111B` fg
- Inactive: `#181825` bg, `#CDD6F4` fg
- Bar background: `#11111B`

---

## Wofi Configuration (`wofi/config` + `wofi/style.css`)

### Config
- Width: 600px, Height: 350px
- Location: center
- Mode: `drun` (desktop files)
- Prompt: "Search..."
- Filter rate: 100ms
- Markup enabled, no actions
- Vertical orientation, fill alignment
- Case insensitive, images enabled (40px)
- GTK dark mode: enabled

### Styling (Catppuccin Mocha)
- **Window**: `#1E1E2E` border (5px), `#CDD6F4` bg, 15px radius
- **Input**: `#1E1E2E` bg, `#CDD6F4` text, bold, 15px radius, 10px margin
- **Inner Box**: `#1E1E2E` bg/border (10px), `#CDD6F4` text, 15px radius
- **Outer Box**: `#1E1E2E` bg, 15px radius
- **Scroll**: 15px radius, 5px margins
- **Selected Item**: `#89B4FA` (blue) bg, 15px radius
- **Entry**: transparent bg, 15px radius

---

## Starship Configuration (`starship.toml`)

### Format
```
[󰣇 ](fg:blue)\
$directory\
$git_branch\
$git_status\
$fill\
$python\
$lua\
$nodejs\
$golang\
$haskell\
$rust\
$ruby\
$package\
$aws\
$docker_context\
$jobs\
$cmd_duration\
$line_break\
$character
```

### Palette: Nord (primary), OneDark (alternative)

### Modules
| Module | Symbol | Style | Details |
|--------|--------|-------|---------|
| Directory | - | bold fg:dark_blue | Truncate to 3, `…/` symbol, repo-aware |
| Git Branch | ` ` | fg:green | `on [branch]` format |
| Git Status | - | fg:green | Shows status + ahead/behind |
| Python | ` ` | teal | pyenv + virtualenv |
| Lua | ` ` | - | - |
| Node.js | ` ` | blue | - |
| Go | ` ` | blue | - |
| Haskell | ` ` | blue | - |
| Rust | ` ` | orange | - |
| Ruby | ` ` | blue | - |
| Package | `󰏗 ` | - | - |
| AWS | ` ` | yellow | Profile + duration |
| Docker | ` ` | `#06969A` | Detects compose/Dockerfile |
| Jobs | ` ` | red | Threshold: 1 |
| Cmd Duration | - | fg:gray | Min 500ms |

### Directory Substitutions
- `Documents` → `󰈙`
- `Downloads` → ` `
- `Music` → ` `
- `Pictures` → ` `

### Nord Palette Colors
```toml
dark_blue = '#5E81AC'
blue = '#81A1C1'
teal = '#88C0D0'
red = '#BF616A'
orange = '#D08770'
green = '#A3BE8C'
yellow = '#EBCB8B'
purple = '#B48EAD'
gray = '#434C5E'
black = '#2E3440'
white = '#D8DEE9'
```

---

## Hyprpaper (`hypr/hyprpaper.conf`)

```ini
preload = /home/mario/Pictures/wallPaper/m4dara.jpg

wallpaper {
    monitor =
    path = /home/mario/Pictures/wallPaper/m4dara.jpg
}

splash = false
ipc = true
```
- Preloads wallpaper for instant switching
- Applies to all monitors (empty monitor = all)
- No splash animation
- IPC enabled for dynamic control

---

## Hyprlock (`hypr/hyprlock.conf`)

### General
- Hide cursor
- Ignore empty input

### Background
- Source: screenshot (current screen blurred)
- Blur: 3 passes, size 8
- Brightness: 0.7

### Input Field
- Size: 300x50, outline 2px
- Colors: outer `#75F1FA` (cyan), inner `#18181B` (dark), text white
- Placeholder: "Enter Password..." (italic)
- Position: center, 50px above center
- No fade on empty

### Labels
- **User**: `$USER`, 24pt, JetBrainsMono Nerd Font, position 80px below center
- **Date/Time**: `cmd[update:1000] echo "$(date '+%A, %d %B  %I:%M %p')"`, 18pt, 90% opacity, position 140px below center

---

## Hypridle (`hypr/hypridle.conf`)

### General
- Lock command: `pidof hyprlock || hyprlock`
- Before sleep: `loginctl lock-session`
- After sleep: `hyprctl dispatch dpms on`

### Listeners
| Timeout | Action |
|---------|--------|
| 300s (5 min) | `hyprlock` |
| 600s (10 min) | `systemctl suspend` |

---

## Theming Summary

| Element | Theme |
|---------|-------|
| **Color Scheme** | Catppuccin Mocha (kitty, waybar, wofi, hyprlock) |
| **Starship Palette** | Nord (primary) / OneDark (alt) |
| **Font** | JetBrains Mono Nerd Font (all UI) |
| **Border Radius** | 10-15px rounded corners throughout |
| **Blur** | Enabled in Hyprland (vibrancy 0.1696), Hyprlock (3 passes, size 8) |
| **Opacity** | Opaque windows (1.0), Waybar semi-transparent modules |

---

## Installation

### 1. Install Core Packages (Arch/pacman)
```bash
# Core Hyprland ecosystem
sudo pacman -S hyprland hyprpaper hyprlock hypridle

# Bar & UI
sudo pacman -S waybar wofi ttf-jetbrains-mono-nerd

# Terminal
sudo pacman -S kitty

# Shell
sudo pacman -S starship

# System utilities
sudo pacman -S wireplumber pipewire brightnessctl playerctl bluez bluez-utils networkmanager btop htop pavucontrol grim slurp wl-clipboard wf-recorder xdg-desktop-portal-hyprland libnotify

# Applications
sudo pacman -S dolphin chromium code
```

### 2. Enable Services
```bash
# NetworkManager
sudo systemctl enable --now NetworkManager

# Bluetooth
sudo systemctl enable --now bluetooth

# PipeWire/WirePlumber (user services)
systemctl --user enable --now pipewire wireplumber pipewire-pulse
```

### 3. Deploy Configs
```bash
# Backup existing
mv ~/.config/hypr ~/.config/hypr.bak 2>/dev/null
mv ~/.config/waybar ~/.config/waybar.bak 2>/dev/null
mv ~/.config/kitty ~/.config/kitty.bak 2>/dev/null
mv ~/.config/wofi ~/.config/wofi.bak 2>/dev/null
mv ~/.config/starship.toml ~/.config/starship.toml.bak 2>/dev/null

# Symlink (adjust path as needed)
ln -sf /path/to/this/repo/hypr ~/.config/hypr
ln -sf /path/to/this/repo/waybar ~/.config/waybar
ln -sf /path/to/this/repo/kitty ~/.config/kitty
ln -sf /path/to/this/repo/wofi ~/.config/wofi
ln -sf /path/to/this/repo/starship.toml ~/.config/starship.toml
```

### 4. Fonts
```bash
sudo pacman -S ttf-jetbrains-mono-nerd
fc-cache -fv
```

### 5. Bluetooth Auto-connect (optional but recommended)
```bash
sudo nano /etc/bluetooth/main.conf
# Uncomment/set:
# AutoEnable=true
# ReconnectAttempts=7
# ReconnectIntervals=1,2,4,8,16,32,64
sudo systemctl restart bluetooth
```

### 6. Login Manager
Ensure `hyprland.desktop` is available for your display manager (SDDM, GDM, Ly, etc.)

### 7. Add Starship to Shell
```bash
# ~/.bashrc or ~/.zshrc
eval "$(starship init bash)"  # or zsh
```

---

## Git Ignore (`.gitignore`)

Excludes:
- Browser configs: `BraveSoftware/`, `chromium/`, `Code - OSS/`
- IDE/editor: `Mousepad/`, `sublime-text/`
- System: `dconf/`, `go/`, `pulse/`, `session/`, `yay/`, `QtProject.conf`
- VirtualBox: `VirtualBox/`

---

## Customization Notes

### Wallpaper
Edit `hypr/hyprpaper.conf`:
```ini
preload = /path/to/your/wallpaper.jpg
wallpaper { monitor = ; path = /path/to/your/wallpaper.jpg }
```

### Monitor Setup
Edit `hypr/hyprland.lua` monitor section for your outputs (use `hyprctl monitors` to list).

### Keyboard Layout
Edit `hypr/hyprland.lua` input section:
```lua
kb_layout = "us"  -- change to your layout (e.g., "de", "fr", "gb")
```

### Starship Prompt
Edit `starship.toml` - change `palette = 'nord'` to `'onedark'` or customize modules.

### Waybar Modules
Add/remove modules in `waybar/config.jsonc` under `modules-left/center/right`.

### VS Code Path
Edit `hypr/hyprland.lua` line 320 if VS Code is installed elsewhere:
```lua
hl.bind(mainMod .. " + V", hl.dsp.exec_cmd("/opt/VSCode-linux-x64/code"))
```

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Waybar not showing | Check `waybar` command output, verify JSONC syntax |
| Wofi not launching | Ensure `gtk_dark=true` in config, check GTK theme |
| Audio keys not working | Verify `wpctl` works, check `wireplumber`/`pipewire` running |
| Bluetooth not connecting | Run `bluetoothctl power on`, check `AutoEnable=true` |
| Hyprlock not blurring | Ensure `hyprpaper` is running for screenshot source |
| Fonts showing boxes | Install `ttf-jetbrains-mono-nerd`, run `fc-cache -fv` |
| Starship not showing | Add `eval "$(starship init bash)"` to shell rc file |
| Screen recording fails | Check `wf-recorder` installed, permissions granted |
| Battery alert not working | Verify BAT1 path in `/sys/class/power_supply/`, check `libnotify` |

---

## Credits & References

- [Hyprland Wiki](https://wiki.hypr.land/)
- [Waybar Configuration](https://github.com/Alexays/Waybar/wiki/Configuration)
- [Catppuccin Theme](https://github.com/catppuccin/catppuccin)
- [Starship Config](https://starship.rs/config/)
- [Wofi](https://hg.sr.ht/~scoopta/wofi)
- [Kitty Terminal](https://sw.kovidgoyal.net/kitty/)
- [JetBrains Mono Nerd Font](https://www.nerdfonts.com/font-downloads)

---

*Last updated: September 22 2026*