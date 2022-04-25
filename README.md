# KoGaMa on Linux
In this guide, you'll learn how to install KoGaMa Standalone app on a Linux environment.

Note: each server has it's own launcher and protocol, so be aware that you have to repeat this process for every different server you play.

```
kogama2-br // for www.kogama.com.br
kogama2-www // for www.kogama.com
kogama2-friends // for friends.kogama.com
```

**In this tutorial we'll be installing the WWW version of the game.**

Requirements:
- Latest ```wine```   
-- ```dotnet45```  
-- ```wine-mono```  

## Installing Wine
First, you have to install the latest version of Wine.  
Visit https://wiki.winehq.org/Download to see the installation steps on your distro.

You can install dotnet45 using WineTricks:
```
winetricks dotnet45
```

## Getting the MSI installer
You need to download the official KoGaMa Standalone installer.
To do this, go to any game, add the **?standalone=1** string in front of the link and click the green button that says "Download KoGaMa".  
Example: https://www.kogama.com/games/play/2593313/?standalone=1

## KoGaMa Standalone Installation
After you downloaded the **KogamaLauncher.msi**, open the Terminal and use the ```cd``` command to go to the directory that contains the installer. If you downloaded it on the default Downloads dir:  
```
cd ~/Downloads
```

Then, initiate the installation process by running the following command:  
```
wine KogamaInstaller.msi
```

If you got a Success message from the launcher, then we can go to the next step:

##  Configuring the URL protocols
In order to play KoGaMa games, we need to configure the .desktop files to handle protocol calls.

First, create a Desktop Entry on ```~/.local/share/applications```
```
touch ~/.local/share/applications/kogama-launcher.desktop
```

Then, edit the file and paste the following text:

```
[Desktop Entry]
Type=Application
Name=KoGaMa WWW
Exec=wine "C:\users\YOUR_USERNAME\Local Settings\Application Data\KogamaLauncher-WWW\BootStrapperWWW.exe" %u
StartupNotify=false
Terminal=false
MimeType=x-scheme-handler/kogama2-www;
```

Remember to change **YOUR_USERNAME** to your current user username.

Now, set this desktop file as default for KoGaMa protocol:

```
xdg-mime default "~/.local/share/applications/kogama-launcher.desktop" x-scheme-handler/kogama2-www
```

Add it to the ~/.local/share/applications/mimeapps.list:

```
[Default Applications]
x-scheme-handler/kogama2-www=kogama-launcher.desktop
```

And then set it as executable:

```
chmod +x ~/.local/share/applications/kogama-launcher.desktop
```

Now you should be ready to go!
