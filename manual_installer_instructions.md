# How To Use & Flash Manual Installer

- After making/downloading manual installer zip keep it in your phone's internal storage or sdcard.
- [Download MT Manager](https://m.apkpure.com/mt-manager/bin.mt.plus) & install it.
> It is recommended to use MT Manager only. You can use other file managers or zip utilities too but with MT Manager, you don't need to unpack zip file to edit it.
- Open the zip file using MT Manager & Click **config.txt** file to open it in text editor.
- In the text editor config.txt file will look like this:
```sh
1. LAUNCHER=
2. DT2S=
3. Pixel_Launcher_Mods_App=
4. Icon_Shape_Changer_App=
5. # Don't modify anything after this
```
- In lines 1-4 you can see variables with the name of **LAUNCHER**, **DT2S**, **Pixel_Launcher_Mods_App** & **Icon_Shape_Changer_App**. We need to add some values of these variables in order to modify the installer & get desired modifications in PLE. The following are the instructions for editing config.txt.

### Editing config.txt

#### Line 1: LAUNCHER Variable
Set this variable to `1` to keep glance greetings with the Extended Settings app, or `0` for the stock At A Glance without extras.
```sh
1. LAUNCHER=1
```

#### Line 2: DT2S Variable
DT2S Means - Double Tap To Sleep Feature. It requires LSPosed Installed in your rom. Without LSPosed it won't work. Read Documentation on GitHub to know more about activating it. Set this variable to 1 to enable it, or 0 to ignore it. Suppose you don't wanna enable DT2S feature in your rom then `the value of variable will be 0`. So, we will edit config.txt like this:
```sh
2. DT2S=0
```

#### Line 3: Pixel_Launcher_Mods_App Variable
It's an app made by Developer [KieronQuinn](https://github.com/KieronQuinn). You will be able to apply Icon Packs using it. It will also enable some more functionality to pixel launcher. Set this variable to 1 to install it, or 0 to ignore it. Suppose you want to install this app in your rom then `the value of variable will be 1`. So, we will edit config.txt like this:
```sh
3. Pixel_Launcher_Mods_App=1
```
#### Line 4: Icon_Shape_Changer_App Variable
This app can change shape of the icons in PLE. Set this variable to 1 to install it, or 0 to ignore it. Suppose you want to install this app in your rom then `the value of variable will be 1`. So, we will edit config.txt like this:
```sh
4. Icon_Shape_Changer_App=1
```

After editing all variables, config.txt will look like this:
```sh
1. LAUNCHER=1
2. DT2S=0
3. Pixel_Launcher_Mods_App=1
4. Icon_Shape_Changer_App=1
5. # Don't modify anything after this
```
Save it, go back. MT Manager will ask you to update the zip. Click OK & flash the zip in magisk.
> Note: You can edit config.txt file again to choose different modifications & installation options by editing variables and flash it again in magisk.
