# ASRock-Z690M-ITX-ax-hackintosh
华擎Z690M-ITX/ax OpenCore黑苹果

# 配置
**机箱** MeshRoom D （2*USB 3.0 5Gbps, 1*USB 3.0 Type-C 10Gbps<br>
**主板** ASRock-Z690M-ITX/ax<br>
**CPU** Intel Core i5-12600K<br>
**内存** 镁光英睿达Pro DDR4 32G\*2<br>
**显卡** MSI Gaming AMD Radeon RX 6600XT MECH 2X 8G OC<br>
**硬盘** 达墨双鱼座（M.2)+镁光M500(SATA 3)<br>
**网卡** BCM 94352z（替换原内置网卡）<br>
接下来无关紧要：<br>
**电源** 航嘉 750W铂金牌<br>
**散热** 利民PS120SE（与机箱冲突，无法盖侧板，实测对于12600K过于豪华）<br>
**天线** 随主板附赠<br>
外设：<br>
**键鼠**<br>
客制化的机械键盘，G502 Hero有线版鼠标，罗技MX Master 3鼠标，RAPOO布艺无线鼠标，Magic TrackPad白色第二代<br>
**显示器**<br>
戴尔 U2723QE显示器，物理分辨率3840*2160，连接至RX6600XT显卡的HDMI接口，显示规格为2160P@30bit<br>
DP接口据说会导致显示问题，需关闭DSC功能。<br>

# 使用环境<br>
110V 60Hz，美国<br>
路由器地区为美国，信道6（2.4G频段），信道48（5G频段）<br>

# 功能可用性
**系统版本 macOS Monterey 版本12.7.3，OpenCore版本0.9.6**<br>
**双硬盘双系统，macOS安装在m.2固态中，Windows 11安装在SATA固态中**<br>
最高支持“目前”的macOS Sonoma 版本14.3，由于个人喜欢的最新版本是Monterey，因为bug相对少，所以不更新。理论上这一套EFI对于Ventura支持也很好，Sonoma情况未知，请自行尝试，关于升级新版本遇到的的问题请不要提issues，不是不想搞，真的不会搞。<br>
Wi-Fi连接功能正常，支持2.4G/5G频段，由于BCM94352z（准确地说是所有黑苹果免驱网卡）都是Wi-Fi 5，所以只能贴着Wi-Fi 5速度的顶来跑，6GHz缺失，5GHz最高866Mbps。<br>
蓝牙功能正常，可以正常发现和连接绝大多数设备。<br>
**随航功能缺失**。无核显不能随航，11代及更高设备无法驱动核显。<br>
**接力，隔空投送，通用控制不能正常工作**，**加钱更换94360NG可以解决**。隔空投送仅支持其它设备投送到此电脑。此电脑无法发送到其它设备。更换94360NG后删除EFI文件夹中的三个博通网卡驱动，然后顺手清理一下```config.plist```中kernel对应项即可。<br>
