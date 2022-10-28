# Magisk Delta

This repo hosts Magisk delta related files

![](https://github.com/topjohnwu/Magisk/raw/master/docs/images/logo.png)

## Introduction

#### **This is not an officially supported [topjohnwu](https://github.com/topjohnwu) project**. 

> If you are looking for official Magisk source, you are in the wrong place, please [go to this page and download Official Magisk](https://github.com/topjohnwu/Magisk)

Yet another crazy custom Magisk by HuskyDG, is always synchronized with official Magisk, including back MagiskHide and some custom features.

## Features
- MagiskHide (does not need Zygisk to be enabled), monitor start up process by logcat (when zygisk is disabled)
- Bootloop Protection: Protect your system from bootloop caused by Magisk modules
- Core-only mode: No modules will load in this mode
- Pre-init mount: Mount files in magiskinit stage, before Android's init is executed
- Custom init.rc: Inject rc script without patching boot image with overlay.d
- System install: Install Magisk into `/system` instead of boot image (for emulator)
- Addon.d fixes when `/data` is not decryptable (Lygisk)
- Tuning F2FS for device with unencrypted data

## Download

> If you are fine with official Magisk setup, it is recommended to stay. If you choose to use Magisk Delta, make sure you read all FAQs and changelog before using Magisk Delta.

### Stable / Beta

> For most user, Stable build is recommended.

#### Stable

- [Magisk 25.2-delta-3](https://huskydg.github.io/download/magisk/25.2-delta.apk)
- [Source code](https://huskydg.github.io/download/magisk/25.2-delta-3.zip)
- [Changelog](https://github.com/HuskyDG/magisk-files/blob/main/note_stable.md)

#### Beta

> Currently same as Stable channel


### Canary / Debug

⚠ Only accept bugreports from Magisk Delta variant.

#### Download

- [Download Canary](https://huskydg.github.io/magisk-files/app-release.apk)
- [Download Debug](https://huskydg.github.io/magisk-files/app-debug.apk)

#### Source code

- [Changelog](https://github.com/HuskyDG/magisk-files/blob/main/note.md)
- [Source code](https://github.com/topjohnwu/Magisk/tree/499eabb8)

## FAQ

### How to switch from current Magisk to Magisk Delta and vice versa?

> Some Mediatek devices prevent boot partition from being modified (or kernel doesn't allow to modify boot image) after booting. When directly installing, you might end up with "/dev/xxxx is read-only" error or the installation seems to be successful but actually fails. In this case, please try patching boot image with Magisk app and flash it from Custom Recovery or Fastboot instead. 

The fast way to migrate to Magisk Delta or switch back to official Magisk: Just flash magisk app like a module.

1. Rename the extension `magisk.apk` to `magisk.zip`
2. Open Magisk app, click "Modules" tab -> "Install from storage" and choose `magisk.zip`
3. Reboot your device

### How do I run magisk on devices with exploit/temporarily root?

- Run your exploit root tool, you shall have root access after exploitation
- Push `magisk.apk` and `busybox` binary to `/data/local/tmp` and run [this script](https://raw.githubusercontent.com/topjohnwu/Magisk/1e6dbad3bbd68bf371511d8f6c1756db0ed61f80/scripts/avd_magisk.sh) with root access

***IMPORTANT! Do not update Magisk through Magisk app when bootloader is still locked or you will brick your device with modified boot image***


### How to install Magisk into emulator (such as NoxPlayer, LDPlayer, etc...)?

> Currently, only Magisk Delta support Magisk installation into system partition. Although emulator has ramdisk image, patching ramdisk is not used because ramdisk is stored in seperate partition with very SMALL disk size that is not enough to store Magisk binaries.

1. Enable Root access in emulator settings
2. Install and open Magisk Delta
3. Grant root access to Magisk Delta, click "Install" under Magisk field and use "Direct Install into system partition" option instead of "Direct Install" option. If you don't see this option, close and re-open Magisk Delta app.
4. Disable Root access in emulator settings.
    *Some emulators delete `su` executable after disabling root access, accidentally remove magisk's `su` so backup and delete `/system/xbin/su` instead.*

### Pass Safetynet / Play Integrity (Device Integrity)

1. Enable Zygisk or install Riru core
2. Enable MagiskHide and install [Safetynet Fix Mod](https://github.com/HuskyDG/safetynet-integrity-fix/releases/latest)
3. Reboot your device

### Why not restore Magisk modules online repo?

The official Magisk modules repository is dead and no longer maintained. Due to that, add them back is meanless. However, [Fox2Code](https://github.com/Fox2Code) has developed [Magisk Modules Manager](https://github.com/Fox2Code/FoxMagiskModuleManager)  app which allows you to download Magisk modules online.

## Donate me

- Paypal: [paypal.me/huskydg](http://paypal.me/huskydg)
- You can now donate me if you want. Remember, I will not make this as a monetization tool and donate is not obligated. Thanks for all your supports and hope you have a good day! 👍


## Other links

- [Internal Documents](./docs/internal-guide.md)
- [Telegram group](https://t.me/magiskdelta)

## License

Our license obviously is the same as [Magisk's license](https://github.com/topjohnwu/Magisk#License)

```
Magisk, including all git submodules are free software:
you can redistribute it and/or modify it under the terms of the
GNU General Public License as published by the Free Software Foundation,
either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```