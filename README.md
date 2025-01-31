
# Installation
### User needs be in `input` group
```
sudo usermod -aG input $USER
```
* For Fedora Silverblue
```
# group 'input' needs to be in /etc/group first
grep -E '^input:' /usr/lib/group | sudo tee -a /etc/group
sudo usermod -aG input $USER
```

### **From releases**
- Download zip file from [releases](https://github.com/harshadgavali/gnome-x11-gesture-daemon/releases)
- Extract zip file
- Inside extracted folder, Run 
```
# Without sudo/root
sh install.sh # Reboot is needed after this

# ** OR ** to restart daemon, without rebooting
sh install.sh --restart

```

### Distributions

* Arch Linux/Manjaro Linux - [gnome-x11-gesture-daemon](https://aur.archlinux.org/packages/gnome-x11-gesture-daemon) Thanks to @[yochananmarqos](https://github.com/yochananmarqos)
```code
yay -S gnome-x11-gesture-daemon
```

### Build from source

#### Using docker/podman
```
make build-docker && make install
```

#### Without docker/podman
* First install build dependencies
```
# dnf/rpm based distributions
sudo dnf install cargo libinput-devel

# apt/deb based distributions
sudo apt install cargo libinput-dev
```
* Then build and install
```
make build && make install
```

### Troubleshooting
- First make sure you've restarted your system after installing.

- Run following command to check if service is running properly (It should be running on X11).
```
systemctl --user status gesture_improvements_gesture_daemon.service
```

- Open issue on github, with output of the above command
### Uninstallation
```
# Without sudo/root
sh ./uninstall.sh
```

# Contributors
[Swastik Dwivedi](https://github.com/drunckj)

# Thanks
[@Smithay](https://github.com/Smithay) for [rust bindings](https://crates.io/crates/input)  for libinput

[FreeDesktop/Dbus Project](https://gitlab.freedesktop.org/dbus/) for [Rust API](https://crates.io/crates/zbus) for D-Bus.
