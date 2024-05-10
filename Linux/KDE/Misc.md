### Clear all KDE configurations

remove the following files:

```
/home/seraj/.kde4
/home/seraj/.local/share/plasma
/home/seraj/.config/kdeglobals
/home/seraj/.config/kwinrc
```
### Missing video thumnail

```
sudo pacman -S ffmpegthumbs kdegraphics-thumbnailers
```

Then navigate to Dolphin configuration and enable thumnail for movies and PDF files or other extensions


### Add global menu for latte-dock


### Merge title bar with top menu bar

1. Install window buttons plasma applet
  ```bash
  sudo pacman -S plasma5-applets-window-buttons`
  ```
2. Add `Window Title Applet widget` to top menu bar

3. Remove title bar for maximized window
  ```bash
  kwriteconfig5 --file ~/.config/kwinrc --group Windows --key BorderlessMaximizedWindows true && qdbus org.kde.KWin /KWin reconfigure
  ```
  > latte-dock will reset this setting i don't know why we can lock the config file after running `kwriteconfig5` by `chattr +i ~/.config/kwinrc`. 

> :warning: By running this command your System Settings will be no longer changable. So you need to run `chattr -i ~/.config/kwinrc` once you want to make modifications.
4. To make the global menu available for gtk applications install the following packages:

```bash
sudo pacman -S appmenu-gtk-module libappindicator-gtk3 libdbusmenu-gtk3
```

5. Right click on Window buttons to make and open its settings.
6. Set the `Show` to `last active windows is maximized`

---
install `appimagelauncher` to install appimage files. (I dont know how to remove the installed package)
---
install `libdbusmenu-glib` if global menu is not working on vscode.
install `plasma-applet-window-buttons` to make `Window Buttons` widget work.
for making the vscode to remove extra top border right click on it and choose `More Actions` and select `No titlebar and frame`
