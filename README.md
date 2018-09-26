# Hasee-OS-X说明



### 电脑配置

|     设备名      |                          型号                          |
| :-------------: | :----------------------------------------------------: |
|       CPU       |               英特尔 第四代酷睿 i5-4210M               |
|      主板       | Type2 - Board Vendor Name1 Type2 - Board Product Name1 |
|      内存       |                 三星 DDR3L 1600MHz 8GB                 |
| 硬盘（Windows） |        三星  MZMPC128HBFU-000MV (128GB固态硬盘)        |
| 硬盘（Mac OS）  |         金士顿  SUV400S37120G (120GB固态硬盘)          |
|  硬盘（Data）   |              希捷 ST1000LM048-2E7172 1TB               |
|      独显       |               Nvidia GeForce 940M（2GB）               |
|      核显       |                英特尔 HD Graphics 4600                 |
|      声卡       |      瑞昱  @ 英特尔 Lynx Point  高保真音频 ALC282      |
|    有线网卡     |   瑞昱 RTL8168/8111/8112 Gigabit Ethernet Controller   |
|    无线网卡     |      博通 Wireless 1510 Wireless-N WLAN Mini-Card      |
|  键盘、触摸板   |             PS/2 标准键盘 + ELAN Clickpad              |



### macOS High Sierra升级至Mac Mojave的一些问题

1. 开机鼠标卡顿，进入桌面后流畅

   > 参照远景论坛教程：[[12.4~12.6] HD4600 开机后鼠标卡顿得到完美的解决！不需要换机型！！不是灌水！！！](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1738959)

2. HD4600局部花屏：

   > 将显存增加至2048MB

   - 补丁如下

   ```
   Name：com.apple.driver.AppleIntelFramebufferAzul
   Find：01030303 00000002 00003001 00006000 00000060
   Replace：01030303 00000002 00003001 00009000 00000080
   Comment：1536MB -> 2048MB for HD4600 Mobile
   ```

3. USB3.0

   - 补丁如下

   ```
   Name：com.apple.driver.usb.AppleUSBXHCI
   Find：83FB0F0F 83030500 00
   Replace：83FB0F90 90909090 90
   Comment：disable port limit in XHCI kext (credit PMHeart)
   ```

