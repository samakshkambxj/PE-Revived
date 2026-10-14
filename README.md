# PE-Revived

**Pixel Launcher Extended, revived for Android 17.** A Magisk/KernelSU module by [**samakshkambxj**](https://github.com/samakshkambxj), continuing the work of [TeamFiles](https://github.com/TeamFiles) (upstream `saitamasahil/Pixel-Launcher-Extended` ended at v1.7 on Android 13). Original work by TeamFiles, GPL-3.0 (see `LICENSE`).

![Header Image](https://raw.githubusercontent.com/saitamasahil/Pixel-Launcher-Extended/main/banner2.jpg)

## Features

| Feature | Status on Android 17 |
|---|---|
| Extra grid sizes (5x7, 5x8, 6x5–6x9) | ✅ Working |
| Extra themed icons | ✅ Shipped, verifying |
| Double tap to sleep | ✅ Native in Android 17, no module needed |
| Extra icon shapes (16 overlays) | ✅ Ship with module, pick from system Icons settings |
| Material You At a Glance greetings | 🚧 Styles pending |
| Pixel Launcher Mods app | 🚧 Dead upstream, replacement queued |
| Hidden launcher flags + dev options | ✅ Partial (more coming) |
| New Wallpaper picker, Themes stub, Recents provider | ✅ Working |

### Preview
<div align="center">
    <img src="screenshots/preview1.png">
</div>
<div align="center">
    <img src="screenshots/preview2.png">
</div>
<div align="center">
    <img src="screenshots/preview3.png">
</div>
<div align="center">
    <img src="screenshots/preview4.png">
</div>
<div align="center">
    <img src="screenshots/preview5.png">
</div>
<div align="center">
    <img src="screenshots/preview6.png">
</div>

## Compatibility
- **Android 17 (SDK 37) only.** Older Android is refused at install time.
- AOSP-based custom ROMs and Pixel stock ROMs with working GApps.
- Root via [Magisk](https://github.com/topjohnwu/Magisk/releases/latest) (stable) or [KernelSU](https://github.com/tiann/KernelSU) / KSU Next.
- No LSPosed needed: double-tap-to-sleep is native in Android 17.
- Proper GApps (Google app, Play Services, System Intelligence) for At a Glance/weather; without them use the [At a Glance Enhancer](#at-a-glance-enhancer) add-on.

**Disclaimer:** not responsible for anything that happens to your device. Keep a backup.

## Installation
1. Keep only the default launcher; remove other third-party launchers.
2. Download a zip from [Releases](https://github.com/samakshkambxj/PE-Revived/releases) (built automatically on every version tag).
3. Flash in Magisk / KernelSU and answer the volume-key prompts (Up = switch, Down = confirm). If your keys don't register, the installer aborts — use the Manual or Customize variant instead.
4. Reboot. Set **Pixel Launcher Extended** as Home in Settings > Apps > Default apps.
5. KernelSU users: in the manager's **App Profiles**, make sure **Unmount modules is OFF** for Pixel Launcher (and the wallpaper app), or the module's files stay invisible to the launcher. Grant root when companion apps ask.

## Variants
- **Offline Installer** (50+ MB): everything inside, no internet needed while flashing, volume-key choices.
- **Online Installer** (<5 MB): downloads only what you pick, needs internet while flashing.
- **Customize Installer**: you pre-pick the options when building the zip (no volume keys at flash time). Good for broken keys.
- **Manual Installer** (50+ MB): like offline, but options come from editing `config.txt` in the zip (see `manual_installer_instructions.md`).

During flashing you choose: At a Glance greetings styles, Launcher Mods app, extra icon shapes.

## Double Tap to Sleep
Built into Android 17 — enable the system's double-tap option and it works on the home screen with no module or LSPosed needed.

## Activating Developer Options in Launcher
- Tap the phone's build number 7 times; launcher dev options unlock alongside the system ones.

## Uninstallation / Updating
- Uninstall from the root manager. To change options or update, flash the newer zip over the old one.

## Add-ons

### At A Glance Enhancer
Enhances At a Glance (doorbell, timer, fitness, torch suggestions…) and fixes weather/select issues on thin GApps. By [Kingsmanz](https://github.com/Kingsman44). Unverified on Android 17 — report results.
- [Download](https://www.pling.com/p/1938895/), flash, reboot.

## Download Links
- [GitHub Releases](https://github.com/samakshkambxj/PE-Revived/releases) (recommended, CI-built)
- Mirrors (upstream v1.7, Android 13 only): [Mirror 1](https://www.pling.com/p/1952604) · [Mirror 2](https://store.kde.org/p/1952604) · [Mirror 3](https://www.opendesktop.org/p/1952604)

## Building from source
```sh
git clone https://github.com/samakshkambxj/PE-Revived
cd PE-Revived
chmod +x builder_dependencies.sh && ./builder_dependencies.sh
```
Then type **PLE** and pick a variant (offline / online / customize / manual). Local porting notes live under `Modifications/`.

## Troubleshooting
- **Installer picks Yes everywhere / keys ignored:** volume detection failed; it now aborts instead — use Manual or Customize.
- **Flashed but nothing changed:** root manager may hide module files from apps (KernelSU App Profiles → disable "Unmount modules" for the launcher), then reboot.
- **Launcher crashes at boot after flashing:** grab `adb logcat -b crash -d` and report it with your ROM + variant.
- **Weather/Select in recents broken:** update Google app, Play Services, System Intelligence, WebView from Play Store; try the At a Glance Enhancer.
- **Material You stuck:** `su -c settings delete secure theme_customization_overlay_packages` (per-boot on some ROMs).
- **Mods app stuck at loading:** force-stop and relaunch it.

## Donation Links
Upstream asks, kept as-is: [Paypal](https://www.paypal.com/paypalme/sahilsaitama96), UPI: `sahilmanchanda1996@okaxis`.

## Credits/Thanks
Google · LiArch55 · saitamasahil · iamlooper · KieronQuinn · uragiristereo · Monet Icons Team · siavash79 · Kingsman44 · anarchist22 · WaifuPX-DG · LawnchairLauncher · RadekBledowski · PalmDevs · agam778 · atharvap8 · jaaat4u · selfmusing · Sameera · naokoshoto · Ryuk · micky387 — and TeamFiles for the original. PE-Revived continuation by [samakshkambxj](https://github.com/samakshkambxj).

## Contact us
[![TeamFiles Telegram](https://img.shields.io/badge/Telegram-TeamFiles-%2326A5E4?logo=Telegram)](https://telegram.me/filesfederation)
[![Modules Repository](https://img.shields.io/badge/Telegram-Modules%20Repository-%2326A5E4?logo=Telegram)](https://telegram.me/modulesrepo)
[![Support Group](https://img.shields.io/badge/Telegram-Support%20Group-%2326A5E4?logo=Telegram)](https://telegram.me/fileschat)
