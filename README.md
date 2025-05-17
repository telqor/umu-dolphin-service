# UMU Dolphin Service

This service/script makes it possible to run games and other Windows executables via umu and GE-Proton, by using the right click context menu in KDE Plasma 6's Dolphin file browser.

In addition, it can create a shortcut which can be moved (to the desktop for example) or renamed at will, to make subsequent launches easier.

## Prerequisite:
Umu must be installed and launchable from the default path. You can verify this and also initialize the prefix and Proton version used by this script by running this command:

```
GAMEID=UmuDolphinService PROTONPATH=GE-Proton umu-run notepad
```
If Umu is not present, I recommend that you use your distribution's package manager to install it. 

## Installation:
1. Make sure that your servicemenus folder exists, if not create it with this command:
```
mkdir -p $HOME/.local/share/kio/servicemenus/
```

2. Download the script into your servicemenus folder:
```
wget -O $HOME/.local/share/kio/servicemenus/umu-dolphin.desktop https://github.com/telqor/umu-dolphin-service/raw/refs/heads/main/umu-dolphin.desktop
```

3. Make the script executable:
```
chmod +x $HOME/.local/share/kio/servicemenus/umu-dolphin.desktop
```

4 (Optional). Restart Dolphin if the extra menu options do not appear when right clicking an .exe file. 

## FAQ:

**Q: Why not just use system Wine to open .exe files?**

A: Wine does not automatically prepare specialized prefixes for gaming like Umu (or Proton in and of itself) do, resulting in often missing critical gaming libraries such as DXVK, VKD3D... 

Even if said libraries are present the versions of Wine shipped by most distributions are based on upstream Wine rather than Valve's gaming-optimized tree, so in games that don't need any cutting edge features from upstream the performance and compatibility will almost always be worse. This provides the most Steam-like environment possible without actually using Steam.

**Q: Why use the same prefix for all games?**

A: This makes it much more simple to deal with installer executables, and in my experience it is not commonplace for games to interfere with each other within a prefix.

**Q: If I used an installer, where are my games installed?**

A: The path to your virtual C drive should be $HOME/Games/umu/UmuDolphinService/drive_c/, from there it depends on what the installer uses as a path, either given as user input or sticking to some default path in Program Files. 
