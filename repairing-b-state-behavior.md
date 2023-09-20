# Repairing B State Behavior v2.0
### Written by: [@bactaholic](https://github.com/bactaholic)
### Method found by: [@NeroReflex](https://github.com/NeroReflex) and @WagesOf

## Disclaimer: I am not responsible for any damage to your system. This software is experimental, though there have been no recorded cases of damage, and everything done is reversible.

## Introduction: This guide will provide a workaround for A or B state ROG Allys. This is a workaround that comes with some quirks. For example, after reawakening, your screen will go black, and then come back after a few seconds. Additionally, the first button you press may result in that input repeating itself until a 2nd button is pressed, at which point it the controls will return to normal. Aside from these two quirks, the workaround works perfectly.

## Step 1
Install ChiemraOS, you can use the stock version or upgrade your kernel to 6.5.0, 6.5.1, or 6.5.2 so long as your system is otherwise stable (with the exception of working QAM/Steam buttons).

## Step 2
After installation, run the following commands to create a directory for your scripts to live:
```
mkdir ~/scripts
cd ~/scripts
```

# Step 3
After creation, create a .sh script file, this can be named whatever you'd like. Fill the sh script with the following contents...
```
#!/bin/bash

case "$1" in
    pre)
            # Code execution BEFORE sleeping/hibernating/suspending
    ;;
    post)
           sleep 2
           echo "Post suspend check for N-Key" > /dev/kmsg
           if grep -Fxq 'ROG Ally' "/sys/devices/virtual/dmi/id/product_family" ; then
                if [[ $(lsusb | grep "0b05:1abe") == "" ]]; then
            echo "Post suspend reinit to find N-Key" > /dev/kmsg
             echo platform > /sys/power/pm_test
                    echo freeze > /sys/power/state
                    echo none > /sys/power/pm_test
                 fi
            fi

    ;;
esac
```
# Step 4
Run the following commands to install your .sh script to its final directory:
```
install -Dm755 ~/scripts/yourShFileName.sh -t ${pkgdir}/usr/lib/systemd/system-sleep
```
***If you make any changes to the script in ~/scripts, re-run this command to replace the old script.***


# Step 5
Run the following command and make sure the contents of the folder match the contents below:
```
sudo nano /usr/lib/systemd/system/systemd-suspend.service
```
contents:
```
[Unit]
Description=System Suspend
Documentation=man:systemd-suspend.service(8)
DefaultDependencies=no
Requires=sleep.target
After=sleep.target

[Service]
Type=oneshot
ExecStart=/usr/lib/systemd/systemd-sleep suspend
```
# Step 6
Run the following command and make sure the "blacklist xpad" line has a # in front of it. LEAVE THE REST OF THE CONTENTS AS THEY ARE:
```
sudo nano /etc/modprobe.d/xone-blacklist.conf
```
comment out the "blacklist xpad" line as follows
```
#blacklist xpad
```
# Step 7
Run the following commands, in this order:
```
sudo systemctl disable --now steam-patch
```
```
sudo pikaur -S handygccs-git
```
```
sudo systemctl enable --now handycon
```
```
sudo systemctl reboot
```
***Congrats!*** You should now have a C-Like state with the quirks listed above.
