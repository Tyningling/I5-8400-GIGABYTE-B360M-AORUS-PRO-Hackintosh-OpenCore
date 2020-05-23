## 为适应未来更新趋势版本，将从Clover迁移到OpenCore.

OpenCore 比之Clover的配置繁琐更多，但带来的是更合理的规范，更优越的性能，目前OC正在不断的更新中，此版本花费了我三天的时间查询大量资料才成功将其运行。目前已经能正常使用，欢迎大家查阅改进。

我目前的机子是这样引导的：
##### UEFI  ->   Refind[强烈建议 主题好看上手简单] -> {「OC&黑苹果」,「Windows10」,「Grub2&Deepin」}
2020-5-24更新：

### 重要：此版本更新你将需要把OC的UEFI启动项的路径重新编辑到EFI\OC\BOOT\BOOTX64.EFI
删除小仙女主题 
设定无时间延迟直接进苹果LOGO
添加USB补丁和USB驱动 - emm我2.0的盘倒是能识别来着----3.0的你们试试看？
最近有一段时间 在用refind整理EFI的时候手jian误删了于是重新配置了一遍 有一些修改我可能也记不得了
那就这样....... 安，

```
系统配置:
主板:GIGABYTE-B360M-AORUS-PRO
CPU:I5-8400
无线网卡：BCM-4322 
蓝牙：来自AC9560的蓝牙支持{WIFI暂时无法驱动支持 但听说AppleIntel已经能初步加载7、9系的部分网卡了，期待那一天到来。}
声卡：ALC892
内存：16G
显卡：8400核显 - UHD630
CFG解锁：已解锁 - 未解锁的请翻阅底部链接，找到解锁教程 或者将CFG模拟设置为True。
USB定制： 暂时未改动 后续会更新
伪造型号： iMac18,1
OC主题: 来自仙女Plus——https://github.com/Fairy-Plus/OpenCoretheme/releases/tag/1.0.2 
[您可以查看OLD文件夹 将其按照下方设定进行配置]
```


操作配置：

OpenCore版本 ： [2020-4-25-RELEASE-OpenCore-0.5.8](https://github.com/williambj1/OpenCore-Factory/releases/tag/2020-04-25)

OpenCoreConfig:  [Version-2.0.0.0](https://mackie100projects.altervista.org/occ-changelog-version-2-0-0-0/) 「请注意在设置里将Config版本调整到OC 0.58」

[Hackintool](https://github.com/headkaze/Hackintool)：版本 3.4.0（0340）

ProperTree：https://github.com/corpnewt/ProperTree

——————————————————————————————————————————


能使本配置成功运行，离不开社区的支持，感谢前辈们的资料援助：

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
