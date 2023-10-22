# ChimeraOS ROG Ally Tricks

Here is a community made repository of fixes, workarounds, patches, and upgrades for ChimeraOS running on Asus ROG Ally devices.

Some of the things you find in this guide may be unofficial changes to original software, such as custom kernel upgrades for ChimeraOS and modified versions of steam-patch. THESE PROJECTS ARE NOT SUPPORTED BY THE DEVELOPERS OF THOSE ORIGINAL PROJECTS.

### Legend
[Stable]  - This process is commonly used by ROG Ally users and produces the expected result

[Dev]     - This process has been tested by a few developers and is stable enough for testing/use

[Testing] - This process is still undergoing testing, beware these may not work
**these guides are either entirely untested or only tested on a select few devices, these guides may contain incomplete information, follow them at your own risk and please do not open issue requests for them**

## Guides

### [Stable] [Installing ChimeraOS on your ROG Ally](https://chimeraos.org/download/)
Please see the "installation" section of the ChimeraOS website for instructions on how to install the operating system. To access the bios on an ROG ally, hold or press rapidly on the Volume Down button while you boot, press "Y" on your controller to access the advanced menu once in the bios, and use the d-pad to scroll right to the "Boot" tab and down to your USB device.

### [Stable] [Repairing A and B State behavior on ROG Ally](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/repairing-b-state-behavior.md)
When installing ChimeraOS on ROG Allys there are 3 possible states of operation. In state A the QAM/Steam buttons do not function except for on the first boot, any sleep/wake cycles break it. State B is indicated by a "light switch" type behavior, where every sleep/wake cycle toggles the buttons. Then there is state C where all buttons function all the time. This guide provides a workaround for A and B state ROG Allys to force C state behavior, though, with some quirks.

### [Stable] [Installing Gyroscope In Emulators](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_gyroscope_emulators.md)
This guide will show you how to install the remaining required components to get gyro controls working within Nintedo Emulators. Please note that support outside of Nintendo Emulators is a Work in Progress.

### [Stable] [Installing Custom 6.5.0 Kernel by @NeroReflex](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_custom_6.5.0_kernel.md)
ChimeraOS, at the time of writing this, installs with an older kernel, this 6.5.0 is compiled specifically for the ROG Ally and brings noticable performance improvements.
EDIT: THIS IS NO LONGER TRUE, CHIMERA HAS UPDATED TO THE 6.5.3 KERNEL BY DEFAULT - SEE OTHER GUIDES

### [Stable] [Installing Custom steam-patch (by @NeroReflex) & Updating HandyGCCS](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_custom_steam_patch.md)
The original version of steam-patch contains controller input fixes which conflict with the workaround for C State found [here](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/repairing-b-state-behavior.md) as well as conflicting with HandyGCCS. This guide will install a custom version which removes the controller input fixes so HandyGCCS can handle them instead.

### [Stable] [Enabling SSH Securely on ChimeraOS](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/enabling_ssh_securely.md)
ChimeraOS by default comes without an SSH Server setup, this is intentional, as all ChimeraOS installations contain the same default root password. This guide will show you how to change that password and setup SSH so you can run commands from another PC. This can be helpful with sending commands to your device, even when its in gamemode!

### [Dev] [Installing Custom 6.6.0-rc6 Kernel](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/installing_6.6.0-rc6_custom_kernel.md)
This guide will show you how to install the 6.6.0-rc6 ROG Ally specific kernel with gyro support.

### [Testing] [Installing NeroReflex's ROG Ally frzr Package](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/neroreflex_frzr_deploy_img.md)
This guide will show you how to use frzr-deploy to install various tweaks and improvements that improve the performance of the system. Please note this is unstable at the time of writing this.

## Related Projects

[ChimeraOS](https://github.com/ChimeraOS/chimeraos)

[Steam-Patch](https://github.com/Maclay74/steam-patch) and [NeroReflex Custom Steam-Patch](https://github.com/NeroReflex/steam-patch)

[HandyGCCS](https://github.com/ShadowBlip/HandyGCCS)

[EmuDeck](https://github.com/dragoonDorise/EmuDeck)

## Helpful Commands

Install DeckyLoader:
```sh
curl -L https://github.com/SteamDeckHomebrew/decky-installer/releases/latest/download/install_release.sh | sh
```

## FAQ
### Q - Do I have to downgrade my Kernel for gyro controls?
A - Things like gyro support are being worked on, and at the time of writing this, 6.5.2 is the most stable, go-to version which still supports gyro. The Kernels listed in this guide are all custom made specifically for the ROG Ally. At the time of writing this there is also a 6.6.0-rc6 kernel which also allows gyro. PLEASE NOTE: GYRO CONTROLS ONLY WORK ON EMULATED TITLES AT THE MOMENT

### Q - How do I enable the rear paddle-buttons on the ROG Ally?
A - At this time we do not have control over mapping these two buttons, it is on the list of things to get done but currently nobody is working on it to my knowledge. If you've got a little experience in C, give it a shot!

### Q - What is "A", "B" and "C" state?
A - These are terms used to describe the sleep/wake functionality of a device.

        A State - All buttons work on boot, QAM and Steam buttons break after a sleep/wake cycle

        B State - Same as before, but the QAM and Steam buttons work every other sleep/wake cycle acting like a light switch, on and off.

        C State - All buttons work all the time

### Q - These guides have a lot of commands. Is there an easier way to send them to my ROG Ally?
A - Yes, and the answer is...another guide! Check out the guide for [securely setting up ssh on an ROG Ally](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/enabling_ssh_securely.md), this will allow you to connect from another PC to send commands. Helpful when you want to be able to have the guide up on a larger screen, but still want to copy/paste commands!

### Q - What is BMI323?
A - You may see this term thrown around in these guides, it is the model ID of the gyroscopic sensor that the ROG Ally is built with. Currently gyro is working within Nintendo Emulators but as of writing this (Oct. 21st '23) support outside of Nintendo Emulators is a work in progress.

### Q - What is frzr? 
A - You'll probably use frzr commands at some point in your usage of ChimeraOS, frzr is a deployment and automatic update mechanism for operating systems. This allows for quick and easy installation of pre-built systems without interrupting the user. You can learn more on its github page [here](https://github.com/bactaholic/chimeraos-ROG-Ally-tricks/blob/main/guides/enabling_ssh_securely.md)