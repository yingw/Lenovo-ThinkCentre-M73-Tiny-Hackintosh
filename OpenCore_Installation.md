
# OpenCore 配置过程

基本参考 [官网说明](https://dortania.github.io/OpenCore-Install-Guide/) 安装

## 相关工具

- 7zip
- Python
- [gibMacOS](https://github.com/corpnewt/gibMacOS) - 下载 MacOS 镜像
  - 如果下载失败，想办法把 [ddrelease64.exe](http://www.chrysocome.net/downloads/ddrelease64.exe) 和 [booticex64.exe](https://www.download3k.com/Install-Bootice.html) 下载了并拷贝到 Scripts 文件夹里面
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) - 生成随机序列号，[参考](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html)，在 [Apple 页](https://checkcoverage.apple.com/cn/zh/) 查询有效性
- [OpenCore](https://github.com/acidanthera/OpenCorePkg) - 目前版本 0.6.3（2020-11），安装手册 [dortania](https://dortania.github.io/OpenCore-Install-Guide/)
- [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) - 版本 2.16.0.0，支持 OpenCore 0.6.3
- [ProperTree](https://github.com/corpnewt/ProperTree) - plist 配置文件编辑器

## ACPI

参考 [官方说明](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-prebuilt.html#desktop-haswell-and-broadwell)

- [SSDT-PLUG](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PLUG-DRTNIA.aml)
- [SSDT-EC](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-DESKTOP.aml)

aml 文件放到 U 盘 `EFI/OC/ACPI` 目录

### Kernel (Kext)

- [Lilu](https://github.com/acidanthera/Lilu/releases) - 各种驱动的核心平台
- [AppleALC](https://github.com/acidanthera/AppleALC/releases) - 声卡驱动
- [WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases) - 显卡驱动
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases) - SMC 内核仿真、传感器
- [AirportBrcmFixup.kext](https://github.com/acidanthera/airportbrcmfixup/releases) - Broadcom 无线网卡所需的 Airport 补丁
- [IntelMausiEthernet.kext](https://github.com/acidanthera/IntelMausi) - Intel 有线网卡驱动程序

kext 文件（目录）放到 U 盘 `EFI/OC/Kexts` 目录，dSYM 是编译文件不需要

### UEFI

- OpenRuntime.efi
- [HfsPlus.efi](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)

放到 `EFI/OC/Drivers` 目录

### Config.plist

根据官网说明配置 [config.plist](https://dortania.github.io/OpenCore-Install-Guide/config.plist/haswell.html)

[开启 4K](https://www.reddit.com/r/hackintosh/comments/i1h47z/how_to_enable_4k_on_hd4600_igpu_in_opencore_using/)

- framebuffer-patch-enable = 01000000
- framebuffer-stolenmem = 00000004 (64m)
- framebuffer-fbmem = 00000003 (48m)
- framebuffer-unifiedmem = 00000080 (提示显存到2G)

开启 4K 60Hz：在 `boot-args` 增加 `-cdfon`
