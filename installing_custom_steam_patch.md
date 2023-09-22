# Installing @NeroReflex Custom Steam Patch

## Introduction:
This guide details how to install [@NeroReflex](https://github.com/NeroReflex) version of steam-patcher which removes the controller support but maintains the rest of the changes included such as TDP support and Icon Swapping. HandyGCCS is installed instead to handle the controller inputs. The following was taken from a gist originally written by [@NeroReflex](https://github.com/NeroReflex) which contains some outdated information which conflicts with other guides in this repository. These sections were taken from there as they do not conflict. The original gist can be found [here](https://gist.github.com/NeroReflex/e546ca365b86d3ef226ea4a085bfae43)

## TDP control
I have put together a steam-patch that only provides TDP control and does not manages buttons, so that you can use [AntiMicroX](https://github.com/AntiMicroX/antimicrox) to use joysticks to control mouse in desktop mode, and to not interfere with HandyGCCS controller support:

```sh
sudo systemctl stop steam-patch # don't worry if this fail. It's normal...
```
```sh
sudo pacman -S rust
```
```sh
cd ~
```
```sh
mkdir src
```
```sh
cd src
```
```sh
git clone https://github.com/NeroReflex/steam-patch.git
```
```sh
cd steam-patch
```
```sh
cargo build --release
```
```sh
mkdir ~/steam-patch-release
```
```sh
sudo cp target/release/steam-patch ~/steam-patch-release/steam-patch
```
```sh
chmod a+x ~/steam-patch-release/steam-patch
```

Then create the file ~/steam-patch-release/steam-patch.service...

```sh
sudo nano ~/steam-patch-release/steam-patch.service
```
And fill with the following contents...
```
[Unit]
Description=Steam Patches Loader
Wants=network.target
After=network.target

[Service]
Type=simple
User=root
ExecStart=/home/gamer/steam-patch-release/steam-patch --user=gamer
WorkingDirectory=/home/gamer/steam-patch

[Install]
WantedBy=multi-user.target
```

***Disclaimer:***
If you changed your username, swap "gamer" for your username in all instances "gamer" is used.

then copy the service file to its destination folder, and assign its proper owner

```sh
cp ~/steam-patch-release/steam-patch.service "/etc/systemd/system/steam-patch.service"
```
```sh
sudo chown root "/etc/systemd/system/steam-patch.service"
```

finally, run the service with...

```sh
sudo systemctl daemon-reload
```
```sh
sudo systemctl enable steam-patch.
```
```sh
sudo systemctl start steam-patch.service
```
## Updating HandyGCCS
As [@NeroReflex](https://github.com/NeroReflex) fork of steam-patch does not manages input it is important to update the handycon service:

```sh
sudo systemctl stop handycon
```
```sh
pikaur -Sy handygccs-git
```
```sh
sudo systemctl enable --now handycon
```

If updating handycon fails with an error do the following and then try again to update:

```sh
sudo pacman -S python-setuptools
```

You should now have full TDP control to exceed 15W within the Quick Access Menu in the Game Mode UI.