# Feature 1 — Extra grids on the A17 base (DONE, verified on-device)

Stock A17 `NexusLauncherRelease` uses spec files, and its Layout picker
lists **one entry per grid-option** (GridSize rows inside one option are
auto-fit, never user-visible). So new sizes need their own grid-option
each — no smali change needed.

## What this adds (A13 parity, verified 2026-10-14)

- small_5x7 (`Small 5×7`), small_5x8 (`Small 5×8`)
- small_6x5 … small_6x9 (`Small 6×5` … `Small 6×9`)
- 6-wide entries reuse the 5-col supporting specs (workspace/allapps/
  folder/hotseat) with 6-wide counts — verified visually fine on-device
- stock keeps: Small (auto 5x5/5x6), Medium (4x4/4x5/4x6), Large, XL

## Files

- `device_profiles_add.xml` — two grid-options cloned from the `small`
  entry (unique names/titles, own single-size `gridSizeSpecsId`); insert
  after the phone `small` option in `res/xml/device_profiles.xml`
- `spec_grid_5x7.xml`, `spec_grid_5x8.xml` — new single-GridSize specs
  under `res/xml/`
- `default_workspace_5x7.xml`, `default_workspace_5x8.xml` — new files
  under `res/xml/` (hotseat-only copies of the stock 5x6 layout)
- `strings_add.xml` — `small_5x7_grid` / `small_5x8_grid` titles, merge
  into `res/values/strings.xml`
- `attrs-fix.xml` — 5 attr definitions apktool 2.11.1 drops on decode
  (`state_dragged`, `matchTextInsetWithQuery`, `alignWithWorkspaceRow`,
  `minDeviceWidthDp`, `allAppsColumns`); merge into
  `res/values/attrs.xml` before rebuild or aapt2 link fails

## Rebuild (verified 2026-10-14, apktool 2.11.1)

> Dex warning: apktool's smali writer emits zero-filled dex headers on
> some machines (deterministic; check with
> `python3 -c "import zipfile;print(zipfile.ZipFile('x.apk').read('classes.dex')[:8])"` —
> must be `b'dex\n039\x00'`). If bad, rebuild resources with apktool
> then **swap in the stock classes*.dex** (resource-only mods don't
> need dex changes; public.xml keeps existing IDs stable so stock dex
> stays consistent) and sign after the swap.

1. `apktool d -f -o dec NexusLauncherRelease.apk`
2. copy the files below into `dec/res/xml/`, merge `strings_add.xml`
   entries into `dec/res/values/strings.xml`, merge `attrs-fix.xml`
   entries into `dec/res/values/attrs.xml`
3. `apktool b dec -o rebuilt.apk`, validate dex magic, swap stock dex
   if bad, sign
4. on-device: `content query --uri
   content://com.google.android.apps.nexuslauncher.grid_control/list_options`
   must show the new entries; after flashing, **reboot** (KernelSU
   mounts only reach apps in namespaces created post-mount) and clear
   stale oat (`/data/dalvik-cache/arm64/*NexusLauncherRelease*`)

## Not yet (Phase B)

6-column phone family (6x5..6x9 from the A13 mod) needs a new
`grid-option` plus a full `spec_handheld_*_6_col` family, 6-col styles,
`grid_icon_6_col` drawable and layouts — listed here so it isn't lost.
