更新中：

macOS Big Sur 11.0.1 Beta版 (20B5022a)

已完结：

macOS Mojave10.14 全版本
*macOS* Catalina10.15 全版本

~~10.16 等待正式版发布!~~

我的博客 https://inkhin.com
### 为适应及满足未来版本的更新，从CLover迁移至OpenCore.

> OpenCore 比之Clover的配置繁琐更多，但带来的是规范更加合理，性能更好，相比🍀更加简洁，并且得到了更多的认可与维护机会。目前OC正在不断的更新。日益强壮之中。

我目前的机子是这样引导的：

UEFI  ->   Refind[强烈建议 主题好看上手简单还没有BIOS风险] -> {「OC&黑苹果」,「Windows10」,「Grub2&Deepin」}



——————

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


理论上，11版本EFI是可以与10.14及10.15通用的，因为改动并不大。
但为了防止某些特殊情况发生，我扔保留了旧版本的仓库文件。
——————
旧版本ReadMe
——————

```
机器配置:
主板:GIGABYTE-B360M-AORUS-PRO
CPU:I5-8400
无线网卡：BCM-4322  Intel-AC9560 
蓝牙：来自AC9560的蓝牙支持 
声卡：ALC892
内存：16G
显卡：8400核显 - UHD630
CFG解锁：已解锁 - 未解锁的请翻阅底部链接，找到解锁教程 或者将CFG模拟设置为True。
伪造型号： iMac19,2
```

——————————————————————————————————————————


能够成功运行，离不开社区的支持，感谢前辈们的分享资料援助：

「有些问题参考由于时间原因没有记住，在这里也向你们表示感谢。」

https://blog.daliansky.net/OpenCore-BootLoader.html

https://blog.skk.moe/post/time-to-use-ocquirks/

https://mackie100projects.altervista.org/

https://blog.skk.moe/post/macos-boot-args/

https://www.jianshu.com/p/da68e410612f?ivk_sa=1023345p

http://bbs.pcbeta.com/viewthread-1843330-1-1.html

http://bbs.pcbeta.com/viewthread-1851385-1-1.html

https://github.com/GeQ1an/MSI-B360M-MORTAR-HACKINTOSH-OPENCORE-EFI/blob/master/README.md

https://github.com/williambj1/OpenCore-Factory

https://www.jianshu.com/p/a466c0193850

http://imacos.top/2020/04/12/0042/
