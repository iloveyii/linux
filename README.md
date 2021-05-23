# Linux

## Reset password

- Error : enter root password for maintenance
- Press shift as soons as system starts
- Advanced option > Goto normal Ubuntu line (with no recovery) > Press e
- Enter init=/bin/bash at the end of `linux` line (remove everything after `ro` first)
- Press F 10
- It will start in single user mode, reset required user's password and reboot

## Reset Ubuntu password in Vmware
- To show boot menu for a longer time, locate the vmare directory and open the .vmx file in text editor
- Add the following at the end of the file, timeout is in milliseconds (make sure the vm machine is off else this change will be overwritten)
```
bios.bootDelay = "5000"
```
- Boot vmaware machine and press and hold shift key, select advanced > recovery > root
- If the file system is ready only use commamnd `mount -rw -o remount /`

## Graphics

- Identify video card `lspci | grep VGA`
- Details `sudo lshw -C video`

## Applications
- Add a custom launcher to dock
- First create a file `~/.local/share/applications/intellij.desktop` with the following contents
```bash
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=IntelliJ
GenericName=IDE
Exec=/home/alex/softwares/intellij/bin/idea.sh
Icon=/home/alex/softwares/intellij/bin/idea.svg
```
- List the dock apps `gsettings get org.gnome.shell favorite-apps`
- Set custom launcher in dock `gsettings set org.gnome.shell favorite-apps "['org.gnome.Nautilus.desktop','intellij.desktop', 'org.gnome.Terminal.desktop', 'google-chrome.desktop', 'firefox.desktop', 'gnome-control-center.desktop', 'org.gnome.tweaks.desktop']"`

