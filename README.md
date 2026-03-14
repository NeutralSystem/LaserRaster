# LaserRaster
Free Windows tool to convert images into laser engraving G-code for Marlin-based machines
# GCode Raster

Python desktop app to convert images into Marlin-compatible laser raster G-code with variable power.

## Features (initial build)

- Supports image loading: PNG, JPG/JPEG, BMP, WEBP, TIFF
- Virtual bed grid preview with drag-and-place image positioning
- Center button to place the image in the middle of the bed
- Configurable bed size for different machines/printers
- Live processed preview while adjusting settings
- Scale control (%) while preserving original image aspect ratio
- Raster controls:
  - bed width/height (mm)
  - scale (%)
  - X/Y placement offsets (mm)
  - line spacing (mm)
  - feed rate (mm/min)
  - min/max power (S0..S255)
  - brightness, contrast, gamma, sharpness
  - inversion toggle
  - serpentine scanning toggle
  - black-to-power mapping toggle
- Marlin output with `M3 S...` power commands and `M5` laser-off safety lines
- Customizable G-code header and footer templates directly in the UI
- One-click restore button for default G-code header/footer templates
- Optional post-engrave square-cut outline at full laser power with configurable pass count
- Separate cutout-only export (`*_cutout.gcode`) using the same square-cut pass settings
- Automatic settings persistence between sessions (including custom templates)
- G-code export (`.gcode`, `.nc`, `.txt`)
