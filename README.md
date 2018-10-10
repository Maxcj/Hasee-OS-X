# Hasee-OS-X说明



### 电脑配置

|     设备名      |                          型号                          |
| :-------------: | :----------------------------------------------------: |
|       CPU       |               英特尔 第四代酷睿 i5-4210M               |
|      主板       | Type2 - Board Vendor Name1 Type2 - Board Product Name1 |
|      内存       |                 三星 DDR3L 1600MHz 8GB                 |
| 硬盘（Windows） |       三星  MZMPC128HBFU-000MV （128GB固态硬盘）       |
| 硬盘（Mac OS）  |        金士顿  SUV400S37120G （120GB固态硬盘）         |
|  硬盘（Data）   |         希捷 ST1000LM048-2E7172（1TB机械硬盘）         |
|      独显       |               Nvidia GeForce 940M（2GB）               |
|      核显       |                英特尔 HD Graphics 4600                 |
|      声卡       |      瑞昱  @ 英特尔 Lynx Point  高保真音频 ALC282      |
|    有线网卡     |   瑞昱 RTL8168/8111/8112 Gigabit Ethernet Controller   |
|    无线网卡     |      博通 Wireless 1510 Wireless-N WLAN Mini-Card      |
|  键盘、触摸板   |             PS/2 标准键盘 + ELAN Clickpad              |



### 更新日志

> 2018.10.10

+ 添加SSDT，以加载两个X86、AppleLPC、AppleHDMP
+ 删除多余Kext，减小EFI体积大小
+ 更新`ACPIBatteryManager.kext`版本为最新版本
+ 更换`ApplePS2SmartTouchPad.kext`为`VoodooPS2Controller.kext`，解决触控板右击失效（`ApplePS2SmartTouchPad.kext`必须按住Ctrl键再单击才可以实现右击）



> 2018.09.26

+ 升级系统至Mac Mojave（18A191）
+ 解决开机鼠标卡顿BUG
+ 解决HD4600局部花屏BUG
+ 解决USB3.0速度只为480MB/S问题



### 目前存在的已知BUG

- 系统偏好设置 -> 触控板  提示`找不到触控板`（更换为`VoodooPS2Controller.kext`出现此BUG）
- ……（待发现）




### Clover以及一些常用的Kext下载地址

+ 引导驱动（四叶草）：[Clover](https://github.com/Dids/clover-builder/releases)
+ 安装Hackintosh必备：[FakeSMC](https://bitbucket.org/RehabMan/os-x-fakesmc-kozlek/downloads/)
+ 驱动扩展库：[Lilu](https://github.com/acidanthera/Lilu/releases)
+ 音频仿冒（需配合Lilu）：[AppleALC](https://github.com/acidanthera/AppleALC/releases)
+ GPU补丁（需配合Lilu）：[WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases)
+ 电池管理：[ACPIBatteryManager](https://bitbucket.org/RehabMan/os-x-acpi-battery-driver/downloads/)
+ 有线网卡：[RTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases)
+ Broadcom蓝牙驱动：[BrcmPatchRAM](https://bitbucket.org/RehabMan/os-x-brcmpatchram/downloads/)
+ 触控板：[Voodoo-I2C-Controller](https://github.com/alexandred/VoodooI2C/releases)、[Voodoo-PS2-Controller](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/)
+ USB：[USB-Inject-All](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
+ 伪造硬件ID：[FakePCIID](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/)
+ 动态电源管理（需配合Lilu）：[CPUFriend](https://github.com/acidanthera/CPUFriend/releases)
+ 解决睡眠无声：[Codec-Commander](https://bitbucket.org/RehabMan/os-x-eapd-codec-commander/downloads/)
+ ……（待更新）



## Hackintosh进阶教程

1.  [电池电量补丁制作教程](http://bbs.pcbeta.com/viewthread-1595139-1-1.html)
2.  [给DSDT/SSDT打补丁，实现笔记本亮度调节](http://bbs.pcbeta.com/viewthread-1571456-1-1.html)
3. [HiDPI 是什么？以及黑苹果如何开启 HiDPI](http://www.sqlsec.com/2018/09/hidpi.html)
4.  [PCI设备列表显示](http://bbs.pcbeta.com/viewthread-1740881-1-1.html)
5. ……（待更新）



### 安装Mac Mojave的一些问题

1. 开机鼠标卡顿，进入桌面后流畅

   > 参照教程：[[12.4~12.6] HD4600 开机后鼠标卡顿得到完美的解决！不需要换机型！！不是灌水！！！](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1738959)

2. HD4600局部花屏：

   > 打补丁将显存增加至2048MB

   ```
   Name：com.apple.driver.AppleIntelFramebufferAzul
   Find：01030303 00000002 00003001 00006000 00000060
   Replace：01030303 00000002 00003001 00009000 00000080
   Comment：1536MB -> 2048MB for HD4600 Mobile
   ```

3. USB3.0 补丁如下：

   ``` 
   ==10.14.1==
   Name: com.apple.driver.usb.AppleUSBXHCI
   Find: 83 FB 0F 0F 83 8F 04 00 00
   Replace: 83 FB 0F 90 90 90 90 90 90
   Comment: USB Port limit patch 10.14.1 18B45d (credits Ricky)
   
   ==10.14==
   Name: com.apple.driver.usb.AppleUSBXHCI
   Find: 83FB0F0F 83030500 00
   Replace: 83FB0F90 90909090 90
   Comment: USB Port limit patch 10.14 18A191
   ```

4. ……（待更新）


