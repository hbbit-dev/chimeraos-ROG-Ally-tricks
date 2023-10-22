# Introduction
This guide will provide the nessecary steps to install the ROG Ally Specific 6.6.0-rc6 Kernel. The process is pretty simple, download the required packages and install them using pacman. **This kernel DOES contain the BMI323 Kernel Driver for Gyro controls, please see gyro guide for more details after installation if desired.**

### Step 1 - Download packages

```mkdir ~/kernel_6.6.0-rc6```

```cd ~/kernel_6.6.0-rc6```

```wget http://neroreflex.duckdns.org/linux-neroreflex-6.6.0.rc6.nrflx1-1-x86_64.pkg.tar.zst```

```wget http://neroreflex.duckdns.org/linux-neroreflex-6.6.0.rc6.nrflx1-1-x86_64.pkg.tar.zst```

### Step 2 - Install packages via Pacman

First, if you have not before, you will need to run the following command...

```sudo frzr-unlock```

Once the system is unlocked, or if its already unlocked, run...

```sudo pacman -U *.pkg.tar.zst```

### Step 3 - Get the new kernel to boot

```sudo nano /boot/loader/entries/frzr-neroreflex.conf```

And paste the following contents into it...

```
title chimeraos-<your_deployment>-nrflx gyro 
linux /vmlinuz-linux-neroreflex
initrd /amd-ucode.img
initrd /initramfs-linux-neroreflex.img
options root=LABEL=frzr_root rw rootflags=subvol=deployments/chimeraos-<your_deployment> quiet splash loglevel=3 rd.systemd.show_status=auto rd.udev.log_priority=3  ibt=off split_lock_detect=off iomem=relaxed amd-pstate=active nowatchdog
```
Make sure to edit <your_deployment> with whatever your brtfs subvolume is! To find your deployment use the following steps

```sudo nano /boot/loader/entries/frzr.conf```

check the last line in the file under options, you should see a path: deployments/chimeraos-xxxx, for example mine says

```options root=LABEL=frzr_root rw rootflags=subvol=deployments/chimeraos-44-1_4b7363e...```

so my active deployment is ```44-1_4b7363e```

Next, you need to set the new frzr-neroreflex.conf as the default boot entry. To do this, use the following command:

```sudo bootctl set-default "frzr-neroreflex.conf"```

then simply reboot...

```sudo systemctl reboot```

### Disclaimer
If you reboot and none of the controls work, this is most likely because they've been blacklisted by accident. If this is the case, use the touch screen to navigate to the desktop and then run the following command...

```sudo nano /etc/modprobe.d/xone-blacklist.conf```

locate the line which says ```blacklist xpad``` and change it to ```#blacklist xpad```, this will comment out that code so it is ignored. Reboot the device and controls should work again.