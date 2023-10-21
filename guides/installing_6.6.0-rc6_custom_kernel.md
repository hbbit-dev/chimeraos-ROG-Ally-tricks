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

```title chimeraos-<your_deployment>-nrflx gyro 
linux /vmlinuz-linux-neroreflex
initrd /amd-ucode.img
initrd /initramfs-linux-neroreflex.img
options root=LABEL=frzr_root rw rootflags=subvol=deployments/chimeraos-<your_deployment> quiet splash loglevel=3 rd.systemd.show_status=auto rd.udev.log_priority=3  ibt=off split_lock_detect=off iomem=relaxed amd-pstate=active nowatchdog
```
Make sure to edit <your_deployment> with whatever your brtfs subvolume is!

Then edit the already existing /boot/loader/loader.conf and add the following lines to the top of the file so that it will default to the newly installed kernel, also allowing you to also select the previous one in case of problems:

```
default frzr-neroreflex.conf
timeout 3
//rest of the code below
```
then simply reboot...

```sudo systemctl reboot```