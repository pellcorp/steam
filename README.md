# Game Tweaks

## Sonic & All-Stars Racing Transformed Collection

https://www.protondb.com/app/212480

Custom controller and settings configuration to play on a Ubuntu machine without a dedicated graphics card.

Using a wired Betop PS4 Fun Controller

Installs fine on Steam on Ubuntu using Proton 7.0, but once I configure this controller, after that things get a little weird.   I could not configure graphics settings after making the controller changes, and trying to setup a second controller was problematic, but I think perhaps I can just manually edit these files bypassing the dodgy UI.

Once you have run the Configure step successfully at least once you can find these files at:

```
~/.steam/steam/steamapps/compatdata/212480/pfx/drive_c/users/steamuser/Documents/SART/
```

# Hardware Issues

## Bebop PS4 Fun Controller

aka EBGames Play Wired Controller

For Ubuntu at least, in order to get the EBGames Wired controller to work, need to add udev rule and some modules config.

1) Copy https://gitlab.com/fabiscafe/game-devices-udev/-/raw/main/71-betop-controllers.rules to to /etc/udev/rules.d/:
```
wget -q https://gitlab.com/fabiscafe/game-devices-udev/-/raw/main/71-betop-controllers.rules -O- | sudo tee /etc/udev/rules.d/71-betop-controllers.rules > /dev/null
```

2) Load the uninput module:
```
echo "uinput" | sudo tee /etc/modules-load.d/uinput.conf > /dev/null
```

3) Reboot

Im not sure if reboot is strictly required

