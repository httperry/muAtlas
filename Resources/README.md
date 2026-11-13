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
├── PCB_Images/
│   ├── Screenshot 2026-10-24 120110.png     # 3D / 2D board renders & layout views
│   ├── Screenshot 2026-10-24 120121.png
│   ├── Screenshot 2026-10-24 120139.png
│   └── Screenshot 2026-10-24 120157.png
└── blender_renders/
    ├── 2ayzs3jo.png                         # 4K studio renders of μAtlas + LattePanda Mu
    ├── h5715ib4.png
    ├── kpsxsa5h.png
    ├── peyqp3z9.png
    ├── tr65dcwh.png
    ├── vyxb3rlo.png
    ├── wu0qwpp2.png
    └── ywwscdp3.png
```

## Icons

The project icon is a stylized μ (mu) glyph with a cyan-to-purple gradient, rendered as a macOS-style rounded-rectangle app icon.

GitHub READMEs use the `<picture>` element to automatically serve the correct variant based on the viewer's system theme.

## PCB Renders

The `PCB_Images/` directory contains high-resolution layout and 3D preview screenshots of the completed μAtlas carrier board exported from EasyEDA Pro.

## Blender Studio Renders

The `blender_renders/` directory contains 4K (3840×2160) studio renders of the μAtlas carrier board with the LattePanda Mu compute module seated in the SO-DIMM slot. These were rendered with Blender 5.3 Cycles using AgX color grading against a pure black void backdrop.

| File | Shot | Description |
|:---|:---|:---|
| `h5715ib4.png` | Shot 01 | Front Hero Image |
| `vyxb3rlo.png` | Shot 02 | SO-DIMM Macro Shot |
| `2ayzs3jo.png` | Shot 03 | A cool wallpaperable shot |
| `tr65dcwh.png` | Shot 04 | Back Hero Image |
| `kpsxsa5h.png` | Shot 05 | Back M.2 Traces and Detailed Shot |
| `ywwscdp3.png` | Shot 06 | Monolithic shot |
| `peyqp3z9.png` | Shot 07 | Dual-Tone Lighting Shot |
| `wu0qwpp2.png` | Shot 08 | Low Angle Shot |
