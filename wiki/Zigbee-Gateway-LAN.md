# Zigbee-Gateway-LAN

>## 特征

1. TI CC2652P (RF-STAR RF-BM-2652P2)多协议无线模块，最大发射功率功率+20dBm;
2. 最大支持接入200+ zigbee设备;
3. 板载BSL按键，支持通过USB/LAN进行固件升级;
4. 用于外部天线的 SMA 天线端口;
5. 两种工作模式:LAN Coordinator(默认) 或 USB Coordinator/Router
6. 支持 Z-Stack coordinator/router固件;
7. 即插即用，默认烧录coordinator固件。
8. 支持[Z2M](https://www.zigbee2mqtt.io/)、[ZHA](https://www.home-assistant.io/integrations/zha/);

>## 购买

[速卖通Aliexpress](https://www.aliexpress.us/item/3256804554006317.html)

>## 使用方法

1. 插入USB-C电源线（5V），插入网线；

2. 运行 [DTUConfigTool_V2(点击下载)](https://docs.coltsmart.com/download/client/dtu-config-tool/x64/nostatement/dtu-config-tool-x64-nostatement%20Setup.zip)，点击“搜索设备”按钮，当搜索到设备之后，复制网关的ip地址备用；另外，可根据自己需求选择IP地址获取的方式是DHCP（建议）或者手动获取，修改完成后，点击“重启修改”，

    **注意！！！其他参数不要修改！！！**

<img src="../img/LAN gateway/LAN gateway-010.jpg" >

    ** ！！！ 老版本请运行 [DTUConfigTool_V1(点击下载)](https://www.coltsmart.com/download/DTUConfigTool_V5.1%E4%B8%AD%E6%80%A7%E7%89%88.rar)，点击“搜索设备”按钮，当搜索到设备之后，去掉自动获取ip选项，点击写入参数，复制网关的ip地址备用。**

<img src="../img/LAN gateway/LAN gateway-001.jpg" >


- ### 在ZHA中使用
    
1. 添加ZHA集成   

<img src="../img/USB gateway/usb-gw-001.jpg" >

2. 在下拉菜单中选择手动

<img src="../img/LAN gateway/LAN gateway-002.png" >

3. Radio type选择ZNP

<img src="../img/LAN gateway/LAN gateway-003.png" >

4. 输入 socket://ip_address:1053,data flow control: software,点击 “提交”。***请将“ip_address”替换为网关的ip，新版本默认端口号是 1053，老版本的默认端口号是5000***

<img src="../img/LAN gateway/LAN gateway-004.png" >

- ### 在Z2M中使用

1. 前往[zigbee2mqtt官网](https://www.zigbee2mqtt.io/guide/installation/)选择一种安装方式
<img src="../img/USB gateway/usb-gw-005.png" >

2. 编辑 Zigbee2MQTT 的configuration.yaml文件,详细配置请前往[Z2M官方文档](https://www.zigbee2mqtt.io/guide/configuration/adapter-settings.html)

    ```yaml
    serial:
        port: tcp://ip_address:1053
    ```
    ***请将“ip_address”替换为网关的ip，新版本默认端口号是 1053，老版本的默认端口号是5000***
> ### 固件升级

1. 下载[ZigStar GW Multi tool](https://github.com/xyzroe/ZigStarGW-MT/releases)，请根据您的操作系统选择对应版本；

2. 停止运行zha或z2m；

3. 打开外壳，按住按键不放，插入USB，然后松开按键,插入网线并获取到ip地址；

4. 下载固件CC1352P2_CC2652P_launchpad_*.zip，并解压得到.HEX文件
    
    [协调器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/coordinator/Z-Stack_3.x.0/bin)

    [路由器](https://github.com/Koenkk/Z-Stack-firmware/tree/master/router/Z-Stack_3.x.0/bin)

5. 运行ZigStar GW Multi tool，在输入框中输入网关ip:1053（!!! 新版本默认端口号是 1053，老版本的默认端口号是5000）,从PC中选择 .hex 文件，勾选Erase,Write,Verify，不要勾选auto BSL, 点击start开始烧录固件。
    
    <img src="../img/LAN gateway/LAN gateway-005.png" >