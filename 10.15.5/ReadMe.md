2020-8-15更新：

OpenCore引导升级至6.0官方正式版本。
升级英特尔无线AC驱动支持-IntelWIFI（8.2) 测试版  itlwm.kext。
升级一批基础驱动。

> **关于IO80211Family，该驱动很有可能在BIGSUR中无法使用，**
> **具体情况参照OpenCore6.1开发版中黑屏重启的情况，**
> **这将导致BCM4322无法继续使用，所以此驱动可能会在下次更新中被丢弃。**
> **该现象在此前经常出现在系统版本升级过程中，需要禁用才能解决，**
> **但OC6.1对此网卡的驱动支持并不友好,**
> **使用AirportBrcmFixup仿冒也没有成功解决.**
> **所以在后续的版本更新有可能会对网卡配置有所变动.**

2020-6-3更新：

注意： 此更新版本仍然使用仿冒七代的方案驱动板载HDMI及DVI输出。

已经更新至10.15.5[19F101]并成功引导：

> 苹果已经发布了适用于macOS Catalina 10.15.5的新补充更新。此更新修补了CVE-2020-9859，这是uncOver的内核漏洞。

更新了一批驱动。

适配OpenCorev0.5.9

添加Beta_itlwm.kext 驱动IntelWifi {公测阶段，由于刚发布，所以暂不默认添加}

关于OCC ： 请升级至最新版本，否则你可能会因为旧版的编辑出现错误。

本版三码未清除，请自行更换。

目前已知未解问题：

暂无。

提醒：使用BCM4322的在进行版本更新时，需要手动禁用BCM4322驱动再重启更新哦！

=================================

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

暂时只能靠仿冒七代ID来解决，~~应该会在weg的下次更新中得到解决~~ 「或许在下下次得到解决。」。

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



操作配置：

OpenCore版本 ： [OpenCore-0.5.9-RELEASE.zip](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.5.9)

OpenCoreConfig:  [Version-2.5.0.0](https://mackie100projects.altervista.org/occ-changelog-version-2-5-0-0/) 「请注意在设置里将Config版本调整到OC 0.5.9」

[Hackintool](https://github.com/headkaze/Hackintool)：版本 3.4.0（0340）

ProperTree：https://github.com/corpnewt/ProperTree