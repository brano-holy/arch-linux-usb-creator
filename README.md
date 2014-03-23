Arch Linux USB Creator
======================

arch-linux-usb-creator
----------------------
*Unofficial helper script for creating USB Flash Installation Media with Arch Linux.*

`arch-linux-usb-creator` creates installation USB according to [https://wiki.archlinux.org/index.php/Install\_from\_a\_USB\_flash\_drive#Using\_manual\_formatting](https://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive#Using_manual_formatting).

Before using `arch-linux-usb-creator`, make sure:

* the latest `syslinux` package (version 6.02 or newer) is installed 
  on the system,
* the USB has a MBR (msdos) partition table,
* the USB partition has a FAT32 filesystem,
* the USB partition is **not** mounted.

Download
--------
Because `arch-linux-usb-creator` is only shell script, there is no need to 
compile.

You can download `arch-linux-usb-creator` directly from GitHub:
```bash
$ wget https://raw.github.com/brano-holy/arch-linux-usb-creator/master/arch-linux-usb-creator
$ chmod +x arch-linux-usb-creator
```

Or with this short URL:
```bash
$ wget http://git.io/84IWDg -O arch-linux-usb-creator
$ chmod +x arch-linux-usb-creator
```

Or using `git clone` command:
```bash
$ git clone https://github.com/brano-holy/arch-linux-usb-creator.git
$ cd arch-linux-usb-creator
```

Usage
-----
Before first use, change `mirror` variable to the closest server from 
[http://www.archlinux.org/download/](http://www.archlinux.org/download/) (it 
should be path to folder which contains *archlinux* folder).

Run `arch-linux-usb-creator` as root user.

```bash
$ ./arch-linux-usb-creator <device-partition> [<path-to-arch-linux-iso>]
```

Omiting `<path-to-arch-linux-iso>` option will download the latest Arch Linux ISO 
from specified mirror and check `sha1sum` after download.

Examples
--------
Use the latest image:
```bash
$ ./arch-linux-usb-creator /dev/sdb1
```

Use previously downloaded image:
```bash
$ ./arch-linux-usb-creator /dev/sdb1 ~/Downloads/archlinux-2014.03.01-dual.iso
```

License
-------
Arch Linux USB Creator is licensed under GNU GPL v3 (see COPYING file).
