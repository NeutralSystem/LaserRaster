# LaserRaster

Free Windows/Linux tool to convert images into laser engraving G-code for Marlin-based machines.

Load an image, adjust settings, export G-code — no coding required.

## [>>> Download Latest Release <<<](../../releases/latest)

Download **GCodeRaster-Setup.exe** from the link above, run the installer, and launch LaserRaster from the Start Menu.

<img src="LaserRaster/LaserRaster.png" alt="Diagram" width="600" />

## What it does

LaserRaster takes an image (PNG, JPG, BMP, WEBP, TIFF) and converts it into raster G-code that a Marlin-compatible laser engraver can execute. The laser power varies per pixel to reproduce the image as a burn on wood, leather, or similar materials.

## How it works

1. **Load an image** — drag or browse to load your source image
2. **Position on the virtual bed** — drag the image on the bed preview or type exact X/Y offsets
3. **Adjust settings** — scale, line spacing, feed rate, laser power range, brightness, contrast, gamma
4. **Export G-code** — save a `.gcode` file ready for your machine

The app scans the image row by row (with optional serpentine/bidirectional scanning), mapping each pixel's brightness to a laser power value between your configured min and max (`S0`–`S255`). Blank areas are skipped automatically — the laser head rapids over empty space instead of slowly traversing it.

## Settings overview

| Setting | What it controls |
|---|---|
| Bed width/height | Your machine's work area (mm) |
| Scale | Image size as % of original aspect ratio |
| X/Y offset | Placement on the bed (mm) |
| Line spacing | Distance between scan lines (mm) — lower = finer detail |
| Feed rate | Laser travel speed (mm/min) |
| Min/Max power | Laser power range (S0–S255) |
| Brightness / Contrast / Gamma / Sharpness | Image adjustments before conversion |
| Invert | Swap black ↔ white |
| Serpentine | Bidirectional scanning (faster, less travel) |
| Black is hot | Whether dark pixels = more laser power |
| Cut outline | Optional rectangle cut around the engraved area |

## G-code output

- Marlin-compatible: `G0`/`G1` moves, `M3 S…` for laser power, `M5` for laser off
- Customisable header/footer templates with placeholders
- Coordinates in millimetres, absolute positioning
- Automatic blank-area optimisation (skips rows and gaps with no laser activity)

## Requirements

- Windows 10 or later (64-bit)
- A Marlin-compatible laser engraver that accepts `M3`/`M5` laser commands

## Building from source (Linux)

### Prerequisites

**Python 3.10+** and the system libraries required by PySide6 / Qt:

Ubuntu / Debian:
```bash
sudo apt install python3 python3-pip python3-venv libgl1 libegl1 libxkbcommon0 libdbus-1-3
```

Fedora:
```bash
sudo dnf install python3 python3-pip mesa-libGL mesa-libEGL libxkbcommon dbus-libs
```

Arch:
```bash
sudo pacman -S python python-pip mesa libxkbcommon dbus
```

### Download, install & run

```bash
# Download the source archive from the latest release
wget https://github.com/NeutralSystem/LaserRaster/releases/latest/download/LaserRaster-source.zip

# Extract into a package directory
mkdir LaserRaster-build && cd LaserRaster-build
unzip ../LaserRaster-source.zip -d LaserRaster

# Create a virtual environment and install dependencies
python3 -m venv .venv
source .venv/bin/activate
pip install -r LaserRaster/requirements.txt

# Run
python3 -m LaserRaster.main
```

## License

MIT, Free to use.
