# Lenovo-ThinkCentre-M73-Tiny-Hackintosh

[联想 M73](https://www.lenovo.com/us/en/desktops/thinkcentre/m-series-tiny/m73/) 的黑苹果 EFI，使用 [OpenCore](https://github.com/acidanthera/OpenCorePkg) 引导。

- OpenCore - [v0.6.3](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.6.3) (2020-11)
- MacOS - macOS Catalina 10.15.7 (19H15)

M73 型号：10AX；硬件规格：

组件 | 型号
---|---
CPU | Intel i3-4170 (Haswell 平台)
显卡 | Intel HD Graphics 4400
声卡 | Realtek ALC283 (Codec = 1)
有线网卡 | Intel I217-V
无线网卡 | 内置的 MiniPCIE 接口无线网卡 BCM943224HMP
蓝牙适配器 | 普通的 USB 接口蓝牙适配器，芯片为 CSR8510A10

正常驱动

- 有线网卡
- 无线网卡
- 蓝牙
- 声卡
- 显卡
- USB 3.0
- 睡眠

不能工作

- VGA 视频输出
- 隔空传送
- 接力

## 使用教程

1. 使用 [gibMacOS](https://github.com/corpnewt/gibMacOS) 下载镜像，烧录 Mac 安装 U 盘
2. 拷贝此 EFI 到 Boot 分区，用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 更换序列号（型号选：iMac 14,4）
3. 根据官网说明修改主机 [BIOS 设置](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#intel-bios-settings)
4. U 盘启动安装（大约 1 小时）
5. 安装完成后可以用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 挂载 EFI 分区，拷贝 U 盘 EFI 到主机启动 EFI 分区

## 配置过程

基本参考 [官网说明](https://dortania.github.io/OpenCore-Install-Guide/) 安装

### 相关工具

- 7zip
- Python
- [gibMacOS](https://github.com/corpnewt/gibMacOS) - 下载 MacOS 镜像
  - 如果下载失败，想办法把 [ddrelease64.exe](http://www.chrysocome.net/downloads/ddrelease64.exe) 和 [booticex64.exe](https://www.download3k.com/Install-Bootice.html) 下载了并拷贝到 Scripts 文件夹里面
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) - 生成随机序列号，[参考](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html)，在 [Apple 页](https://checkcoverage.apple.com/cn/zh/) 查询有效性
- [OpenCore](https://github.com/acidanthera/OpenCorePkg) - 目前版本 0.6.3（2020-11），安装手册 [dortania](https://dortania.github.io/OpenCore-Install-Guide/)
- [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) - 版本 2.16.0.0，支持 OpenCore 0.6.3
- [ProperTree](https://github.com/corpnewt/ProperTree) - plist 配置文件编辑器

### ACPI

参考 [官方说明](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-prebuilt.html#desktop-haswell-and-broadwell)

- [SSDT-PLUG](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PLUG-DRTNIA.aml)
- [SSDT-EC](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-DESKTOP.aml)

放到 U 盘 `EFI/OC/ACPI` 目录

### Kext

- [Lilu](https://github.com/acidanthera/Lilu/releases) - 各种驱动的核心平台
- [AppleALC](https://github.com/acidanthera/AppleALC/releases) - 声卡驱动
- [WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases) - 显卡驱动
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases) - SMC 内核仿真、传感器
- [AirportBrcmFixup.kext](https://github.com/acidanthera/airportbrcmfixup/releases) - Broadcom 无线网卡所需的 Airport 补丁
- [IntelMausiEthernet.kext](https://github.com/acidanthera/IntelMausi) - Intel 有线网卡驱动程序

### Driver

- OpenRuntime.efi
- [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)

### Config.plist

根据官网说明配置 [config.plist](https://dortania.github.io/OpenCore-Install-Guide/config.plist/haswell.html)

## 其他

启动后建议开启第三方软件运行权限 `sudo spctl --master-disable`

参考

- [思波图的 M73 黑苹果教程](https://www.bilibili.com/video/BV1ZK411J7SC)
- [Lenovo-M73-Tiny-Hackintosh](https://github.com/cstrouse/Lenovo-M73-Tiny-Hackintosh) - Clover & OC
- [m73-tiny-hackintosh](https://github.com/rehandalal/m73-tiny-hackintosh) - for Clover
- [qianbinbin/hackintosh-m73-tiny](https://github.com/qianbinbin/hackintosh-m73-tiny) - tools & OC
