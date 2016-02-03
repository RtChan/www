家用路由WDS中继设置
===
2015-8-1 13:41:52 Author:Rt Chen

最后更新：2016-2-3 18:45:16

## 前言 ##
家中离路由器最远的房间信号比较差，使用清华同方入门级笔记本电脑搜索wifi信号非常差，导致网络质量非常差。之前使用TP-LINK WR340G+作为副路由器启用WDS失败，无法正常连接，遂放弃。今日捡到新路由器一个，型号较为先进，因此打算试试。

**设备型号：**

【主路由器】<br>
- 型号： NETGEAR WNDR4300<br>
- 固件版本： V1.0.1.64PRRU

【副路由器】<br>
- 型号： TP-LINK WR845N V3.0<br>
- 固件版本： 1.2.10 Build 140210 Rel.38079n

## 过程 ##

### 设置与记录 ###
记录（拿纸拿笔抄下来）主路由器WIFI配置，为配置WDS作准备。
> **页面位置：NETGEAR管理页 -> “高级”选项卡 -> 安装 -> 无线设置**<br>
> 无线网络标识（SSID）：记录，供副路由器使用<br>
> 频道：也就是“信道”。手动设定一个固定的频道，不能使用“自动”，记录，供副路由器使用<br>
> 安全选项：记录，供副路由器使用<br>
> 密码：记录，供副路由器使用<br>
> ![NETGEAR_WIFI](imgs/2015-8-1/NETGEAR_WIFI.JPG "NETGEAR的WIFI配置")

### 启用主路由器的WDS功能 ###
> **页面位置：NETGEAR管理页 -> “高级”选项卡 -> 高级设置 -> 无线中继功能**<br>
> 勾选“启用无线中继功能(2.4GHz b/g/n)”<br>
> 选择“中心基站模式”<br>
> 中继器MAC地址 1：填写副路由器MAC地址（可在副路由器背面找到）<br>
> ![NETGEAR_WDS](imgs/2015-8-1/NETGEAR_WDS.JPG "NETGEAR的WDS配置")

### 设置副路由器LAN地址 ###
为了方便管理与避免地址冲突，设置副路由器LAN地址与主路由器不同，重启副路由器。 
> **页面位置：TP-LINK管理页 -> 网络参数 -> LAN口设置**<br>
> IP地址：192.168.1.254<br>
> ![TPLINK_LAN](imgs/2015-8-1/TPLINK_LAN.JPG "TP-LINK的LAN配置")

### 设置无线网络信息及WDS配置 ###
注意，此处部分参数需要与主路由器参数一致。
> **页面位置：TP-LINK管理页 -> 无线设置 -> 基本设置**<br>
> SSID号：填写副路由器WIFI名称，随意即可**注1*<br>
> 信道：需要与主路由器一致<br>
> 模式：默认即可
> 频段带宽：默认即可
> 勾选“开启WDS”

### 添加主路由器SSID ###
勾选“开启WDS后”，页面会自动扩展出WDS配置部分。点击“扫描”按钮，选择主路由器的SSID（WIFI名称）。
> （桥接的）SSID：无需修改，页面自动填写<br>
> （桥接的）BSSID：无需修改，页面自动填写<br>
> 无线地址格式：默认即可<br>
> 秘钥类型：与主路由器一致<br>
> WEP秘钥序号：一般情况下无需修改 **注2*<br>
> 秘钥：与主路由器WIFI连接密码一致<br>
> ![TPLINK_WDS](imgs/2015-8-1/TPLINK_WDS.JPG "TP-LINK的WDS配置")

### 副路由器设置 ###
保存页面后，WDS功能已启动。接下来设置副路由器的WIFI密码。注意，如果是开放的WIFI网络，此步骤可不设置。
> **页面位置：TP-LINK管理页 -> 无线设置 -> 无线安全设置**<br>
> 建议使用WPA-PSK/WPA2-PSK<br>
> 认证类型：默认即可，建议选择WPA2-PSK
> 加密算法：默认即可，建议选择AES
> PSK密码：也就是副路由器的WIFI连接密码。随意即可，建议与主路由器的WIFI密码一致。**注1*<br>
> ![TPLINK_WIFI_SAFE](imgs/2015-8-1/TPLINK_WIFI_SAFE.JPG "TP-LINK的WIFI安全配置")

接下来，由于主路由器已启用DHCP服务器功能，因此关闭副路由器的DHCP服务器功能。
> **页面位置：TP-LINK管理页 -> DHCP服务器 -> DHCP服务**<br>
> DHCP服务器：不启用<br>
> ![TPLINK_DHCP](imgs/2015-8-1/TPLINK_DHCP.JPG "TP-LINK的DHCP配置")

**注1*：当副路由器与主路由器的SSID及密码相同时，接入的设备可在两个路由器间无缝切换。也就是走出了主路由器的信号范围，手机会自动连接上副路由器。

**注2*：建议使用WPA2-PSK加密类型配合AES算法，较为安全。但某些旧设备可能不支持这种加密方式。例如SONY PSP1000就不支持WPA2，可以选用WPA-PSK/WPA2-PSK复合加密方式，由设备自动选择合适的加密方式。

### 配置完成 ###
此时，查看副路由器状态页，可以看到WDS功能启动成功。但注意，开启成功不代表可以正常上网。
> **页面位置：TP-LINK管理页 -> 运行状态**<br>
> ![TPLINK_STATUS](imgs/2015-8-1/TPLINK_STATUS.JPG "TP-LINK的运行状态页")

此时WDS设置已经完毕。理论上此时就可以上网了。但是发现连接副路由器后可以访问控制页面但不能浏览网页。想起NETGEAR设置了ARP保护，因此需要将副路由器添加到静态ARP表。
> **页面位置：NETGEAR管理页 -> “高级”选项卡 -> 安装 -> 局域网IP设置**<br>
> 将副路由器添加到IP-MAC绑定列表中即可。<br>
> MAC地址为副路由器MAC地址，IP地址为副路由器的LAN口地址（也就是管理页地址），设备名称随便写个自己看得懂的就行了。

## 后记 ##

1. 三星Galaxy S4（GT-I9500）在已连上WIFI的情况下，不会自动选择最优WIFI信号，哪怕他们SSID与密码一致。也就是不会在“信号差”的时候切换，只会在“没有信号”的时候进行切换。<br>不过，在主、副路由器信号范围内开启WIFI的话，会自动选择信号最佳的路由器进行连接。
2. 三星Galaxy S4（GT-I9500）在WIFI加密方式选择上，WPA-PSK优先于WPA2-PSK。
3. 一开始TP-LINK启用WDS后，不明原因无法上网。怀疑是固件问题，经查，使用的固件是2013年的。访问官网，发现新的固件`TL-WR845N V3.0_140210标准版`。该固件changelog中写明解决了WDS连接不稳定的问题，因此更新至此固件。问题解决。<br>固件下载地址：[TL-WR845N V3.0_140210标准版](http://service.tp-link.com.cn/detail_download_1395.html "http://service.tp-link.com.cn/detail_download_1395.html")<br>固件升级指导：[[TL-WR845N] 软件升级设置指导](http://service.tp-link.com.cn/detail_article_2120.html "http://service.tp-link.com.cn/detail_article_2120.html")
4. 如果主、副路由器设置同一个SSID，则接入设备连接时无法分辨所接入的路由器究竟是哪个。此时需要确保副路由器与主路由器的通信情况。我的笔记本连了副路由器，但是副路由器离主路由器比较远，网络状态比较差，此时我的笔记本虽然信号满格，但是网络质量也会比较差。因此副路由器的摆放位置也需要研究一下，要保证与主、副路由器之间通信顺畅。
5. 如果大家还不明白，可以访问TP-LINK官网的WDS功能设置指南。（早知道有这么好的东西就不用查这么久资料了T_T）<br>
资料：[TP-LINK无线路由器WDS功能应用方法](http://service.tp-link.com.cn/detail_article_106.html "http://service.tp-link.com.cn/detail_article_106.html")


【版权声明】

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />家用路由WDS中继设置 由 Rt Chen 创作，采用 <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">知识共享 署名 4.0 国际 许可协议</a>进行许可。

----------
END OF DOCUMENT