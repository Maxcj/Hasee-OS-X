# Hasee-OS-X说明



## 电脑配置

|       设备名       |                          型号                          |   ID/备注    |
| :----------------: | :----------------------------------------------------: | :----------: |
|        CPU         |               英特尔 第四代酷睿 i5-4210M               |              |
|        主板        | Type2 - Board Vendor Name1 Type2 - Board Product Name1 |              |
|        内存        |                 三星 DDR3L 1600MHz 8GB                 |              |
|   硬盘（Mac OS）   |        金士顿  SUV400S37120G （120GB固态硬盘）         |              |
| 硬盘（Windows 10） |       三星  MZMPC128HBFU-000MV （128GB固态硬盘）       |              |
|    硬盘（File）    |         希捷 ST1000LM048-2E7172（1TB机械硬盘）         |              |
|      核心显卡      |                英特尔 HD Graphics 4600                 |              |
|      独立显卡      |               Nvidia GeForce 940M（2GB）               | 需要屏蔽独显 |
|        声卡        |         瑞昱  @ 英特尔 Lynx Point  高保真音频          |    ALC282    |
|      有线网卡      |   瑞昱 RTL8168/8111/8112 Gigabit Ethernet Controller   |   RTL8111    |
|      无线网卡      |      博通 Wireless 1510 Wireless-N WLAN Mini-Card      |     免驱     |
|    键盘、触摸板    |             PS/2 标准键盘 + ELAN Clickpad              |              |
|     SD卡读卡器     |                Realtek PCIE CardReader                 |  0x522710EC  |



##  EFI下载

+ 最新版本：`2.0.3`
+ [下载地址](https://github.com/Maxcj/Hasee-OS-X/releases)



## 更新日志

> 2018.10.16

+ 修改`DSDT.aml`
+ 使用`Intel FB-Patcher`修补USB端口
+ 添加`USBPorts.kext`，去除`USBInjectAll.kext` 以及关闭端口限制的补丁
  +  [详细教程参考黑果小兵的部落阁](https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html)
+ 修改`ApplePS2SmartTouchPad.kext`实现小键盘开机自启动





> 2018.10.13

+ 驱动原生`AppleBacklight.kext`修复小太阳滑块等级不均匀Bug



> 2018.10.10

+ 添加SSDT，以加载两个X86、AppleLPC、AppleHDMP修复睡眠问题
+ 删除多余Kext，减小EFI体积大小
+ 更新`ACPIBatteryManager.kext`、`USBInjectAll.kext`版本为最新版本





> 2018.09.26

+ 升级系统至Mac Mojave（18A191）
+ 解决开机鼠标卡顿Bug
+ 解决HD4600局部花屏Bug
+ 解决USB3.0速度只有480MB/S问题



## 目前存在的已知BUG

- SD卡未能驱动
  -  [PCI读卡器驱动](http://bbs.pcbeta.com/viewthread-1761527-1-1.html)、 [PCI读卡器是否可以驱动](http://bbs.pcbeta.com/viewthread-1748821-1-1.html)
- 触控板右击失效（`ApplePS2SmartTouchPad.kext`必须按住Ctrl键再单击才可以实现右击）
- ……（待发现）



## Clover以及一些常用的Kext下载地址

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

1.  电池图标显示：[电池电量补丁制作教程](http://bbs.pcbeta.com/viewthread-1595139-1-1.html)
2.  笔记本亮度调节：[给DSDT/SSDT打补丁，实现笔记本亮度调节](http://bbs.pcbeta.com/viewthread-1571456-1-1.html)
3. 开启HiDPI：[HiDPI 是什么？以及黑苹果如何开启 HiDPI](http://www.sqlsec.com/2018/09/hidpi.html)
4.  系统报告 -> 中显示PCI设备： [PCI设备列表显示](http://bbs.pcbeta.com/viewthread-1740881-1-1.html)
5. ……（待更新）



## 安装Mac Mojave的一些问题

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

3. USB3.0 补丁（需配合最新版本的[USB-Inject-All](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)）如下：

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



## 部分截图

### 桌面

![桌面](http://pggninums.bkt.clouddn.com/%E6%A1%8C%E9%9D%A2.png)



### 关于本机

![关于本机](http://pggninums.bkt.clouddn.com/%E5%85%B3%E4%BA%8E%E6%9C%AC%E6%9C%BA.png)

### 显卡

![显卡](http://pggninums.bkt.clouddn.com/%E6%98%BE%E5%8D%A1.png)

### 水波纹效果

![水波纹效果](http://pggninums.bkt.clouddn.com/%E6%B0%B4%E6%B3%A2%E7%BA%B9.png)

### 声卡

![声卡](http://pggninums.bkt.clouddn.com/%E5%A3%B0%E5%8D%A1.png)

### 有线网卡

![有线网卡](http://pggninums.bkt.clouddn.com/%E6%9C%89%E7%BA%BF%E7%BD%91%E5%8D%A1.png)

### 无线网卡

![无线网卡](http://pggninums.bkt.clouddn.com/%E6%97%A0%E7%BA%BF%E7%BD%91%E5%8D%A1.png)

### 原生电源管理

> Haswell框架 HD4600 只需要加载两个`X86`、`AppleLPC`、`AppleHPET`即可。

![电源管理](http://pggninums.bkt.clouddn.com/%E5%8E%9F%E7%94%9F%E7%94%B5%E6%BA%90%E7%AE%A1%E7%90%86.png)

### 小太阳快捷键

> Clover中勾选`AddPLNF`，给`DSDT`打补丁实现`17级均匀亮度`，小太阳快捷键外接USB接盘修改快捷键即可。

![小太阳快捷键](http://pggninums.bkt.clouddn.com/%E5%B0%8F%E5%A4%AA%E9%98%B3.png)

### 电源电池

![电源信息](http://pggninums.bkt.clouddn.com/%E7%94%B5%E6%BA%90.png)

### USB

![USB](http://pggninums.bkt.clouddn.com/USB.png)

### HIDPI

> 感谢开源项目：[one-key-hidpi](https://github.com/xzhih/one-key-hidpi)

![HIDPI](http://pggninums.bkt.clouddn.com/HIDPI.png)

