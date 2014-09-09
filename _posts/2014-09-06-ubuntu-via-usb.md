---
layout: post
title:  "Ubuntu via USB"
date:   2014-09-06 19:34:31
---

I find [OS X][] to be the most enjoyable and productive desktop operating system available.
Unfortunately my employer [PwC][] provides me with a [Lenovo][].
This machine precludes me from using OS X and subjects me to both Windows and corporate data security policies.

[OS X]: https://www.apple.com/osx
[PwC]: http://pwc.com.au
[Lenovo]: http://shop.lenovo.com/il/en/laptops/thinkpad/t-series/t440s

Rather than living within these constraints I prefer to maintain an alternate operating system for personal use.
This gives me freedom without the inconvenience of maintaining and carrying two laptops.

I use [Ubuntu][] via a bootable encrypted USB flash drive.
This keeps my personal data physically separated from the laptop's hard drive, work-life balance made manifest.
It also makes the laptop feel disposable which I like.

[Ubuntu]: http://www.ubuntu.com/desktop

I don't recommend that you try this.
Your wants and needs will almost certainly be better met by [iOS][] or OS X.
However, if your hardware choices are constrained this is far more liberating than using someone else's Windows.

[iOS]: https://www.apple.com/ios

## Hardware required

1. A USB drive to temporarily store the Ubuntu installer (1 GB or greater).
2. A USB drive to install Ubuntu (as large as you can obtain).

For a large USB drive I bought a 64 GB [SanDisk Ultra Fit][] flash drive.
Physically it's only marginally bigger than the plug which means I can comfortably leave it plugged in continually.
This is key to giving the illusion that I am using my own laptop rather than a laptop with my own peripheral.

[SanDisk Ultra Fit]: http://www.sandisk.com/products/usb/drives/ultra-fit3

After a lifetime of hand-me-down PCs, hulking towers for gaming and loaned ThinkPads I find it remarkable that a drive the size of my thumbnail can be the only desktop hardware that I need to own.

## Create a bootable USB drive

You should only need to use this once.

1. Download [Ubuntu Desktop][].
2. Download [Pen Drive Linux's Universal USB Installer][].
3. Select `Ubuntu` from the dropdown list.
4. Browse to and select the file downloaded in step 1.
5. Select your USB drive.
6. Select the checkbox that formats your USB drive.
7. Create.

[Ubuntu Desktop]: http://www.ubuntu.com/download/desktop
[Pen Drive Linux's Universal USB Installer]: http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3

## Install Ubuntu

You can configure Ubuntu to use multiple encrypted logical volumes.
Having multiple logical volumes allows you to reinstall the operating system without migrating `/home` and to fill up `/home` with minimal consequence.
Encrypting your data is always a good idea but particularly when your data is on something as losable as a tiny USB flash drive.

1. Select your preferred language.
2. Select installation type `something else`.
3. Remove any partitions under your target USB drive.
4. Select the `free space` under your target USB drive and create a new `primary` partition at the `beginning of this space` to be used as an `Ext4 journaling file system` with a mount point of `/boot` (I used 250 MB).
This is required to support encrypted logical volumes.
5. Select the `free space` under your target USB drive and create a new `logical` partition at the `beginning of this space` as a `physical volume for encryption` (I used 8000 MB).
6. Change the mount point of the Linux device-mapper of this partition to `/`.
7. Select the `free space` under your target USB drive and create a new `logical` partition at the `beginning of this space` as a `physical volume for encryption` (I used all that remained but 2000 MB).
8. Change the mount point of the Linux device-mapper of this partition to /home.
9. Select the `free space` under your target USB drive and create a new `logical` partition at the `end of this space` as a `physical volume for encryption` (I used 2000 MB).
10. Change the Linux device-mapper of this partition to use this as `swap area`.
11. Select your target USB drive to be the device for boot loader installation.
12. Complete the remaining steps to your preference.
