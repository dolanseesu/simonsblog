---
title: "What To Do After Installing Arch Linux"
#title: "What to do after installing Arch Linux"
date: 2020-10-10T14:29:09+02:00
description: ""
categories:
  - "Arch"
tags:
#  - ""

draft: false

# theme-specific params
lead: "Some steps to get you started."
comments: false # Enable Disqus comments for specific page
authorbox: true # Enable authorbox for specific page
pager: true # Enable pager navigation (prev/next) for specific page
toc: true # Enable Table of Contents for specific page
mathjax: false # Enable MathJax for specific page
sidebar: "right" # Enable sidebar (on the right side) per page
widgets: # Enable sidebar widgets in given order per page
  - "taglist"
---

You have successfully installed Arch and you're wondering what to do next? Let's go through some steps to get a working system.
The overall steps might apply to other minimal Linux distros (Void, Gentoo) as well, but be sure to check the corresponding Wiki.

In this guide I will be using Arch Linux, but the overall steps apply to all linux distros. You might want to double check with the according Wiki though.

## Add a user

As the first step, let's add a user, so you don't have to log in as root everytime. Also, always working as root is a bad habit.
The new user will be added to the 'wheel' group, which means he can run every command as with root privileges if he so chooses. To enable the wheel group, we need to edit the visudo file.

```bash
sudo EDITOR=vim visudo
```

You can replace vim with any text editor you want, for example Nano. Then, uncomment the line `%wheel ALL=(ALL) ALL`. Now we can add the new user.

```bash
useradd -m -G wheel -s /bin/bash <USERNAME>
```

This adds a new user with his own hime directory to the wheel group and specifies the shell he is using (bash, in this case). Of course you have to replace `<USERNAME>` with your own username.

Now, the user needs a password:

```bash
passwd <USERNAME>
```

Type in a password and confirm it.

## Install microcodes

The microcode patches provide security and stability updates for every Intel and AMD processor, so you should install them.

```bash
sudo pacman -S intel-ucode
OR
sudo pacman -S amd-ucode
```

After the package is installed, we need to reconfigure GRUB to load the microcode update:

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

Restart your system for the changes to take effect.

## AUR helper

An AUR helper makes it easy to install packages from the Arch User Repository (AUR) which immensly expands the programs you can use on Arch. yay is the most popular one and there are only a few steps to install it.

First, we need git, be be able to clone the repository:

```bash
sudo pacman -S git
```

Then we can download the repo.

```bash
git clone https://aur.archlinux.org/yay.git
```

As the last step, navigate into the yay directory and and install it.

```bash
cd yay
makepkg -si
```

Since yay is a pacman wrapper, you can run normal pacman commands also with yay.
___Note:__ Never run yay with root privileges, the program will even abort. You will get asked for your password during the installation.

## Display drivers

Depending in your graphics card, you need the corresponding graphics driver.

Platform | Package
--- | ---
AMD | mesa
Intel graphics | mesa
Nvidia | nvidia

If you have a older or a more specific graphics card, be sure to check the Arch Wiki.

If you are using Xorg, also install the `xorg-drivers` package.

## Useful services

These services are really useful for resource and disk management.

```bash
sudo pacman -S acpid ntp dbus avahi cups cronie
```

Then, enable these services, so they get started when the system boots up.

```bash
sudo systemctl enable acpid
sudo systemctl enable ntpd
sudo systemctl enable avahi-daemon
sudo systemctl enable org.cups.cupsd.service
```

## Sound server

The base Arch install doesn't provide and sound output, so we need to install a sound server.

```bash
sudo pacman -S pulseaudio pulseaudio-alsa alsa-utils
```

Reboot you system after the installation.
Pulseaudio works out of the box, you only need to unmute the channels. This can be done with the command `alsamixer`. Select your sound card with `F6` and unmute the required channels with `m`.

If you want a graphical user interface to do this, install the `pavucontrol` package.

## Graphical user interface

If you want to operate your distribution with a GUI, be it a full-featured desktop environment or just a window manager, you need a display server. I will be using Xorg.

```bash
pacman -S xorg-server xorg-xinit xorg-drivers
```

### Window manager

If you are just using a window manager, you need a display and login manager and the WM itself.
I am using `lightdm` and its gtk-greeter as a display manager and `awesome` as my window manager.

```bash
sudo pacman -S lightdm lightdm-gtk-greeter awesome
```

To enable lightdm on startup, run:

```bash
sudo systemctl enable lightdm.service
```

I have made and introduction to Awesome [here](link_to_awesome.md).

### Desktop environment

I am using Gnome as an example in this guide. For more desktop environments, see [here](https://wiki.archlinux.org/index.php/Desktop_environment).

 To install Gnome and all its features just install the `gnome` package.
If you want a more minimal approach, install only the following packages:

```bash
pacman -S gnome-shell nautilus gnome-terminal gnome-tweak-tool gnome-control-center xdg-user-dirs gdm gnome-keyring
```

Now enable the Gnome Display Manager:

```bash
systemctl start gdm.service
systemctl enable gdm.service
```

Now you can install your everyday programs like a terminal emulator, browser, file explorer, etc.

## References

- [Arch Wiki: General recommendations](https://wiki.archlinux.org/index.php/General_recommendations#Hardware_auto-recognition)
- [yay GitHub repo](https://github.com/Jguer/yay)