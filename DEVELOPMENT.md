# Configuration Profiles Development Plan

## Overview
This document outlines the development plan for different GPD Pocket 4 usage scenarios.

**Current Status**: Case 3 (Extended Setup) is fully implemented and active.

## Profile Details

### ✅ Case 3: Extended Setup (IMPLEMENTED)
**Target**: GPD Pocket 4 + 19" portable monitor (2x HD resolution)
**Status**: ✅ **Fully Configured**

**Implementation Details**:
- Multi-monitor configuration with `display_index_preferences`
- Monitor 0 (External): 6 workspaces for productivity
- Monitor 1 (GPD): 2 workspaces for focus/quick tasks
- Automatic application routing via `initial_workspace_rules`
- Development tools → External monitor
- Quick utilities → GPD monitor

**Current Configuration**:
```json
{
  "display_index_preferences": {
    "0": "8947848",           // External monitor (HSX0324)
    "1": "HSX0324-5&16867cf9&0&UID256"  // GPD built-in
  },
  "initial_workspace_rules": [
    // Development tools go to external monitor
    {"kind": "Exe", "id": "devenv.exe", "monitor_index": 0, "workspace_name": "CODE"},
    {"kind": "Exe", "id": "Code.exe", "monitor_index": 0, "workspace_name": "CODE"},
    // Quick tools go to GPD monitor  
    {"kind": "Exe", "id": "notepad.exe", "monitor_index": 1, "workspace_name": "FOCUS"}
  ]
}
```

### Case 1: Laptop Only (laptop-only.json)
**Target**: GPD Pocket 4 standalone, 7" display
**Challenges**: 
- Limited screen real estate
- High DPI display
- Touch/trackpad navigation

**Planned Optimizations**:
```json
{
  "default_workspace_padding": 10,
  "default_container_padding": 8,
  "border_width": 4,
  "monitors": [
    {
      "workspaces": [
        {"name": "I", "layout": "BSP"},
        {"name": "II", "layout": "VerticalStack"},
        {"name": "III", "layout": "Monocle"},
        {"name": "IV", "layout": "HorizontalStack"}
      ]
    }
  ]
}
```

### Case 2: Tablet Mode (tablet-mode.json)  
**Target**: GPD Pocket 4 in portrait/tablet orientation
**Challenges**:
- Portrait aspect ratio
- Touch-first interaction
- Virtual keyboard space

**Planned Optimizations**:
- Larger touch targets
- Portrait-optimized layouts
- Auto-hiding elements
- Simplified workspace switching

### Case 3: Extended Setup (dual-monitor.json)
**Target**: GPD Pocket 4 + 19" portable monitor (2x HD resolution)
**Challenges**:
- Different DPI scales
- Cross-monitor window management  
- Optimal workspace distribution

**Planned Optimizations**:
```json
{
  "cross_monitor_move_behaviour": "Insert",
  "display_index_preferences": {
    "\\\\?\\DISPLAY#...": 0,
    "\\\\?\\DISPLAY#...": 1
  },
  "monitors": [
    {
      "workspaces": [...] // Primary monitor workspaces
    },
    {
      "workspaces": [...] // Secondary monitor workspaces  
    }
  ]
}
```

### Case 4: Docked Setup (docked-desktop.json)
**Target**: Full desktop replacement with multiple peripherals
**Status**: Future consideration

## Implementation Plan

1. **Phase 1**: Create base profiles for Cases 1-3
2. **Phase 2**: Develop switching scripts
3. **Phase 3**: Auto-detection based on connected displays
4. **Phase 4**: User testing and refinement

## Scripts to Develop

### switch-profile.ps1
- Manual profile switching
- Backup current config
- Apply new profile
- Restart komorebi services

### detect-displays.ps1  
- Detect connected monitors
- Identify display configurations
- Auto-suggest/apply appropriate profile
- Integration with Windows display events
