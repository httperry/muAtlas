[← Back to Root](../README.md)

# Resources

This directory contains static assets, project iconography, and PCB renders used by the project documentation.

## Structure

```
Resources/
├── Icons/
│   └── Icon Exports/
│       ├── Icon-macOS-Default-1024@1x.png   # Light-mode icon (cyan/purple gradient)
│       └── Icon-macOS-Dark-1024@1x.png      # Dark-mode icon
└── PCB_Images/
    ├── Screenshot 2026-10-24 120110.png     # 3D / 2D board renders & layout views
    ├── Screenshot 2026-10-24 120121.png
    ├── Screenshot 2026-10-24 120139.png
    └── Screenshot 2026-10-24 120157.png
```

## Icons

The project icon is a stylized μ (mu) glyph with a cyan-to-purple gradient, rendered as a macOS-style rounded-rectangle app icon.

GitHub READMEs use the `<picture>` element to automatically serve the correct variant based on the viewer's system theme.

## PCB Renders

The `PCB_Images/` directory contains high-resolution layout and 3D preview screenshots of the completed μAtlas carrier board exported from EasyEDA Pro.
