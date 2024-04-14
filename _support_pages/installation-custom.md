---
title: Manually Installing carbonOS
description: Guide on how to manually install carbonOS from the command line, which allows for dual-boot and other advanced setups
os_version: "2022.1"
---

Manually installing carbonOS from the command line gives you complete control
over the parition layout of the system, and other install-time settings.
This is useful, for instance, if you'd like to dual-boot
carbonOS with another system, or if you'd like to use a different filesystem
type. Please keep in mind, however, that only the default partition layout
created by carbonOS's basic installer is officially supported.

1. Download the [ISO Image](/download)
2. Write the ISO to a USB flash drive, using `dd`, [balenaEtcher](https://www.balena.io/etcher/), or similar software
3. Boot your machine into the EFI firmware. Disable secure boot, and
ensure that your USB drive has priority in the boot order
4. Boot your machine from the USB drive. 
5. Select "Try or Install carbonOS" from the menu. You can select the ramdisk
alternative if necessary (i.e. you want to remove the USB drive during
installation), but I don't recommend using the ramdisk unless you have at least
8GB of RAM.
6. Once the system boots, follow the on-screen instructions until it asks you
whether you want to try or install the OS. Select "Try"
7. In the LiveOS session, bring up a terminal. You'll need to use `pkexec` to
give yourself root privilages
7. Create & format your partitions/filesystems however you wish. carbonOS 2022.1
requires that the partition label of the root partition is `carbon-root`. This
will change in future versions of the OS.
8. Mount the partitions. I suggest doing this in `/mnt`
9. Run `updatectl init-os --sysroot=/path/to/mounted/sysroot /sysroot`. This
will copy carbonOS's system files into your partition layout.
10. Unless your partitions follow the 
[Discoverable Partitions Spec](https://systemd.io/DISCOVERABLE_PARTITIONS/),
you'll need to create an `/etc/fstab` file. Once you create and appropriately
populate this file, you'll need to copy it into
`/path/to/mounted/sysroot/ostree/deploy/carbonOS/deploy/*/etc/`, which will
become `/etc` once you boot into your new installation of carbonOS
11. Install the bootloader by running `bootctl install`. If you'd like to use
a custom bootloader, it will need to be compatible with the 
[Boot Loader Spec](https://systemd.io/BOOT_LOADER_SPECIFICATION/)
12. Reboot. carbonOS should now be installed

