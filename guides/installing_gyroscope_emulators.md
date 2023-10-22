# Installing Gyroscope Required Services For Emulators

## Introduction:
This guide will cover how to get the remaining components installed and functioning gyro controls within Nintendo Emulators (Switch/Wii U/3DS), **Please note this will not work unless you've already upgraded your kernel to one which contains the BMI323 Kernel Driver, without this driver the gyro hardware within your device won't be recognized at all. If you have not updated to a kernel which contains this driver, please follow one of the other guides regarding Kernel upgrades first. All kernel guides included in this repo above version 6.5.2 will include the BMI323 Kernel Driver.**

Support outside emulators is a currently WIP feature which will not be covered by this guide.

### Step 1 - Download the required packages
To install required software you only need to download two pre-built packages:

```sh
wget https://github.com/NeroReflex/rog-ally-motion-evdev/releases/download/v1.0.0-znver4/rog-ally-motion-evdev-1.0.0-1-x86_64.pkg.tar.zst
sudo pacman -U  rog-ally-motion-evdev-*-x86_64.pkg.tar.zst
```

```sh
wget https://github.com/NeroReflex/rog-ally-evdevhook2/releases/download/v1.0.1-znver4/rog-ally-evdevhook2-1.0.1.r1.g3635e5a-1-x86_64.pkg.tar.zst
sudo pacman -U rog-ally-evdevhook2-*-x86_64.pkg.tar.zst
```

__NOTE:__ You should check the latest release of both software in respective pages and change the download URL accordingly:
  - [rog-ally-motion-evdev](https://github.com/NeroReflex/rog-ally-motion-evdev/releases)
  - [rog-ally-evdevhook2](https://github.com/NeroReflex/rog-ally-evdevhook2/releases)

### Step 2 - Auto-Starting Services
Once installed enabling auto-start will be required, this can be done with the following commands:

```sh
systemctl --user enable ally-motion-evdev
systemctl --user enable evdevhook2
```

After that, simply reboot using ```systemctl reboot```, they should be enabled and working on the next boot.
