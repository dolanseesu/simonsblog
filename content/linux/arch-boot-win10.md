---
title: "How To Dualboot Arch Linux And Windows 10"
date: 2020-09-22T12:01:40+02:00
description: ""
categories:
  - "Windows"
  - "Arch"
tags:
  - "Grub"
  - "Dual Boot"

draft: false

# theme-specific params
lead: "Don't want to live without either one? Here's a guide to get you going."
comments: false # Enable Disqus comments for specific page
authorbox: true # Enable authorbox for specific page
pager: true # Enable pager navigation (prev/next) for specific page
toc: true # Enable Table of Contents for specific page
mathjax: false # Enable MathJax for specific page
sidebar: "right" # Enable sidebar (on the right side) per page
widgets: # Enable sidebar widgets in given order per page
  - "taglist"
---

## Things to consider

In this guide I am assuming that you are using a computer with UEFI firmware. Do __NOT__ follow this guide if you have a BIOS system! Also you need to have administrator privileges in Windows.

The easiest way is to install Windows before Arch Linux, so the Windows bootloader won't overwrite GRUB later. Also you get a headstart, as Windows will already create an UEFI partition during the installation process.

Keep in mind to create your partition(s) for Arch Linux during the installation process. If you get a PC with Windows preinstalled, you can shrink the C:\ partition and create a new empty partition. A guide can be found [here](https://www.digitaltrends.com/computing/how-to-partition-a-hard-drive-in-windows/).

Always read the entire section before blindly posting any commands. Keep in mind that I'm not responsible for any damage or data loss that may occur with wrong execution..

## Changes in Windows 10

As soon as the Windows 10 installation is complete, boot into Windows.

First of all, we need to disable __Fast Startup__. A guide on how to do this can be found [here](https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html). This will disable hibernation as well.

After this is done, shutdown you PC. Yes, shut it down, a restart won't do it. Then power it on again and acces your UEFI interface. This is done by pressing one of the F-keys (F2 in most cases) on start up. Once your in, disable __Secure Boot__. You can find this setting most times in either the __Seurity__ or __Boot__ tab. 

## Install Arch

Now you are finally ready to install Arch Linux!

Follow the [Arch installation guide](https://wiki.archlinux.org/index.php/Installation_guide) to the point, were you need to install a boot loader. Keep in mind, that you don't need to create an UEFI partition, as Windows already set one up for you.

I will use the GRUB bootloader in this guide, as it is easy to use and works well with windows. Install it and a few extra packages using pacman.

```bash
pacman -S grub efibootmgr os-prober dosfstools intel-ucode
```

_Note: if you are using an AMD processor, install the `amd-ucode` package._

Then, create the __efi-directory__ and mount it.

```bash
mkdir /boot/efi
mount /dev/sda1 /boot/efi
```

_Note: I'm assuming __/dev/sda1__ is you UEFI partition. If it differs, change it accordingly._

Edit __/etc/default/grub__ with Vim or Nano and set `DEFAULT_TIMEOUT=30`. This line will be at the top of the file. This increases the time you have to choose an OS to 30 seconds.

Now, we can install GRUB and create the partition file.

```bash
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub --recheck
grub-mkconfig -o /boot/grub/grub.cfg
```

Thanks to the __os-prober__ package, GRUB detects Windows 10 on its own and adds the accoding entry in the configuration file.

After successfully setting up out boot loader, we can install some more usefull packages. Choose the ones you want.

```bash
pacman -S iw wpa_supplicant dialog networkmanager gvfs ntfs-3g udisks2
```

If you don't know what these do, read up on them on the Arch Wiki before installing them.

At last, exit __Arch-chroot__, umnount your OS partition and reboot.

```bash
exit
umount -R /mnt
reboot
```
Now you have both operating systems working and can choose which to boot at start up!

## References

- [Arch Wiki: Installation guide](https://wiki.archlinux.org/index.php/Installation_guide)
- [Arch Wiki: GRUB](https://wiki.archlinux.org/index.php/GRUB)
- [Arch Wiki: Dual boot with Windows](https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot)
