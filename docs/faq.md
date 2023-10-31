## FAQ

### How do I install Magisk Delta from scratch?

- Process like installing Magisk: <https://topjohnwu.github.io/Magisk/install.html>

### How do I switch from the current Magisk to Magisk Delta and vice versa?

Just do it like when you update Magisk!

#### Direct Install (Recommended)

1. Install, open, and then grant root access to Magisk Delta.
2. Inside **Magisk**, tap "Install" and then "Direct Install". If you don't see this, try restarting the app.

#### Just flash Magisk Delta from the current Magisk app

1. Rename the extension `magisk.apk` to `magisk.zip`
2. Open Magisk app, click the "Modules" tab -> "Install from storage" and choose `magisk.zip`

#### Install Magisk directly to `/system` (Not recommended)

> Please only use this method on ROMs with Permissive SELinux mode or Enforcing SELinux with permissive "u:r:su:s0" context in sepolicy rules such as user-debug ROMs like LineageOS. You should have a backup of your ROM in case the system can't boot, and do not use broken Custom Recovery. Your ROM must be able to mount read-write, and your kernel must support dynamic SeLinux rules patch. Process this method at your own risk!

For some reasons, you don't want to install Magisk in the regular way (patch boot image); you can install Magisk directly to `/system`.

1. Restore to the stock boot image if you already have Magisk installed.
2. Boot to recovery, rename `magisk.apk` to `systemmagisk.zip`, and flash it.
3. If you want to update Magisk, please use **Direct Install into system partition** instead of **Direct Install**.

### How to install Magisk into an Android-x86 project or Android emulator

#### Before start

1. Only Magisk Delta supports Magisk installation on system partitions.
2. Although the emulator has a ramdisk image, patching ramdisk is not used because ramdisk is stored in a separate partition with a very SMALL disk size that is not enough to store Magisk binaries.
3. The latest Magisk Delta Canary has been adopted to support Bluestacks, ~~but need [app_process wrapper](https://github.com/HuskyDG/app_process_wrapper/releases) to run Zygisk.~~
4. Lists of emulators have been tested: **NoxPlayer**, **LDPlayer**, and **MEmu**.
5. Lists of Android x86 projects have been tested: **BlissOS**, **PrimeOS**
6. Waydroid is supported on the Canary build.

#### Step-by-step to install Magisk into an emulator like NoxPlayer, LDPlayer, MemuPlayer, etc

1. Enable Root access in emulator settings.
2. Install and open Magisk Delta.
3. Grant root access to Magisk Delta, click "Install" under the Magisk field, and use "Direct Install into system partition" option instead of "Direct Install" option. (If you don't see this option, close and re-open Magisk Delta app.) Don't restart now!
4. ~~Disable Root access in emulator settings.~~ Backup built-in `su` (`/system/bin/su` and `/system/xbin/su`) and delete them (in case you want to uninstall Magisk and restore to built-in `su`), then reboot. Because emulators like LDPlayer will remove all su after disabling ROOT from settings, **DO NOT** disable Root access in emulator settings.
5. Enjoy Magisk!

#### Step-by-step instructions for installing Magisk on Bluestacks

1. Download Bluestacks Tweaker [here](https://bstweaker.tk/).
2. Use Bluestacks Tweaker and click "Unlock" to unlock Bluestacks instance, and then launch it. Otherwise, you can't install Magisk.
3. When the instance starts up successfully, click "Patch" to open root access, install Magisk Delta, and execute the "Direct Install into system partition" action.
4. When you are done, click "UnPatch" and then restart the instance.
5. Enjoy Magisk!

#### Step-by-step to install Magisk into an Android-x86 project

- You can use [initrd-magisk](https://github.com/HuskyDG/initrd-magisk) or directly install Magisk into the system partition, like in the guide above.

#### Step-by-step instructions for installing Magisk on Waydroid

- Please check <https://github.com/nitanmarcel/waydroid-magisk> or <https://github.com/casualsnek/waydroid_script> for more information.

### After enabling MagiskHide, why are my apps and games still getting detected by the emulator?

MagiskHide is not an emulator-detection bypass.

### How do I manually trigger Core-only mode from Recovery?

Create an empty file named `.disable_magisk` in these locations: `/cache`, `/persist`, or `/metadata`

### Why not restore Magisk modules online repo?

The official Magisk module repository is dead and no longer maintained. Due to that, adding them back is meaningless. However, [Fox2Code](https://github.com/Fox2Code) has developed [Magisk Module Manager](https://github.com/Fox2Code/FoxMagiskModuleManager) app, which allows you to download Magisk modules online.
> It has been archived as of May 4, 2023. The new repo has since been adapted by [Androidacy](https://github.com/Androidacy/MagiskModuleManager)

### Should I install Shxxxxo module to hide root?

- It is not recommended; you should uninstall it. If not, don't complain about crashing. MagiskHide should be enough.
- If you really want to use Shxxxxo, then uninstall Magisk Delta and use Official Magisk ¯\_(ツ)_/¯

### Why are some modules broken after enabling SuList?

SuList means MagiskSU and modules are not mounted by default; only those apps in the list will have Magisk mounted, so the functionality of the modules is not fully supported because most of them must be mounted in all apps, which is equivalent to being detected. For more information about SuList, please [read this](./internal-guide.html#magiskhide-sulist)
