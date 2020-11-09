2020-11-9更新：

OC引导升级至OC0.6.2

升级一批基础驱动。

OpenCore引导升级至6.2官方正式版本。

因为网卡更换，删除了一批驱动，目前仅保留AirportBrcmFixup即可

~~升级英特尔无线AC驱动支持-IntelWIFI（8.2) 测试版  itlwm.kext。~~ (已移除Intel无线驱动，网卡改动如下。)

之前提过：

> **关于IO80211Family，该驱动很有可能在BIGSUR中无法使用，**
> **具体情况参照OpenCore6.1开发版中黑屏重启的情况，**
> **这将导致BCM4322无法继续使用，所以此驱动可能会在下次更新中被丢弃。**
> **该现象在此前经常出现在系统版本升级过程中，需要禁用才能解决，**
> **但OC6.1对此网卡的驱动支持并不友好,**
> **使用AirportBrcmFixup仿冒也没有成功解决.**
> **所以在后续的版本更新有可能会对网卡配置有所变动.**

所以在MacOS11版本我迫不得已换上了

比BCM943224_0X432B更新一个版本的白果卡 —— *BCM*943224PCIEBT2

这套台式PCI转接+网卡总共更换花销70¥。

目前的配置单：

```
机器配置:
主板:GIGABYTE-B360M-AORUS-PRO
CPU:Intel I5-8400
无线网卡：BCM943224PCIEBT2
蓝牙：来自BCM943224PCIEBT2的原生蓝牙支持 
声卡：来自主板的集成声卡 -- ALC892
内存：台电A30 DDR4 8GX2 2400MHz
显卡：来自CPU的核心显卡 -- UHD630
以太网：来自主板的Realtek网卡
```

操作配置：

OpenCore版本 ： [OpenCore-0.6.2-RELEASE.zip](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.6.2)

ProperTree：https://github.com/corpnewt/ProperTree

