2020-5-28更新：

已经能正常升级10.15.5，但是暂时不会更新，因为目前还不完善。

如果你选择升级，应该对以下问题有所防备。

==================================

注意，由于WEG1.4还没有更新，如果你像我一样贸然更新可能会遇到一些问题。

我目前已遇到并解决的问题：

##### 问题一：点击软件更新重新安装系统更新时 系统无限重启：

这是由于我为了搭配refind的图形引导设定了OC的引导菜单为0秒，而本次安装更新会导致OC多出一个 installers选项，OC会默认进入该选项，直到更新安装完成该选项才会消失。

解决方法：

如果还能进MAC 就进mac 使用OpenCore Config 修改即可 如果进不了 

进入windows，使用diskpart工具挂载EFI分区，用ProperTree打开config文件，

```yaml
Misc -> Boot  :  

				  Timeout: 5 等待时间

				  ShowPicker: True 显示菜单

  			  Picker mode :  Builtin 设置菜单启动
```

如果你使用了BCM4322的网卡驱动，那么你还得禁用一下，否则总是会在进度条出现以后就重启 导致了无限重启。

Kernel -> Add -> 找到PATH带IO80211Family.kext 设置 Enabled: false ;

##### 问题二： 进入更新后 前面跑的好好的 突然显示器无信号了，但是电脑没有关闭，风扇还在转。

耐心等待,出现这个问题我也是懵的，等了差不多几分钟，电脑突然就重启了。此时进OC引导，已经没有了Installers选项，说明更新已经完成。

##### 问题三： 为什么更新完成后进入系统，显示器还是无信号，但是键盘功能灯有反应。

可能15.5这次更新，又对UHD630动手了，就像上次更新到15.4 会黑屏一样。

暂时只能靠仿冒七代ID来解决，应该会在weg的下次更新中得到解决。

```xml
注意哦，
如果是使用OC引导升级的，并且确定自己是10.15.5以前没出现问题的，不要按照他说的将它整个PciRoot复制过去，
只要修改
DeviceProperties -> PciRoot(0x0)/Pci(0x2,0x0) > AAPL,ig-platform-id和device-id两项分别为00001259和12590000，就可以了。

修改后文件示例：

                                <key>AAPL,ig-platform-id</key>
                                <data>AAASWQ==</data>
                                <key>AAPL,slot-name</key>
                                <string>Internal</string>
                                <key>device-id</key>
                                <data>ElkAAA==</data>
```

 这个问题的解决要感谢 Judicious提供的建议，出处：http://bbs.pcbeta.com/viewthread-1858867-1-1.html

 2020-5-24更新：

### 重要：此版本更新你将需要把OC的UEFI启动项的路径重新编辑到EFI\OC\BOOT\BOOTX64.EFI

删除小仙女主题 
设定无时间延迟直接进苹果LOGO
添加USB补丁和USB驱动 - emm我2.0的盘倒是能识别来着----3.0的你们试试看？
最近有一段时间 在用refind整理EFI的时候手jian误删了于是重新配置了一遍 有一些修改我可能也记不得了
那就这样....... 安，

### 为适应未来更新趋势版本，已从Clover迁移到OpenCore.

OpenCore 比之Clover的配置繁琐更多，但带来的是更合理的规范，更优越的性能，目前OC正在不断的更新中，此版本花费了我三天的时间查询大量资料才成功将其运行。目前已经能正常使用，欢迎大家查阅改进。

我目前的机子是这样引导的：

##### UEFI  ->   Refind[强烈建议 主题好看上手简单] -> {「OC&黑苹果」,「Windows10」,「Grub2&Deepin」}

```
系统配置:
主板:GIGABYTE-B360M-AORUS-PRO
CPU:I5-8400
无线网卡：BCM-4322 
蓝牙：来自AC9560的蓝牙支持{WIFI暂时无法驱动支持 但听说AppleIntel已经能初步加载7、9系的部分网卡了，期待那一天到来。} [2020.5.28：Intelwifi已经能够初步驱动9560，但是目前还不是很完善]
声卡：ALC892
内存：16G
显卡：8400核显 - UHD630
CFG解锁：已解锁 - 未解锁的请翻阅底部链接，找到解锁教程 或者将CFG模拟设置为True。
伪造型号： iMac19,2
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
