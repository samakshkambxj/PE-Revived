# Feature 4 — Icon shapes on the A17 base

Stock A17 ships a few adaptive-icon shapes, but the ThemePicker's Icons
section only lists overlays in the
`android.theme.customization.adaptive_icon_shape` category. The A13-era
TeamFiles overlays used `..._shape_vm`, so they registered but never
showed up — and both categories could be active at once (home on one,
drawer on the other).

## What was done

- Rebuilt all 16 `TeamFiles_we_*` overlays with the stock
  `adaptive_icon_shape` category and SDK 37 metadata. No code inside,
  so apktool round-trips cleanly; signed after rebuild.
- Moved out of `system/product/overlay/` into top-level `shapes/`.
  They install as user apps at flash time (`pm install -r`, keeps the
  current selection), which registers them regardless of module mount
  timing. Pick via system Wallpaper & style > Icons, or
  `cmd overlay enable --user 0 <package>`.
- Dropped Extended Settings, Icon Shape Changer, and DT2S apps
  (broken / native in A17); their installer options are gone.
