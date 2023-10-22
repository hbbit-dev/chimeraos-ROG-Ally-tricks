# Introduction

This guide will show you how to download and install [NeroReflex's](https://github.com/NeroReflex) custom ROG Specific frzr package. This allows for easy installation of most of the various changes NeroReflex has made to optimize the performance on the ROG.

Please note this is an unstable package which is still undergoing testing, proceed at your own risk.

### Step 1 - Download the .img.tar.xz

The image can be found at:

```https://github.com/NeroReflex/chimeraos/releases/tag/45_6f671d3```

Downloading this through firefox should place it in your Downloads folder by default. We're going to make a specific folder for it to make things neat.

```mkdir ~/neroreflex-frzr-img```
```cd ~/neroreflex-frzr-img```
```mv ~/Downloads/chimeraos-file-version-you-downloaded ~/neroreflex-frzr-img/```

### Step 2 - Deploy the image

Use the following command to deploy the image on your system:

```frzr deploy ~/neroreflex-frzr-img/chimeraos-file-version-you-downloaded```

please remember to swap the file name for whichever version you downloaded. After this you should be able to reboot using ```systemctl reboot``` and it should be installed properly.