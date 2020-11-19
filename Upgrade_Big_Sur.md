# 升级到 Big Sur

参考[注意事项](https://dortania.github.io/OpenCore-Install-Guide/extras/big-sur/)。

大体上直接从安装好的 Catalina 系统内直接升级就可以，只是要注意安装过程重启后会在 verbose 模式有很长时间的升级过程，大概一小时左右，重启四五次，耐心等待。

升级到 Big Sur 后有可能 943224 网卡不再免驱，可以打一个补丁 [IO80211-Patches](https://github.com/khronokernel/IO80211-Patches)，就是将低版本的驱动提取出来到 Big Sur 就行了。（且首几次重启很慢，打好补丁后就重启很快了，甚至超过了 Catalina，不知道是不是驱动的问题）

全新安装：TBD
