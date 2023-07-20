<div align="center">

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/M-L-P/grub2-androidx86)](https://github.com/M-L-P/grub2-androidx86/releases/latest)
[![GitHub all releases](https://img.shields.io/github/downloads/M-L-P/grub2-androidx86/total)](https://github.com/M-L-P/grub2-androidx86/releases)
[![GitHub Discussions](https://img.shields.io/github/discussions/M-L-P/grub2-androidx86)](https://github.com/M-L-P/grub2-androidx86/discussions)
[![GitHub Repo stars](https://img.shields.io/github/stars/M-L-P/grub2-androidx86?style=social)](https://github.com/M-L-P/grub2-androidx86/stargazers)

</div>

[English](README.md)|[简体中文](README-自述文件.md)|[繁體中文](README-繁體中文.md)|...
--|--|--|--

<h1 align="center">grub2-androidx86</h1>

這個是用來多啟動各種 Android-x86 的，並且支持設置內核命令行參數。它也許支持安全啟動
#### 文件結構樹狀圖
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/EFI.png"><br/>
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/SRC.png">

-----------------------------------------------------------------------------------------------------------------------------------
## 💻️預覽👀

<details>
<summary>🖱️點擊展開查看🖱️</summary>

### 1024x768
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/繁體中文.gif">

### 1920x1080
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/0-open.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/1-lang.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/2-noti.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/3-k.png">
<img src="https://raw.githubusercontent.com/M-L-P/.github/main/screenshots/grub2-androidx86/繁體中文/4-g.png">
</details>

## 🧭指南⬇️

### 下載
<details>
<summary>🖱️點擊展開查看🖱️</summary>

- 下載 .iso 文件，<br>
[AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)<br/>
[BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)<br/>
[PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)
- 進入 releases 下載,<br>
[Releases](https://github.com/M-L-P/grub2-androidx86/releases)

</details>

### `ext4|f2fs` 和 `SRC`

#### 創建 `ext4|f2fs`
<details>
<summary>🖱️點擊展開查看🖱️</summary>

- 使用 Gnome-Disk 或 Gparted 來創建一個用於安裝的分區, ≥ 8GB；

常見的分區尺寸轉換

物理存儲|符號|邏輯存儲
--|--|--
  8 GB|≈|  7,630 MiB
 16 GB|≈| 15,258 MiB
 32 GB|≈| 30,518 MiB
 64 GB|≈| 61,036 MiB
128 GB|≈|122,070 MiB
256 GB|≈|244,140 MiB
512 GB|≈|488,282 MiB
  1 TB|≈|976,562 MiB

- - 格式化成 ext4 適配於 HDD；
- - 格式化成 f2fs 適配於 SSD；
- - - `sudo {package manager} install f2fs-tools` 用於獲取 f2fs 的支持。

</details>

#### 復製 `SRC`

<details>
<summary>🖱️點擊展開查看🖱️</summary>

- 解壓 `grub2-androidx86-版本號.zip`；
- 復製文件夾 `/[#ext4#f2fs]/Android-x86` 到 `ext4|f2fs` 分區，適用於 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- 復製文件夾 `/[#ext4#f2fs]/BlissOS` 到 `ext4|f2fs` 分區，適用於 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- 復製文件夾 `/[#ext4#f2fs]/PrimeOS` 到 `ext4|f2fs` 分區，適用於 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

#### 復製 system

<details>
<summary>🖱️點擊展開查看🖱️</summary>

- 掛載 .iso 文件；
##### 如果你希望尺寸更小並且只讀，
- 復製虛擬分區文件 `iso: /system.sfs` 或 `iso: /system.efs`，
- - 粘貼到 `ext4|f2fs: /Android-x86` ，適用於 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘貼到 `ext4|f2fs: /BlissOS` ，適用於 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘貼到 `ext4|f2fs: /PrimeOS` ，適用於 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；
##### 如果你希望可寫入，
- 掛載 `iso: /system.sfs` 或 `iso: /system.efs` 並且找到裏面的 `system.img`，
- - - `sudo {package manager} install erofs-utils` 用於獲取 erofs 支持，
- 復製虛擬分區文件 `system.img`,
- - 粘貼到 `ext4|f2fs: /Android-x86` ，適用於 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘貼到 `ext4|f2fs: /BlissOS` ，適用於 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘貼到 `ext4|f2fs: /PrimeOS` ，適用於 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

### 復製到 ESP

#### 復製 `kernel` & `initrd.img`
 
<details>
<summary>🖱️點擊展開查看🖱️</summary>

- 掛載 .iso 文件；
- 復製文件 `iso: /kernel`,
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_AOSP` ，適用於 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_BlissOS` ，適用於 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_PrimeOS` ，適用於 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；
- 復製文件 `iso: /initrd.img`,
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_AOSP` 和 `ext4|f2fs: /Android-x86/boot` ，適用於 [AOSP](https://sourceforge.net/projects/android-x86/files/Release%209.0/)；
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_BlissOS` 和 `ext4|f2fs: /BlissOS/boot` ，適用於 [BlissOS](https://sourceforge.net/projects/blissos-dev/files/Beta/)；
- - 粘貼到 `/[#ESP]/EFI/androidx86/grub/boot_PrimeOS` 和 `ext4|f2fs: /PrimeOS/boot` ，適用於 [PrimeOS](https://sourceforge.net/projects/primeos/files/64-bit/)；

</details>

#### 復製 EFI 文件
- 復製文件夾 `[#ESP]/EFI/androidx86` into `ESP: /EFI`；

## 📝FAQ❓️
### 安全啟動
- 我還沒試過，但可能支持安全啟動，如果你使用 `grub.cer`(安全啟動證書)，
- - `grub.cer`(安全啟動證書) 來自 [Ventoy](https://github.com/ventoy/Ventoy)；
### 無法啟動
- 每次更新的時候，都要手動覆蓋 `kernel`、`initrd.img`和`system`。

## ⭐收藏🌟
如果你喜歡並且期待未來的更新，你可以點亮星星。💫<br/>
告訴你的朋友，你得到了個好東西。

## 🎉來源🎊
- 安全證書來自 [Ventoy](https://github.com/ventoy/Ventoy)；
- 壁紙是通過谷歌搜索到的；
- 通知欄的邊角料是參考 Pixel 的圖形界面的；
- 窗口的邊角料是參考 [BlissOS](https://blissos.org/) 的圖形界面的；
- Terminal box 是改編自 [Termux](https://github.com/termux/termux-app) 的圖形界面的；
- 許多內核命令行參數的信息是摘抄自 [BlissOS Docs](https://docs.blissos.org/configuration/configuration-through-command-line-parameters/)；
- Grub tune 摘抄自 [BreadMaker](https://github.com/BreadMaker) 的 [grub-tune-tester](https://breadmaker.github.io/grub-tune-tester/)；
- [initrd-magisk](https://github.com/HuskyDG/initrd-magisk) 和 [Magisk Delta](https://github.com/HuskyDG/magisk-files) 來自 [阮shìwēi](https://github.com/HuskyDG)；
- 一些代碼來自 .iso 文件的 grub2 配置；
- .gif 的動態截圖是使用 [Screen2Gif](https://github.com/NickeManarin/ScreenToGif) 對 hyper-V 截取的；
...
