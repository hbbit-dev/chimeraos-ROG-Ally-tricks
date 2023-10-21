# Introduction
This guide will provide the nessecary steps to install the ROG Ally Specific 6.6.0-rc6 Kernel. The process is pretty simple, download the required packages and install them using pacman. **This kernel DOES contain the BMI323 Kernel Driver for Gyro controls, please see gyro guide for more details after installation if desired.**

### Step 1 - Download packages

```mkdir ~/kernel_6.6.0-rc6```
```cd ~/kernel_6.6.0-rc6```
```wget http://neroreflex.duckdns.org/linux-neroreflex-6.6.0.rc6.nrflx1-1-x86_64.pkg.tar.zst```
TODO: LINK
```wget http://neroreflex.duckdns.org/linux-neroreflex-6.6.0.rc6.nrflx1-1-x86_64.pkg.tar.zst```

### Step 2 - Install packages via Pacman

```sudo pacman -U *.pkg.tar.zst```

### Step 3 - Get the new kernel to boot

```sudo nano /boot/loader/entries/frzr.conf```

-Change the line "initrd /initramfs-linux.img" to say "initrd /initramfs-linux-chimeraos.img"

-Change the line "linux /vmlinuz-linux" to say "linux /vmlinuz-linux-chimeraos"

### WARNING:
***Triple check you spelled file correctly or IT WILL NOT BOOT AND THE CONSOLE WILL BE DEAD!!!***

After this step you should be able to reboot into the new kernel using ```systemctl reboot```. 