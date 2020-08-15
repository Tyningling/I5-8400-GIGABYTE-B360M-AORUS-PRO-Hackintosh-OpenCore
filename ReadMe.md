### 为适应及满足未来版本的更新，从CLover迁移至OpenCore.

> OpenCore 比之Clover的配置繁琐更多，但带来的是规范更加合理，性能更好，相比🍀更加简洁，并且得到了更多的认可与维护机会。目前OC正在不断的更新。日益强壮之中。
>

我目前的机子是这样引导的：

UEFI  ->   Refind[强烈建议 主题好看上手简单还没有BIOS风险] -> {「OC&黑苹果」,「Windows10」,「Grub2&Deepin」}

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