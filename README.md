# kosu-winello
osu! stable installer for Linux with patched Proton-osu and other features.

![ezgif com-video-to-gif(1)](https://user-images.githubusercontent.com/98063377/224407211-70fa648c-b96f-442b-b5f5-eaf28a84670a.gif)

# Index

- [Installation](#installation)
	- [Prerequisites](#prerequisites)
 		- [Drivers](#drivers)		 
		- [PipeWire](#pipewire)
	- [Installing osu!](#installing-osu)
- [Features](#features)
- [Troubleshooting](#troubleshooting)
- [Flags](#flags)
- [Steam Deck Support](#steam-deck-support)
- [Credits](#credits)

# Installation

## Prerequisites 

The only requirements, besides **64- and 32-bit graphics drivers**, are `git`, `zenity`,`wget` and `xdg-desktop-portal` (for in-game links).

You can easily install them like this:

**Ubuntu/Debian:** `sudo apt install -y git wget zenity xdg-desktop-portal`

**Arch Linux:** `sudo pacman -Syu --needed  --noconfirm git wget zenity xdg-desktop-portal`

**Fedora:** `sudo dnf install -y git wget zenity xdg-desktop-portal`

**openSUSE:** `sudo zypper install -y git wget zenity xdg-desktop-portal`

## Drivers:

As obvious as this might sound, installing drivers the **right** way is needed to have a great experience overall
and avoid poor performance or other problems. 

Keep in mind that osu! needs **lib32 drivers** in order to run as it should, so
if you're having performance problems, it's probably related to this.

Please make sure to follow the instructions below:
- [Installing Drivers](https://github.com/lutris/docs/blob/master/InstallingDrivers.md)

## PipeWire:

`PipeWire` **isn't really a dependency but is highly recommended, especially with this script.**

Check if it's already on your system with:

```
export LANG=C
pactl info | grep "Server Name"
```

If it shows `Server Name: PulseAudio (on Pipewire)` , then you're good to go. 

Otherwise, make sure to install it following the instructions at here: 
- [Installing PipeWire](https://github.com/NelloKudo/kosu-winello/wiki/Installing-PipeWire)

## Installing osu!:
```
git clone https://github.com/PhoenixAceVFX/Kawata-winello.git
cd Kawata-winello
chmod +x ./kosu-winello.sh
./kosu-winello.sh
```

You can now launch osu! with:
```
kosu-wine
```
### ⚠ **!! \o/ !!** ⚠ :
- You might need to relaunch your terminal to launch the game.
- Use **-40/35ms** offset to make up for Wine quirks (or -25 if you're using audio compatibility mode)

# Features:
- Comes with **updatable patched** [Proton-osu](https://github.com/whrvt/umubuilder) binaries with the latest osu! patches for low-latency audio, better performance, alt-tab behavior, crashes fixes and more.
- Uses [umu-launcher](https://github.com/Open-Wine-Components/umu-launcher) to run Proton-osu on Steam's runtime, providing great performance on every system.
- Provides [osu-handler](https://aur.archlinux.org/packages/osu-handler) for importing maps and skins, Discord RPC with [rpc-bridge](https://github.com/EnderIce2/rpc-bridge) and support for native file managers!
- Supports the latest [tosu](https://github.com/KotRikD/tosu) and legacy [gosumemory](https://github.com/l3lackShark/gosumemory) for streaming etc. with automatic install! (Check [flags](#flags)!)
- Installs osu! on either default or custom path (using GUI), also working for already existing osu! installations from Windows!
- Skips the pain of downloading Wineprefix thanks to [my fork](https://gitlab.com/NelloKudo/kosu-winello-prefix) of [kosu-wineprefix](https://gitlab.com/kosu-wine/kosu-wineprefix)
- Support for Windows fonts pre-installed in Proton (JP fonts, special characters etc.)

# Troubleshooting

Please refer to [kosu-winello's wiki](https://github.com/NelloKudo/kosu-winello/wiki) for troubleshooting of any type. 

If that doesn't help, either:
- Join [ThePooN's Discord](https://discord.gg/bc4qaYjqyT) and ask in #osu-linux, they'll know how to help! <3
- Write me on Discord (marshnello)

# Flags:
**Installation script:** 
```
./kosu-winello.sh: Installs the game
./kosu-winello.sh --no-deps: Installs the game but skips installing dependencies
./kosu-winello.sh uninstall: Uninstalls the game
./kosu-winello.sh fix-umu: Tries to fix umu-launcher issues (partial downloads, corruption etc.)
```

**Game script:**
```
kosu-wine: Runs osu!
kosu-wine --winecfg : Runs winecfg on the osu! Wineprefix
kosu-wine --winetricks: Install packages on osu! Wineprefix
kosu-wine --regedit: Opens regedit on osu! Wineprefix
kosu-wine --kill: Kills osu! and related processes in osu! Wineprefix
kosu-wine --kill9: Kills osu! but with wineserver -k9
kosu-wine --update: Updates wine-osu to latest version
kosu-wine --fixprefix: Reinstalls the osu! Wineprefix from system
kosu-wine --fix-umu: Reinstalls files related to umu-launcher in case something went wrong
kosu-wine --fixfolders: Reinstalls registry keys for native file manager in case they break
kosu-wine --fixrpc: Reinstalls rpc-bridge if needed!
kosu-wine --info: Troubleshooting and more info
kosu-wine --remove: Uninstalls osu! and the script
kosu-wine --changedir: Changes directory of the install according to the user
kosu-wine --devserver <address>: Runs osu with an alternative server (e.g. --devserver akatsuki.gg)
kosu-wine --runinprefix <file>: Launches a custom executable within osu!'s Wineprefix
kosu-wine --osuhandler <beatmap, skin..>: Launches osu-handler-wine with the specified file/link
kosu-wine --gosumemory: Installs and runs gosumemory without any needed config!
kosu-wine --tosu: Installs and runs tosu without any needed config!
kosu-wine --disable-memory-reader: Turn off gosumemory and tosu
```

# Steam Deck Support

Since osu! runs on Proton, you can play that on Steam Deck as well!

It is recommended to not manually install PipeWire on the Steam Deck as it is already installed by default and attempting to do so may cause audio issues.

# Credits

Special thanks to:

- [whrvt aka spectator](https://github.com/whrvt/wine-osu-patches) for his help with Wine, Proton and related, never failed to solve any issue :')
- [ThePooN's Discord](https://discord.gg/bc4qaYjqyT) for supporting Winello since its early stages!
- [umu-launcher](https://github.com/Open-Wine-Components/umu-launcher) for making using Proton as easy as this!
- [gonX's wine-osu](https://drive.google.com/drive/folders/17MVlyXixv7uS3JW4B-H8oS4qgLn7eBw5)
- [Integrating native file manager by Maot](https://gist.github.com/maotovisk/1bf3a7c9054890f91b9234c3663c03a2)
- [KatouMegumi's guide](https://wiki.archlinux.org/title/User:Katoumegumi#osu!_(stable)_on_Arch_Linux)
- [hwsnemo's wine-osu](https://software.opensuse.org//download.html?project=home%3Ahwsnemo%3Apackaged-wine-osu&package=wine-osu)
- [diamondburned's kosu-wine](https://gitlab.com/kosu-wine/kosu-wine)
- [openglfreak's packages](https://github.com/openglfreak)
- [EnderIce2's rpc-bridge](https://github.com/EnderIce2/rpc-bridge)
- Last but not least, every contributor. Thanks for making Winello even better!

And that's all. Have fun playing osu!

## Check the guide above for troubleshooting or extra tools!

