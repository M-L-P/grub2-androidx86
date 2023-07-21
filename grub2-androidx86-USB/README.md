<div align="center">

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/M-L-P/grub2-androidx86-USB)](https://github.com/M-L-P/grub2-androidx86-USB/releases/latest)
[![GitHub all releases](https://img.shields.io/github/downloads/M-L-P/grub2-androidx86-USB/total)](https://github.com/M-L-P/grub2-androidx86-USB/releases)
[![GitHub Discussions](https://img.shields.io/github/discussions/M-L-P/grub2-androidx86-USB)](https://github.com/M-L-P/grub2-androidx86-USB/discussions)
[![GitHub Repo stars](https://img.shields.io/github/stars/M-L-P/grub2-androidx86-USB?style=social)](https://github.com/M-L-P/grub2-androidx86-USB/stargazers)

</div>

[English](README.md)|[简体中文](README-自述文件.md)|[繁體中文](README-繁體中文.md)|...
--|--|--|--

<h1 align="center">grub2-androidx86-USB</h1>

grub2-androidx86 for USB. It is used for USB-HDD, USB-SSD or USB flash disk.
#### File Tree
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/EFI-USB.png"><br/>
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/SRC-USB.png">

-----------------------------------------------------------------------------------------------------------------------------------
## 💻️Preview👀

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

### 1024x768
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/English.gif">

### 1920x1080
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/0-open.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/1-lang.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/2-noti.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/3-k.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/English/4-g.png">
</details>

## 🧭Guide⬇️

### Download
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- Download the .iso file,<br>
[AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)<br/>
[BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)<br/>
[PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)
- Download from releases,<br>
[Releases](https://github.com/M-L-P/grub2-androidx86/releases)

</details>

### `ext4|f2fs` and `SRC`

#### Create `ext4|f2fs`
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- Use Gnome-Disk or Gparted to create a partition for installation, ≥ 8GB；

Common partition size conversions

Physical Storage|Character|Logical Storage
--|--|--
  8 GB|≈|  7,630 MiB
 16 GB|≈| 15,258 MiB
 32 GB|≈| 30,518 MiB
 64 GB|≈| 61,036 MiB
128 GB|≈|122,070 MiB
256 GB|≈|244,140 MiB
512 GB|≈|488,282 MiB
  1 TB|≈|976,562 MiB

- - format it as ext4 for HDD;
- - format it as f2fs for SSD;
- - - `sudo {package manager} install f2fs-tools` in order to support f2fs.

</details>

#### Copy `SRC`

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- Unzip `grub2-androidx86-USB-version.zip`;
- Copy the folder `/[#ext4#f2fs]-USB/USB-Android-x86` into the `ext4|f2fs` partition for [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/);
- Copy the folder `/[#ext4#f2fs]-USB/USB-BlissOS` into the `ext4|f2fs` partition for [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/);
- Copy the folder `/[#ext4#f2fs]-USB/USB-PrimeOS` into the `ext4|f2fs` partition for [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/);

</details>

#### Copy system

<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- Mount the .iso file;
##### If you want smaller size and Read-Only,
- Copy the virtual partition `iso: /system.sfs` or `iso: /system.efs`,
- - and paste into `ext4|f2fs: /USB-Android-x86` for [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/);
- - and paste into into `ext4|f2fs: /USB-BlissOS` for [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/);
- - and paste into `ext4|f2fs: /USB-PrimeOS` for [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/);
##### If you want it writable,
- Mount `iso: /system.sfs` or `iso: /system.efs` and find `system.img` in it,
- - - `sudo {package manager} install erofs-utils` in order to support erofs,
- Copy the virtual partition `system.img`,
- - and paste into `ext4|f2fs: /USB-Android-x86` for [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/);
- - and paste into `ext4|f2fs: /USB-BlissOS` for [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/);
- - and paste into `ext4|f2fs: /USB-PrimeOS` for [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/);

</details>

### Copy into ESP

#### Copy `kernel` & `initrd.img`
 
<details>
<summary>🖱️Click to Unfold to see🖱️</summary>

- Mount the .iso file;
- Copy the file `iso: /kernel`,
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_AOSP` for [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/);
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_BlissOS` for [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/);
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_PrimeOS` for [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/);
- Copy the `iso: /initrd.img`,
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_AOSP` and `ext4|f2fs: /USB-Android-x86/boot` for [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/);
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_BlissOS` and `ext4|f2fs: /USB-BlissOS/boot` for [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/);
- - and paste into `/[#ESP]-USB/EFI/androidx86-USB/boot_PrimeOS` and `ext4|f2fs: /USB-PrimeOS/boot` for [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/);

</details>

#### Copy EFI files
- Copy the folder `[#ESP]-USB/EFI/androidx86-USB` into `ESP: /EFI`;

## 📝FAQ❓️
### Secure Boot
- It might support secure boot if you use `grub.cer`(Secure Boot Certificate), which is what I haven't tried,
- - `grub.cer`(Secure Boot Certificate) is from [Ventoy](https://github.com/ventoy/Ventoy);
### Cannot boot
- You should cover `kernel`, `initrd.img`and `system` by your hands once you get a newer .iso file.

## ⭐Star🌟
If you like it and are looking forward to the coming update, you can star it.💫<br/>
Tell your friends that you have got a good stuff.

## 🎉Credit🎊
- Secure Boot Certificate comes from [Ventoy](https://github.com/ventoy/Ventoy);
- Wallpapers are searched by using Google;
- The leftover materials of the noti are drawn with reference to the graphical interface of Pixel;
- The leftover materials of the window are drawn with reference to the graphical interface of [BlissOS](https://blissos.org/);
- Terminal box is adapted from the graphical interface of [Termux](https://github.com/termux/termux-app);
- Many things about Kernel Command Line Parameters are copied from [BlissOS Docs](https://docs.blissos.org/configuration/configuration-through-command-line-parameters/);
- Grub tune is copied from [grub-tune-tester](https://breadmaker.github.io/grub-tune-tester/) of [BreadMaker](https://github.com/BreadMaker);
- [initrd-magisk](https://github.com/HuskyDG/initrd-magisk) and [Magisk Delta](https://github.com/HuskyDG/magisk-files) of [shìwēi nguyen](https://github.com/HuskyDG);
- Some codes are adapted from the grub2 of their .iso files;
- The .gif cartoon is taken by using Hyper-V and [Screen2Gif](https://github.com/NickeManarin/ScreenToGif);
- ...
