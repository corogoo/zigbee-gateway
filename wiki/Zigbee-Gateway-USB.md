# Zigbee-Gateway-USB

>## 特征

1. TI CC2652P (RF-STAR RF-BM-2652P2)多协议无线模块，最大发射功率功率+20dBm;
2. 最大支持接入200+ zigbee设备;
3. 板载BSL按键，支持通过USB进行固件升级;
4. 2个LED指示灯;
5. 用于外部天线的 SMA 天线端口;
6. 通过通用的 CH340E/CH340C USB-UART 桥进行通信;
7. 支持 Z-Stack coordinator/router固件;
8. 即插即用，默认烧录coordinator固件。
9. 支持[Z2M](https://www.zigbee2mqtt.io/)、[ZHA](https://www.home-assistant.io/integrations/zha/);

>## 购买

[速卖通Aliexpress](https://www.aliexpress.us/item/3256803441836847.html)

***


>## 使用方法

- ### 在ZHA中使用
    
1. 插入USB网关，并添加ZHA集成   
<img src="../img/USB gateway/usb-gw-001.jpg" >

2. 选择对应端口
<img src="../img/USB gateway/usb-gw-002.webp" >

3. 流控默认不选
<img src="../img/USB gateway/usb-gw-003.webp" >

4. 添加成功
<img src="../img/USB gateway/usb-gw-004.webp" >

- ### 在Z2M中使用

1. 前往[zigbee2mqtt官网](https://www.zigbee2mqtt.io/guide/installation/)选择一种安装方式
<img src="../img/USB gateway/usb-gw-005.png" >

2. 编辑 Zigbee2MQTT 的configuration.yaml文件,详细配置请前往[Z2M官方文档](https://www.zigbee2mqtt.io/guide/configuration/adapter-settings.html)

    ```yaml
    serial:
        port: /dev/ttyUSB0
    ```

> ### 固件升级

1. 下载[ZigStar GW Multi tool](https://github.com/xyzroe/ZigStarGW-MT/releases)，请根据您的操作系统选择对应版本；

2. 打开外壳，按住按键不放，插入USB，然后松开按键；

3. 串口驱动
    1. 如果您是mac os系统，串口驱动无需安装；
    2. 如果您是windows系统，请在设备管理器中的“端口（COM 和 LPT）”下检查
        
        <img src="../img/USB gateway/usb-gw-006.png" >
        
        如果没有[点此链接](https://www.wch.cn/download/CH341SER_ZIP.html)下载安装

4. 运行ZigStar GW Multi tool，点击刷新按钮，在下拉列表中选择正确的COM端口

    <img src="../img/USB gateway/usb-gw-007.png" >

5. 下载固件CC1352P2_CC2652P_launchpad_*.zip，并解压得到.HEX文件
    
    [协调器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/coordinator/Z-Stack_3.x.0/bin)

    [路由器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/router/Z-Stack_3.x.0/bin)

6. 从PC中选择 .hex 文件，勾选Erase,Write and Verify，点击start开始烧录固件。

    <img src="../img/USB gateway/usb-gw-008.png" >