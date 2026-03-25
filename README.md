# Desktop Zoom

Research and tooling for on-demand screen magnification on Linux, with full keyboard and mouse passthrough.

## Goal

Run a script on a Linux desktop (GNOME, KDE, etc.) that opens a live zoom window following the mouse cursor. Requirements:

- Multiple zoom levels via repeated key presses
- Full keyboard and mouse passthrough while zoomed
- Lightweight -- should not run as a heavy background process

## Research Summary

The `readme.log` file contains a detailed survey of existing tools and compositor-level solutions. Key findings:

### Recommended: Compositor-Level Zoom

| Desktop Environment | Solution | Toggle Shortcut | Scriptable |
|---|---|---|---|
| GNOME | Built-in Shell Magnifier | Super+Alt+8 | `gsettings` / D-Bus |
| KDE Plasma | KWin Zoom Effect | Meta+= / Meta+- | `qdbus` / D-Bus |
| XFCE | xfwm4 built-in zoom | Alt+scroll | xdotool key injection |
| Cinnamon | Cinnamon Magnifier | configurable | `dconf` |

Compositor zoom is the best approach because it provides full passthrough at zero CPU cost when inactive. A simple shell script calling `gsettings` or `qdbus` gives toggle, zoom level, and mouse-follow.

### Standalone Viewer Tools

Tools like `magnus`, `xzoom`, `KMag`, and `wooz` open a separate magnified window. These are generally less practical because they lack click passthrough, many are X11-only, and the separate window can be disorienting.

## Status

Research phase. See `readme.log` for the full compatibility matrix and detailed notes on each tool.
