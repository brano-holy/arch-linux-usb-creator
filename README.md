Arch Linux USB Creator
======================

arch-linux-usb-creator
----------------------

Helper script for creating USB Flash Installation Media with Arch Linux.

The script is creating installation USB according to [https://wiki.archlinux.org/index.php/Install\_from\_a\_USB\_flash\_drive#Using\_manual\_formatting](https://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive#Using_manual_formatting).

Before using this script, make sure:

* the latest *syslinux* package (version 6.02 or newer) is installed on the system,
* the USB has a MBR (msdos) partition table,
* the USB partition has a FAT32 filesystem,
* the USB partition is not mounted.

Usage
-----

`./arch-linux-usb-creator <path-to-arch-linux-iso> <device-partition>`

Example
-------

`./arch-linux-usb-creator ~/Downloads/archlinux-2014.03.01-dual.iso /dev/sdb1`
