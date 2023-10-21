# Installing Gyroscope required services for emulators

## Introduction:
This will install required software to allow the bmi323 IMU to be used in Nintendo emulators (Switch/Wii U/3DS).

Support outside emulators is a currently WIP feature which will not be covered by this guide.

## Installation:
To install required software you only need to download pre-built packages:

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

## Auto-Starting Services:
Once installed enabling auto-start will be required:

```sh
systemctl --user enable ally-motion-evdev
systemctl --user enable evdevhook2
```
