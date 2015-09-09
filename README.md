Arch Linux USB Creator
======================

archlinux-usb-creator
----------------------
*An unofficial helper script for creating a USB Flash Installation Media with 
Arch Linux.*

`archlinux-usb-creator` creates an installation USB according to 
[https://wiki.archlinux.org/index.php/Install\_from\_a\_USB\_flash\_drive#Using\_manual\_formatting](https://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive#Using_manual_formatting).

Download
--------
You can download `archlinux-usb-creator` from GitHub using the following 
`git clone` command:
```bash
$ git clone https://github.com/branoholy/archlinux-usb-creator.git
$ cd archlinux-usb-creator
```

Or an archive with the following `wget` command:
```bash
$ wget https://github.com/branoholy/archlinux-usb-creator/archive/master.tar.gz -O aluc.tar.gz
$ tar -xf aluc.tar.gz
$ cd archlinux-usb-creator-master
```

Or with this short URL (useful when you have to type the URL manually):
```bash
$ wget http://git.io/KAKgAQ -O aluc.tar.gz
$ tar -xf aluc.tar.gz
$ cd archlinux-usb-creator-master
```

Usage
-----
Run `archlinux-usb-creator` as a root user.

```bash
$ ./archlinux-usb-creator <device-partition> [<path-to-archlinux-iso>]
```

Omitting the `<path-to-archlinux-iso>` option will download the latest Arch 
Linux ISO from a specified mirror (see the [Config](#config) section) and check 
`sha1sum` after download.

The `<path-to-archlinux-iso>` option can be also used to specify a directory 
where the ISO will be downloaded (default is `/tmp`).

The downloaded ISO will be deleted automatically.

### Config
Change the `mirror` variable in the config file (`config.conf`) to the closest 
server from [https://www.archlinux.org/mirrors/status/](https://www.archlinux.org/mirrors/status/) 
(use the *Mirror URL* column) if you want to download the latest ISO image.

If you do not have installed the latest `syslinux` package, you can download it 
from [Arch Linux Package Database](https://www.archlinux.org/packages/?repo=Core&q=syslinux). 
Choose your architecture and click on the *Download From Mirror* link. After 
downloading and unpacking, change the `syslinux` variable to the `bios` folder 
containing `*.c32` files and the `extlinux` variable to the `extlinux` binary.

Dependencies
------------
Before using `archlinux-usb-creator`, make sure:

* the latest `syslinux` package (version 6.02 or newer) is installed 
  on the system (see the [Config](#config) section for more details),
* the USB device has a MBR (msdos) partition table,
* the USB partition has a FAT32 filesystem,
* the USB partition is **not** mounted (you can use `lsblk` to check it).

Build
-----
There is no need to build `archlinux-usb-creator` because it's only a shell 
script.

Examples
--------
Use the latest image (download it):
```bash
$ ./archlinux-usb-creator /dev/sdb1
```

Use the latest image (download it) and use `~/Downloads` instead of `/tmp` 
where the ISO will be downloaded:
```bash
$ ./archlinux-usb-creator /dev/sdb1 ~/Downloads
```

Use a previously downloaded image:
```bash
$ ./archlinux-usb-creator /dev/sdb1 ~/Downloads/archlinux-2014.03.01-dual.iso
```

License
-------
Arch Linux USB Creator is licensed under GNU GPL v3 (see 
[COPYING](https://github.com/branoholy/archlinux-usb-creator/blob/master/COPYING) 
file).

