## Introduction:
There are several kernel's created for the ROG Ally, I (@bactaholic) have personally 6.5.0 to be the most stable at the time of writing this (9/20/23). This guide serves as an installation guide for [@NeroReflex](https://github.com/NeroReflex) custom 6.5.0 kernel, and also includes the commands needed to downgrade back to 6.4.7 if needed. The majority of this guide is from a different gist originally, portions of which are outdated/conflict with other guides in this repository. You can find the original gist from [@NeroReflex](https://github.com/NeroReflex) [here](https://gist.github.com/NeroReflex/e546ca365b86d3ef226ea4a085bfae43)

## Get DKMS
For dkms to work you will need base-devel as well as dkms itself.

Not using/breaking dkms will have no impact on the ally itself, but may break additional hardware for example bluetooth xbox one controller

```sh
sudo pacman -S base-devel dkms unzip git wget
```

## Download & extract LLVM
Kernel is compiled with clang and it will be needed to properly recompile kernel modules with dkms:

```sh
cd ~ # this is very important for a later command.
wget http://neroreflex.duckdns.org/llvm.zip # this one comes from my bedroom: please be patient
unzip llvm.zip
```

## Downloading the kernel
The kernel has to be downloaded, yes, you guessed it... from my bedroom.

Kernel 6.4.7 got more testing, has horizon zero dawn performance regression but otherwise a 10% performance boost.
Contreller after resume had a different behaviour for every person. For me sometimes I lost steam and guide buttons but never native-xbox buttons!

```sh
mkdir ~/kernel_6.4.7
cd ~/kernel_6.4.7
wget http://neroreflex.duckdns.org/linux-chimeraos-6.4.7.chos4-1-x86_64.pkg.tar.zst
wget http://neroreflex.duckdns.org/linux-chimeraos-headers-6.4.7.chos4-1-x86_64.pkg.tar.zst
```

Kernel 6.5.0 has (at the moment) very low in-game testing: who tested it reported a visible performance gain, in games and in switch emulator, tested with a zelda title!
The known total number of people that installed this version is now 5.
Might also have negative impact on some -untested- games (like horizon zero dawn).
Prepare for a mystical experience either way!
```sh
mkdir ~/kernel_6.5.0
cd ~/kernel_6.5.0
wget http://neroreflex.duckdns.org/linux-chimeraos-6.5.chos1-1-x86_64.pkg.tar.zst
wget http://neroreflex.duckdns.org/linux-chimeraos-headers-6.5.chos1-1-x86_64.pkg.tar.zst
```

## Installing the kernel
In order to install the kernel you cd into the directory containing the downloaded kernel and do:

```sh
export PATH="/home/gamer/llvm-project-llvmorg-17.0.0-rc1/build/bin:$PATH"
sudo pacman -U *.tar.zst
```

## Firmware Overrides
If you are installing 6.5.0 firmware overrides MUST be DISABLED for sound to work.

If you are installing 6.4.7 firmware overrides MUST be ENABLED for sound to work.

firmware overrides are controlled via:
```sh
sudo nano /etc/device-quirks/device-quirks.conf # 0 = disabled, 1 = enabled
# same as before.... Ctrl+O, Ctrl+X
sudo frzr-tweaks

# !!! WARNING !!! ONLY DO THIS IF YOU WANT TO DISABLE OVERRIDES, IT SHOULD HOWEVER NOT BE NEEDED
# at this point I noticed overrides were still in the bootloader config file, I just:
sudo nano /boot/loader/entries/frzr.conf # here you find the "initrd /rog_ally_0x58_acpi_override" line with ally quirks and comment it (place # in front of the correct line)
```

## Get the kernel to boot
Here you have to options, you copy the new kernel over the old one (ugly way, just works):

```sh
cd /boot
sudo cp vmlinuz-linux-chimeraos vmlinuz-linux
sudo cp initramfs-linux-chimeraos.img initramfs-linux.img
```

Or you edit the bootloader configuration (this is the proper way, but you MUST be careful):
```sh
sudo nano /boot/loader/entries/frzr.conf
#change the line "initrd /initramfs-linux.img" with "initrd /initramfs-linux-chimeraos.img"
#change the line "linux /vmlinuz-linux" with "linux /vmlinuz-linux-chimeraos"
# WARNING: Triple check you spelled file correctly or IT WILL NOT BOOT AND THE CONSOLE WILL BE DEAD!!!
```
