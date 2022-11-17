# Zigbee-Gateway-LAN

>## 特征

1. TI CC2652P (RF-STAR RF-BM-2652P2)多协议无线模块，最大发射功率功率+20dBm;
2. 最大支持接入200+ zigbee设备;
3. 支持通过USB/LAN进行固件升级;
4. 用于外部天线的 SMA 天线端口;
5. 两种工作模式:LAN Coordinator（默认） 或 USB Coordinator/Router
7. 支持 Z-Stack coordinator/router固件;
8. 即插即用，默认烧录coordinator固件。
9. 支持[Z2M](https://www.zigbee2mqtt.io/)、[ZHA](https://www.home-assistant.io/integrations/zha/);

>## 购买

[Zigbee LAN Gateway PRO](https://www.aliexpress.us/item/3256804557892073.html)

[Zigbee POE Gateway PRO](https://www.aliexpress.us/item/3256804675805140.html) 

>## 使用方法

1. 插入USB-C电源线（5V），插入网线；

2. POE版本支持IEEE802.3af标准，支持宽输入电压范围37Vdc ~ 57Vdc；***注意POE版本不需要USB供电***

3. 下载[ZigStar GW Multi tool](https://github.com/xyzroe/ZigStarGW-MT/releases)，请根据您的操作系统选择对应版本；

4. 运行 ZigStar GW Multi tool，点击刷新按钮，在下拉列表中选择端口号是6638的地址，此时即可获得网关的IP地址；

<img src="../img/LAN gateway/LAN gateway-006.png" >

5. 在浏览器中输入网关的ip地址即可进入网关后台页面

<img src="../img/LAN gateway/LAN gateway-007.png" >

- ### 在ZHA中使用
    
1. 添加ZHA集成   

<img src="../img/USB gateway/usb-gw-001.jpg" >

2. 在下拉菜单中选择手动

<img src="../img/LAN gateway/LAN gateway-002.png" >

3. Radio type选择ZNP

<img src="../img/LAN gateway/LAN gateway-003.png" >

4. 输入 socket://ip_address:6638,data flow control: software,点击 “提交”。***请将“ip_address”替换为网关的ip***

<img src="../img/LAN gateway/LAN gateway-008.png" >

- ### 在Z2M中使用

1. 前往[zigbee2mqtt官网](https://www.zigbee2mqtt.io/guide/installation/)选择一种安装方式
<img src="../img/USB gateway/usb-gw-005.png" >

2. 编辑 Zigbee2MQTT 的configuration.yaml文件,详细配置请前往[Z2M官方文档](https://www.zigbee2mqtt.io/guide/configuration/adapter-settings.html)

    ```yaml
    serial:
        port: tcp://ip_address:6638
    ```
    ***请将“ip_address”替换为网关的ip***
> ### 固件升级

1. 下载[ZigStar GW Multi tool](https://github.com/xyzroe/ZigStarGW-MT/releases)，请根据您的操作系统选择对应版本；

2. 停止运行zha或z2m；

3. 下载固件CC1352P2_CC2652P_launchpad_*.zip，并解压得到.HEX文件
    
    [协调器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/coordinator/Z-Stack_3.x.0/bin)

    [路由器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/router/Z-Stack_3.x.0/bin)

5. 运行ZigStar GW Multi tool，点击刷新按钮，选择端口号是6638的ip地址,从PC中选择 .hex 文件，勾选Erase,Write,Verify,auto BSL, 点击start开始烧录固件。
    
    <img src="../img/LAN gateway/LAN gateway-009.png" >


>## 进阶

    本产品结合WT32-ETH01,LILYGO® TTGO T-Internet-POE，[zigstar](https://zig-star.com/)的优秀设计进行绘制的电路，理论上支持上述硬件的Tasmota固件（需自编译），支持[ZigStar ESP Firmware](https://github.com/xyzroe/ZigStarGW-FW/releases)固件,感谢各位！