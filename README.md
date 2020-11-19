# Lenovo-ThinkCentre-M73-Tiny-Hackintosh

[联想 M73](https://www.lenovo.com/us/en/desktops/thinkcentre/m-series-tiny/m73/) 的黑苹果 EFI，使用 [OpenCore](https://github.com/acidanthera/OpenCorePkg) 引导。

## 介绍

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

正常驱动：

- 有线网卡
- 无线网卡
- 蓝牙
- 声卡
- 显卡
- USB 3.0
- 睡眠
- HDMI 4G 分辨率 60Hz 刷新率输出
- 隔空传送（AirDrop）
- 接力（Handoff）

不能工作：

- VGA 视频输出

## 使用教程

1. 使用 [gibMacOS](https://github.com/corpnewt/gibMacOS) 下载镜像，烧录 Mac 安装 U 盘
2. 拷贝此 EFI 到 Boot 分区，用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 更换序列号（型号选：`iMac14,4`）
3. 根据官网说明修改主机 [BIOS 设置](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#intel-bios-settings)
4. U 盘启动安装（大约 1 小时）
5. 安装完成后可以用 [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) 挂载 EFI 分区，拷贝 U 盘 EFI 到主机 EFI 分区

## 其他

启动后建议开启第三方软件运行权限 `sudo spctl --master-disable`

- 需要了解此版本 OpenCore 配置过程可参考 [OpenCore_Installation.md](./OpenCore_Installation.md)；
- 需要了解如何升级到 Big Sur 可参考 [Upgrade_Big_Sur.md](./Upgrade_Big_Sur.md)；

其他参考教程：

- [思波图的 M73 黑苹果教程](https://www.bilibili.com/video/BV1ZK411J7SC)
- [Lenovo-M73-Tiny-Hackintosh](https://github.com/cstrouse/Lenovo-M73-Tiny-Hackintosh) - Clover & OC
- [m73-tiny-hackintosh](https://github.com/rehandalal/m73-tiny-hackintosh) - for Clover
- [qianbinbin/hackintosh-m73-tiny](https://github.com/qianbinbin/hackintosh-m73-tiny) - tools & OC
