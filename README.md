# ChimeraOS ROG Ally Tricks

Here is a community made repository of fixes, workarounds, patches, and upgrades for ChimeraOS running on Asus ROG Ally devices.

Some of the things you find in this guide may be unofficial changes to original software, such as custom kernel upgrades for ChimeraOS and modified versions of steam-patch. THESE PROJECTS ARE NOT SUPPORTED BY THE DEVELOPERS OF THOSE ORIGINAL PROJECTS.

### Legend
[Stable]  - This process has been repeated numerous times with the same expected result
[Dev]     - This process has been tested by a few developers and is stable enough for use, subject to change.
[Testing] - This process is still undergoing testing
## Guides

### [Stable] [Installing ChimeraOS on your ROG Ally](https://chimeraos.org/download/)
Please see the "installation" section of the ChimeraOS website for instructions on how to install the operating system. To access the bios on an ROG ally, hold or press rapidly on the Volume Down button while you boot, press "Y" on your controller to access the advanced menu once in the bios, and use the d-pad to scroll right to the "Boot" tab and down to your USB device.

### [Stable] [Repairing A and B State behavior on ROG Ally](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/repairing-b-state-behavior.md)
When installing ChimeraOS on ROG Allys there are 3 possible states of operation. In state A the QAM/Steam buttons do not function except for on the first boot, any sleep/wake cycles break it. State B is indicated by a "light switch" type behavior, where every sleep/wake cycle toggles the buttons. Then there is state C where all buttons function all the time. This guide provides a workaround for A and B state ROG Allys to force C state behavior, though, with some quirks.

### [Stable] [Installing Custom 6.5.2 Kernel w/ Gyro Support](TODO: LINK)
PLEASE NOTE GYRO IS ONLY WORKING WITHIN NINTENDO EMULATORS AT THE TIME OF WRITING THIS (Oct. 9th 2023)
This guide will show you how to install the 6.5.2 ROG Ally specific kernel with gyro support.

### [Dev] [Installing Custom 6.6-rc4 Kernel w/ Gyro Support](TODO: LINK)
PLEASE NOTE GYRO IS ONLY WORKING WITHIN NINTENDO EMULATORS AT THE TIME OF WRITING THIS (Oct. 9th 2023)
This guide will show you how to install the 6.6-rc4 ROG Ally specific kernel with gyro support.

### [Stable] [Installing Custom 6.5.0 Kernel by @NeroReflex](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_custom_6.5.0_kernel.md)
ChimeraOS, at the time of writing this, installs with an older kernel, this 6.5.0 is compiled specifically for the ROG Ally and brings noticable performance improvements.
EDIT: THIS IS NO LONGER TRUE, CHIMERA HAS UPDATED TO THE 6.5.3 KERNEL BY DEFAULT - SEE OTHER GUIDES

### [Stable] [Installing Custom steam-patch (by @NeroReflex) & Updating HandyGCCS](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_custom_steam_patch.md)
The original version of steam-patch contains controller input fixes which conflict with the workaround for C State found [here](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/repairing-b-state-behavior.md) as well as conflicting with HandyGCCS. This guide will install a custom version which removes the controller input fixes so HandyGCCS can handle them instead.

### [Stable] [Setting Up Secure SSH For Easy Access](TODO: LINK)
ChimeraOS by default comes without an SSH Server setup, this is intentional, as all ChimeraOS installations contain the same default root password. This guide will show you how to change that password and setup SSH so you can run commands from another PC. This can be helpful with sending commands to your device, even when its in gamemode!

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

## FAQ
### Q - Do I have to downgrade my Kernel for gyro controls?
A - Things like gyro support are being worked on, and at the time of writing this, 6.5.2 is the most stable, go-to version which still supports gyro. The Kernels listed in this guide are all custom made specifically for the ROG Ally. At the time of writing this there is also a 6.6-rc4 kernel which also allows gyro. PLEASE NOTE: GYRO CONTROLS ONLY WORK ON EMULATED TITLES AT THE MOMENT

### Q - How do I enable the rear paddle-buttons on the ROG Ally?
A - At this time we do not have control over mapping these two buttons, it is on the list of things to get done but currently nobody is working on it to my knowledge. If you've got a little experience in C, give it a shot!

### Q - What is "A", "B" and "C" state?
A - These are terms used to describe the sleep/wake functionality of a device.
        A State - All buttons work on boot, QAM and Steam buttons break after a sleep/wake cycle
        B State - Same as before, but the QAM and Steam buttons work every other sleep/wake cycle, acting like a light switch, on and off.
        C State - All buttons work all the time