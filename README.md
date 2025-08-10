# 🪟 Komorebi + YASB Configuration

Personal configuration files for:
- **Komorebi** - Tiling Window Manager for Windows
- **YASB** - Yet Another Status Bar
- **WHKD** - Windows Hotkey Daemon

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

### Komorebi
- 7 preconfigured workspaces with different layouts
- Custom borders with "Ashes" theme
- 20px padding for containers and workspaces
- App-specific rules

### YASB
- Modern status bar with system information
- Customizable widgets
- Clean CSS styling

## 🔧 Customization

Edit the configuration files to match your preferences:
- `komorebi/komorebi.json` - Window manager settings
- `komorebi/applications.json` - App-specific behaviors
- `whkdrc` - Hotkey bindings
- `yasb/config.yaml` - Status bar configuration
- `yasb/styles.css` - Status bar styling

## 📝 License

MIT License - Feel free to use and modify!
