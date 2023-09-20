## Introduction:
This guide details how to install [@NeroReflex](https://github.com/NeroReflex) version of steam-patcher which removes the controller support but maintains the rest of the changes included such as TDP support and Icon Swapping. HandyGCCS is installed instead to handle the controller inputs. The following was taken from a gist originally written by @NeroReflex(https://github.com/NeroReflex) which contains some outdated information which conflicts with other guides in this repository. These sections were taken from there as they do not conflict. The original gist can be found [here](https://gist.github.com/NeroReflex/e546ca365b86d3ef226ea4a085bfae43)

## TDP control
To have TDP control working you use steam-patch. I have put together a steam-patch that only provides TDP control and does not manages buttons, so that you can use [AntiMicroX](https://github.com/AntiMicroX/antimicrox) to use joysticks to control mouse in desktop mode:

```sh
sudo systemctl stop steam-patch # don't worry if this fail. It's normal...
sudo pacman -S rust
cd ~
mkdir src
cd src
git clone https://github.com/NeroReflex/steam-patch.git
cd steam-patch
cargo build --release
mkdir ~/steam-patch
sudo cp target/release/steam-patch ~/steam-patch/steam-patch
chmod a+x ~/steam-patch/steam-patch
```

Then create the file ~/steam-patch/steam-patch.service with the following content:

```
[Unit]
Description=Steam Patches Loader
Wants=network.target
After=network.target

[Service]
Type=simple
User=root
ExecStart=${WORKING_FOLDER}/steam-patch --user=gamer
WorkingDirectory=/home/gamer/steam-patch

[Install]
WantedBy=multi-user.target
```

and finally run:

```sh
cp ~/steam-patch/steam-patch.service "/etc/systemd/system/steam-patch.service"
sudo chown root "/etc/systemd/system/steam-patch.service"

# Run service
sudo systemctl daemon-reload
sudo systemctl enable steam-patch.service
sudo systemctl start steam-patch.service
```
## Updating HandyGCCS
As my fork of steam-patch does not manages input it is important to update the handycon service:

```sh
sudo systemctl stop handycon
# now your buttons should not be working!
pikaur -Sy handygccs-git
sudo systemctl enable --now handycon
# now your buttons should be working again!
```

If updating handycon fails with an error do the following and then try again to update:

```sh
sudo pacman -S python-setuptools
```
