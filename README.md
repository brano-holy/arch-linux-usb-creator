# Arch Linux USB Creator

*An unofficial helper script for creating a USB Flash Installation Media with
Arch Linux.*

`archlinux-usb-creator` creates an installation USB according to
[https://wiki.archlinux.org/index.php/Install\_from\_a\_USB\_flash\_drive#Using\_manual\_formatting](https://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive#Using_manual_formatting).

## Download
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
$ wget https://git.io/KAKgAQ -O aluc.tar.gz
$ tar -xf aluc.tar.gz
$ cd archlinux-usb-creator-master
```

## Usage
Run `archlinux-usb-creator` as a root user.

```bash
$ ./archlinux-usb-creator <device-partition> [-p <path>] [-m <url>] [-h]
```

### Options
* `-p`, `--path`: Path to Arch Linux ISO. If omitted, the latest Arch Linux ISO
  from the specified mirror will be downloaded and `sha1sum` will be checked
  after download (the downloaded ISO will be deleted automatically). If
  specified, it can be a path to the ISO to use or a directory where the ISO
  will be downloaded.

  Default: `/tmp`
* `-m`, `--mirror`: URL of Arch Linux mirror. It has to be specified if you want
  to download the latest ISO image. Use URL of the closest server from
  https://www.archlinux.org/mirrors/status/ (use the *Mirror URL* column).

  Default: `mirror` from `aluc.conf`
* `-h`, `--help`: Print the help.
* `-v`, `--version`: Print the version number.

### Config (aluc.conf)
* `mirror`: The default mirror URL if the `--mirror` option is omitted.
* `syslinux`: If you do not have installed the latest `syslinux` package, you
  can download it from [Arch Linux Package Database](https://www.archlinux.org/packages/core/x86_64/syslinux/download/).
  After downloading and unpacking, change the `syslinux` variable to the `bios`
  folder containing `*.c32` files.
* `extlinux`: If you downloaded the `syslinux` package, change the `extlinux`
  variable to the path to the `extlinux` binary.

## Dependencies
Before using `archlinux-usb-creator`, make sure:

* the latest `syslinux` package (version 6.03 or newer) is installed in the
  system (see the [Config](#config) section for more details),
* the USB device has a MBR (msdos) partition table,
* the USB partition has a FAT32 filesystem,
* the USB partition is **not** mounted (you can use `lsblk` to check it).

## Build
There is no need to build `archlinux-usb-creator` because it's only a shell
script.

## Examples
Download the latest image from the mirror to `/tmp`:
```bash
$ ./archlinux-usb-creator /dev/sdb1 -m https://mirror.dkm.cz/archlinux/
```

Download the latest image to `/tmp` (the mirror is taken from `aluc.conf`):
```bash
$ ./archlinux-usb-creator /dev/sdb1
```

Download the latest image to `~/Downloads` (the mirror is taken from `aluc.conf`):
```bash
$ ./archlinux-usb-creator /dev/sdb1 -p ~/Downloads
```

Use a previously downloaded image:
```bash
$ ./archlinux-usb-creator /dev/sdb1 -p /tmp/archlinux-2018.03.01-x86_64.iso
```

## License
Arch Linux USB Creator is licensed under GNU GPL v3 (see the
[LICENSE](https://github.com/branoholy/archlinux-usb-creator/blob/master/LICENSE)
file).
