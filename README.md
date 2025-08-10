# 🪟 Komorebi + YASB Configuration

Personal configuration files for:
- **Komorebi** - Tiling Window Manager for Windows
- **YASB** - Yet Another Status Bar
- **WHKD** - Windows Hotkey Daemon

Optimized for **GPD Pocket 4** with multiple display configurations.

## 🖥️ Display Configurations

This setup supports multiple usage scenarios for GPD Pocket 4:

| Case | Setup | Description | Optimal Settings | Status |
|------|-------|-------------|------------------|--------|
| **Case 1** | 📱 Laptop Only | GPD Pocket 4 standalone<br/>Small 7" display | • Minimal padding (10px)<br/>• 3-4 workspaces<br/>• Simple layouts (BSP, Stack)<br/>• Larger fonts | ⚠️ Planned |
| **Case 2** | 🔄 Tablet Mode | GPD Pocket 4 in tablet orientation<br/>Touch-optimized | • Touch-friendly spacing<br/>• Portrait layouts<br/>• Simplified navigation<br/>• Auto-hide elements | ⚠️ Planned |
| **Case 3** | 🖥️ Extended Setup | GPD Pocket 4 + 19" portable monitor<br/>Dual screen productivity | • Multi-monitor config<br/>• Extended workspace layouts<br/>• Cross-monitor movement<br/>• Different DPI handling | ⚠️ Planned |
| **Case 4** | 🏠 Docked Setup | GPD Pocket 4 + external peripherals<br/>Desktop replacement | • Full desktop experience<br/>• Multiple external displays<br/>• Optimized for productivity | 💭 Future |

### Current Configuration
The current setup is a **baseline configuration** that works across all scenarios. Specific optimizations for each case will be added as separate configuration profiles.

## 📁 Structure

```
├── komorebi/
│   ├── komorebi.json      # Main komorebi configuration
│   └── applications.json  # App-specific rules
├── yasb/
│   ├── config.yaml       # YASB configuration
│   └── styles.css        # YASB styling
├── whkdrc                # Hotkey bindings
└── .vscode/              # VS Code workspace settings
```

## 🚀 Installation

### Prerequisites
- [Komorebi](https://github.com/LGUG2Z/komorebi) - Tiling window manager
- [WHKD](https://github.com/LGUG2Z/whkd) - Hotkey daemon
- [YASB](https://github.com/denBot/yasb) - Status bar

### Setup

1. **Clone this repository:**
   ```powershell
   git clone <your-repo-url> ~/.config
   cd ~/.config
   ```

2. **Set environment variable (add to PowerShell profile):**
   ```powershell
   $Env:KOMOREBI_CONFIG_HOME = 'C:\Users\YourUsername\.config\komorebi'
   ```

3. **Start the components:**
   ```powershell
   # Start komorebi
   komorebic start
   
   # Start hotkey daemon
   whkd
   
   # Start status bar
   yasb
   ```

## ⌨️ Default Hotkeys

| Key Combination | Action |
|----------------|--------|
| `Alt + H/J/K/L` | Navigate windows (vim-style) |
| `Alt + Shift + H/J/K/L` | Move windows |
| `Alt + 1-8` | Switch workspaces |
| `Alt + Shift + 1-8` | Move window to workspace |
| `Alt + Q` | Close window |
| `Alt + T` | Toggle float |
| `Alt + Shift + R` | Retile |
| `Alt + P` | Pause/resume tiling |

## 🎨 Features

### GPD Pocket 4 Optimizations
- **Small Screen Friendly**: Optimized layouts for 7" display
- **Multi-Display Support**: Seamless external monitor integration
- **Touch-Friendly Options**: Tablet mode configurations
- **DPI Awareness**: Proper scaling across different display densities
- **Performance Tuned**: Lightweight configs for handheld performance

### Komorebi
- 7 preconfigured workspaces with different layouts
- Custom borders with "Ashes" theme
- 20px padding for containers and workspaces (adjustable per profile)
- App-specific rules
- Multi-monitor display preferences

### YASB
- Modern status bar with system information
- Customizable widgets
- Clean CSS styling
- Responsive design for different screen sizes

## 🔧 Customization

Edit the configuration files to match your preferences:
- `komorebi/komorebi.json` - Window manager settings
- `komorebi/applications.json` - App-specific behaviors
- `whkdrc` - Hotkey bindings
- `yasb/config.yaml` - Status bar configuration
- `yasb/styles.css` - Status bar styling

### Configuration Profiles (Planned)
```
komorebi/
├── komorebi.json                 # Current baseline config
├── profiles/
│   ├── laptop-only.json         # Case 1: Small screen optimized
│   ├── tablet-mode.json         # Case 2: Touch-friendly
│   ├── dual-monitor.json        # Case 3: Extended setup
│   └── docked-desktop.json      # Case 4: Full desktop
└── scripts/
    ├── switch-profile.ps1       # Profile switching utility
    └── detect-displays.ps1      # Auto-detect display setup
```

### Switching Between Profiles (Planned)
```powershell
# Manual profile switching
.\scripts\switch-profile.ps1 -Profile "laptop-only"

# Auto-detect and switch based on connected displays  
.\scripts\detect-displays.ps1 -AutoSwitch
```

## 📝 License

MIT License - Feel free to use and modify!
