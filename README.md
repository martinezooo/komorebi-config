# 🪟 Komorebi + YASB Configuration

Personal configuration files for:
- **Komorebi** - Tiling Window Manager for Windows
- **YASB** - Yet Another Status Bar
- **WHKD** - Windows Hotkey Daemon

Optimized for **GPD Pocket 4** with multiple display configurations.

## 🖥️ Display Configurations

This setup supports multiple usage scenarios for GPD Pocket 4:

| Case | Setup | Description | Status | Configuration |
|------|-------|-------------|--------|---------------|
| **Case 1** | 📱 Laptop Only | GPD Pocket 4 standalone<br/>Small 7" display | ⚠️ Planned | Minimal padding, 3-4 workspaces |
| **Case 2** | 🔄 Tablet Mode | GPD Pocket 4 in tablet orientation<br/>Touch-optimized | ⚠️ Planned | Portrait layouts, touch-friendly |
| **Case 3** | 🎮 Gaming Setup | GPD Pocket 4 + Arzopa Z1FC 16.1" 144Hz Gaming Monitor<br/>Dual screen productivity with FreeSync | ✅ **Active** | Multi-monitor rules configured |
| **Case 4** | 🏠 Docked Setup | GPD Pocket 4 + external peripherals<br/>Desktop replacement | 💭 Future | Full desktop experience |

### Current Configuration (Case 3)
The active configuration is optimized for **Case 3**: GPD Pocket 4 + external monitor setup.

**Monitor Assignment:**
- **Monitor 0** (Arzopa Z1FC Gaming Monitor 16.1" 144Hz): Primary productivity monitor with 6 workspaces
  - *144Hz FreeSync Premium for smooth window transitions*
  - `CODE` - Development tools (Visual Studio, VS Code)
  - `WEB` - Web browsers (Firefox, Chrome)  
  - `TERM` - Terminals and command line tools
  - `DOCS` - Documentation and reading
  - `TOOLS` - Utility applications
  - `MEDIA` - Media and entertainment
- **Monitor 1** (GPD Pocket 4 built-in 7"): Secondary monitor with 5 workspaces
  - *Note: Shows as "UNKNOWN" device - this is normal for internal eDP displays*
  - `FOCUS` - Single-window focus mode (Notepad, small tools)
  - `QUICK` - Quick access apps (Calculator, temp windows)
  - `NEW-1`, `NEW-2`, `NEW-3` - Additional workspaces for new applications

**Automatic Window Placement:**
- Visual Studio/VS Code → External monitor `CODE` workspace
- Firefox/Chrome → External monitor `WEB` workspace
- Windows Terminal/PowerShell → External monitor `TERM` workspace
- Notepad → GPD monitor `FOCUS` workspace
- Calculator → GPD monitor `QUICK` workspace

**Handling New/Undefined Applications:**
Since komorebi doesn't support a global default monitor, new applications typically open on Monitor 0 (external). To use the GPD monitor for focused work:

1. **Move to GPD monitor**: `Alt+Shift+H` (moves current window to left monitor)
2. **Switch to GPD workspaces**: 
   - `Alt+7` for FOCUS workspace (single-window mode)
   - `Alt+8` for QUICK workspace (calculator-style apps)
   - Additional workspaces: NEW-1, NEW-2, NEW-3 (accessible via komorebic commands)
3. **All GPD workspaces use BSP layout** for distraction-free single-window focus

**Enhanced Case 3 Features:**
- 5 workspaces available on GPD monitor (FOCUS, QUICK, NEW-1, NEW-2, NEW-3)
- BSP layout on all GPD workspaces prevents window splitting
- Use `setup-enhanced-case3.ps1` script to configure additional workspaces

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
- `komorebi/komorebi.json` - Window manager settings with monitor-specific rules
- `komorebi/applications.json` - App-specific behaviors and float rules
- `whkdrc` - Hotkey bindings
- `yasb/config.yaml` - Status bar configuration
- `yasb/styles.css` - Status bar styling

### Adding New Applications
To add automatic workspace assignment for new applications:

1. Find the executable name: `Get-Process | Where-Object {$_.ProcessName -like "*appname*"}`
2. Add to `komorebi.json` in the `initial_workspace_rules` section:
```json
{
  "kind": "Exe",
  "id": "your-app.exe",
  "matching_strategy": "Legacy", 
  "monitor_index": 0,
  "workspace_name": "DESIRED_WORKSPACE"
}
```

### Monitor Configuration
- Monitor indexes are set via `display_index_preferences` using monitor serial numbers
- Current setup: Monitor 0 (external), Monitor 1 (GPD built-in)
- Change `monitor_index` in workspace rules to assign apps to different monitors

## 📝 License

MIT License - Feel free to use and modify!
