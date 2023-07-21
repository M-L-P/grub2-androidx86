<div align="center">

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/M-L-P/grub2-androidx86)](https://github.com/M-L-P/grub2-androidx86/releases/latest)
[![GitHub all releases](https://img.shields.io/github/downloads/M-L-P/grub2-androidx86/total)](https://github.com/M-L-P/grub2-androidx86/releases)
[![GitHub Discussions](https://img.shields.io/github/discussions/M-L-P/grub2-androidx86)](https://github.com/M-L-P/grub2-androidx86/discussions)
[![GitHub Repo stars](https://img.shields.io/github/stars/M-L-P/grub2-androidx86?style=social)](https://github.com/M-L-P/grub2-androidx86/stargazers)

</div>

Language|grub2-androidx86|grub2-androidx86-USB
--|--|--
English|[English](README.md)|USB   [English](grub2-androidx86-USB/README.md)
简体中文|[简体中文](README-自述文件.md)|USB   [简体中文](grub2-androidx86-USB/README-自述文件.md)
繁體中文|[繁體中文](README-繁體中文.md)|USB   [繁體中文](grub2-androidx86-USB/README-繁體中文.md)
...|...|USB   ...

<h1 align="center">grub2-androidx86</h1>

这个是用来多启动各种 Android-x86 的，并且支持设置内核命令行参数。它也许支持安全启动
#### 文件结构树状图
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/EFI.png"><br/>
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/SRC.png">

-----------------------------------------------------------------------------------------------------------------------------------
## 💻️预览👀

<details>
<summary>🖱️点击展开查看🖱️</summary>

### 1024x768
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/简体中文.gif">

### 1920x1080
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/0-open.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/1-lang.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/2-noti.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/3-k.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/简体中文/4-g.png">
</details>

## 🧭指南⬇️

### 下载
<details>
<summary>🖱️点击展开查看🖱️</summary>

- 下载 .iso 文件，<br>
[AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)<br/>
[BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)<br/>
[PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)
- 进入 releases 下载,<br>
[Releases](https://github.com/M-L-P/grub2-androidx86/releases)

</details>

### `ext4|f2fs` 和 `SRC`

#### 创建 `ext4|f2fs`
<details>
<summary>🖱️点击展开查看🖱️</summary>

- 使用 Gnome-Disk 或 Gparted 来创建一个用于安装的分区, ≥ 8GB；

常见的分区尺寸转换

物理存储|符号|逻辑存储
--|--|--
  8 GB|≈|  7,630 MiB
 16 GB|≈| 15,258 MiB
 32 GB|≈| 30,518 MiB
 64 GB|≈| 61,036 MiB
128 GB|≈|122,070 MiB
256 GB|≈|244,140 MiB
512 GB|≈|488,282 MiB
  1 TB|≈|976,562 MiB

- - 格式化成 ext4 适配于 HDD；
- - 格式化成 f2fs 适配于 SSD；
- - - `sudo {package manager} install f2fs-tools` 用于获取 f2fs 的支持。

</details>

#### 复制 `SRC`

<details>
<summary>🖱️点击展开查看🖱️</summary>

- 解压 `grub2-androidx86-版本号.zip`；
- 复制文件夹 `/[#ext4#f2fs]/Android-x86` 到 `ext4|f2fs` 分区，适用于 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- 复制文件夹 `/[#ext4#f2fs]/BlissOS` 到 `ext4|f2fs` 分区，适用于 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- 复制文件夹 `/[#ext4#f2fs]/PrimeOS` 到 `ext4|f2fs` 分区，适用于 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

#### 复制 system

<details>
<summary>🖱️点击展开查看🖱️</summary>

- 挂载 .iso 文件；
##### 如果你希望尺寸更小并且只读，
- 复制虚拟分区文件 `iso: /system.sfs` 或 `iso: /system.efs`，
- - 粘贴到 `ext4|f2fs: /Android-x86` ，适用于 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘贴到 `ext4|f2fs: /BlissOS` ，适用于 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘贴到 `ext4|f2fs: /PrimeOS` ，适用于 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；
##### 如果你希望可写入，
- 挂载 `iso: /system.sfs` 或 `iso: /system.efs` 并且找到里面的 `system.img`，
- - - `sudo {package manager} install erofs-utils` 用于获取 erofs 支持，
- 复制虚拟分区文件 `system.img`,
- - 粘贴到 `ext4|f2fs: /Android-x86` ，适用于 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘贴到 `ext4|f2fs: /BlissOS` ，适用于 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘贴到 `ext4|f2fs: /PrimeOS` ，适用于 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

### 复制到 ESP

#### 复制 `kernel` & `initrd.img`
 
<details>
<summary>🖱️点击展开查看🖱️</summary>

- 挂载 .iso 文件；
- 复制文件 `iso: /kernel`,
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_AOSP` ，适用于 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_BlissOS` ，适用于 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_PrimeOS` ，适用于 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；
- 复制文件 `iso: /initrd.img`,
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_AOSP` 和 `ext4|f2fs: /Android-x86/boot` ，适用于 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_BlissOS` 和 `ext4|f2fs: /BlissOS/boot` ，适用于 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘贴到 `/[#ESP]/EFI/androidx86/boot_PrimeOS` 和 `ext4|f2fs: /PrimeOS/boot` ，适用于 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

#### 复制 EFI 文件
- 复制文件夹 `[#ESP]/EFI/androidx86` into `ESP: /EFI`；

## 📝FAQ❓️
### 安全启动
- 我还没试过，但可能支持安全启动，如果你使用 `grub.cer`(安全启动证书)，
- - `grub.cer`(安全启动证书) 来自 [Ventoy](https://github.com/ventoy/Ventoy)；
### 无法启动
- 每次更新的时候，都要手动覆盖 `kernel`、`initrd.img`和`system`。

## ⭐收藏🌟
如果你喜欢并且期待未来的更新，你可以点亮星星。💫<br/>
告诉你的朋友，你得到了个好东西。

## 🎉来源🎊
- 安全证书来自 [Ventoy](https://github.com/ventoy/Ventoy)；
- 壁纸是通过谷歌搜索到的；
- 通知栏的边角料是参考 Pixel 的图形界面的；
- 窗口的边角料是参考 [BlissOS](https://blissos.org/) 的图形界面的；
- Terminal box 是改编自 [Termux](https://github.com/termux/termux-app) 的图形界面的；
- 许多内核命令行参数的信息是摘抄自 [BlissOS Docs](https://docs.blissos.org/configuration/configuration-through-command-line-parameters/)；
- Grub tune 摘抄自 [BreadMaker](https://github.com/BreadMaker) 的 [grub-tune-tester](https://breadmaker.github.io/grub-tune-tester/)；
- [initrd-magisk](https://github.com/HuskyDG/initrd-magisk) 和 [Magisk Delta](https://github.com/HuskyDG/magisk-files) 来自 [阮shìwēi](https://github.com/HuskyDG)；
- 一些代码来自 .iso 文件的 grub2 配置；
- .gif 的动态截图是使用 [Screen2Gif](https://github.com/NickeManarin/ScreenToGif) 对 hyper-V 截取的；
- ……
