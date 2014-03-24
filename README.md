Arch Linux USB Creator
======================

arch-linux-usb-creator
----------------------
*Unofficial helper script for creating USB Flash Installation Media with Arch Linux.*

`arch-linux-usb-creator` creates installation USB according to [https://wiki.archlinux.org/index.php/Install\_from\_a\_USB\_flash\_drive#Using\_manual\_formatting](https://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive#Using_manual_formatting).

Before using `arch-linux-usb-creator`, make sure:

* the latest `syslinux` package (version 6.02 or newer) is installed 
  on the system,
* the USB device has a MBR (msdos) partition table,
* the USB partition has a FAT32 filesystem,
* the USB partition is **not** mounted (you can use `lsblk` to check it).

Download
--------
You can download `arch-linux-usb-creator` from GitHub using `git clone` command:
```bash
$ git clone https://github.com/brano-holy/arch-linux-usb-creator.git
$ cd arch-linux-usb-creator
```

Or archive with `wget` command:
```bash
$ wget https://github.com/brano-holy/arch-linux-usb-creator/archive/master.tar.gz -O aluc.tar.gz
$ tar -xf aluc.tar.gz
$ cd arch-linux-usb-creator-master
```

Or with this short URL:
```bash
$ wget http://git.io/PzxJTg -O aluc.tar.gz
$ tar -xf aluc.tar.gz
$ cd arch-linux-usb-creator-master
```

Build
-----
There is no need to build `arch-linux-usb-creator` because it's only shell script.

Usage
-----
Before first use, change `mirror` variable in `mirrors.conf` to the closest 
server from 
[https://www.archlinux.org/mirrors/status/](https://www.archlinux.org/mirrors/status/) 
(use *Mirror URL* column).

Run `arch-linux-usb-creator` as root user.

```bash
$ ./arch-linux-usb-creator <device-partition> [<path-to-arch-linux-iso>]
```

Omitting `<path-to-arch-linux-iso>` option will download the latest Arch Linux ISO 
from specified mirror and check `sha1sum` after download.

`<path-to-arch-linux-iso>` option can be also used to specify directory where 
the ISO will be downloaded (default is `/tmp`).

Downloaded ISO will be deleted automatically.

Examples
--------
Use the latest image (download it):
```bash
$ ./arch-linux-usb-creator /dev/sdb1
```

Use the latest image (download it) and use `~/Downloads` instead of `/tmp` 
where the ISO will be downloaded:
```bash
$ ./arch-linux-usb-creator /dev/sdb1 ~/Downloads
```

Use previously downloaded image:
```bash
$ ./arch-linux-usb-creator /dev/sdb1 ~/Downloads/archlinux-2014.03.01-dual.iso
```

License
-------
Arch Linux USB Creator is licensed under GNU GPL v3 (see 
[COPYING](https://github.com/brano-holy/arch-linux-usb-creator/blob/master/COPYING) 
file).
