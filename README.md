# ChimeraOS ROG Ally Tricks

Here is a community made repository of fixes, workarounds, patches, and upgrades for ChimeraOS running on Asus ROG Ally devices.

Some of the things you find in this guide may be unofficial changes to original software, such as custom kernel upgrades for ChimeraOS and modified versions of steam-patch. THESE PROJECTS ARE NOT SUPPORTED BY THE DEVELOPERS OF THOSE ORIGINAL PROJECTS.

## Guides

### [Installing ChimeraOS on your ROG Ally](https://chimeraos.org/download/)
Please see the "installation" section of the ChimeraOS website for instructions on how to install the operating system. To access the bios on an ROG ally, hold or press rapidly on the Volume Down button while you boot, press "Y" on your controller to access the advanced menu once in the bios, and use the d-pad to scroll right to the "Boot" tab and down to your USB device.

### [Repairing A and B State behavior on ROG Ally](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/repairing-b-state-behavior.md)
When installing ChimeraOS on ROG Allys there are 3 possible states of operation. In state A the QAM/Steam buttons do not function except for on the first boot, any sleep/wake cycles break it. State B is indicated by a "light switch" type behavior, where every sleep/wake cycle toggles the buttons. Then there is state C where all buttons function all the time. This guide provides a workaround for A and B state ROG Allys to force C state behavior, though, with some quirks.

### [Installing Custom 6.5.0 Kernel by @NeroReflex](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/installing_custom_6.5.0_kernel.md)
ChimeraOS, at the time of writing this, installs with an older kernel, this 6.5.0 is compiled specifically for the ROG Ally and brings noticable performance improvements.

### [Installing Custom steam-patch (by @NeroReflex) & Updating HandyGCCS](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/installing_custom_steam_patch.md)
The original version of steam-patch contains controller input fixes which conflict with the workaround for C State found [here](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/repairing-b-state-behavior.md) as well as conflicting with HandyGCCS. This guide will install a custom version which removes the controller input fixes so HandyGCCS can handle them instead.

## Related Projects

[ChimeraOS](https://github.com/ChimeraOS/chimeraos)

[Steam-Patch](https://github.com/Maclay74/steam-patch) and [NeroReflex Custom Steam-Patch](https://github.com/NeroReflex/steam-patch)

[HandyGCCS](https://github.com/ShadowBlip/HandyGCCS)

[EmuDeck](https://github.com/dragoonDorise/EmuDeck)

## Helpful Comamnds

Install DeckyLoader:
```sh
curl -L https://github.com/SteamDeckHomebrew/decky-installer/releases/latest/download/install_release.sh | sh
```