# ASRock-Z690M-ITX-ax-hackintosh
华擎Z690M-ITX/ax OpenCore黑苹果

# 配置
**机箱** MeshRoom D （2*USB 3.0 5Gbps, 1*USB 3.0 Type-C 10Gbps<br>
**主板** ASRock-Z690M-ITX/ax<br>
**CPU** Intel Core i5-12600K<br>
**内存** 镁光英睿达Pro DDR4 3200MHz 32G\*2<br>
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
**接力，隔空投送，通用控制不能正常工作**，**加钱更换94360NG可以解决**。如果使用Monterey或更高版本系统，隔空投送仅支持其它设备投送到此电脑（Big Sur不受影响）。此电脑无法发送到其它设备。更换94360NG后删除EFI文件夹中的三个博通网卡驱动，然后顺手清理一下```config.plist```中kernel对应项可以让这三个功能正常使用。<br>
**USB缺少接口** 华擎Z690M-ITX/ax只有一个XHCI控制器，上面接了高达28个USB port，macOS下使用```XhciPortLimit``` quirk可以在旧版本中解决问题，Monterey和后续新系统不行。跟据我个人需求去掉了部分USB接口。主板上的前面板USB 3.0和Type-C均正常工作，其余USB 2.0接针均无法工作，后面板如图示。比较遗憾的是后面版的Type-C为USB 2.0速率，不过如果你前面板只有一个USB 3.0的A口，可以再把3.0加回来（总之就是加一个端口。<br>
**缺失Intel网卡驱动**如果你没有更换博通网卡，则无法驱动无线网卡。需要自行添加驱动以及修改```config.plist```<br>
**显存显示99%占用**。其实也不是什么大问题，反正系统本来也不能查看。第三方软件读到错误数据正常。<br>
其它的没说就是一切正常<br>
**风扇MAX转速无法获取**最高转速和最低转速获取值都是65535，当前转速不影响。仅影响想要使用Macs Fan Control手动调节的用户。
**Final Cut Pro新版本系统冲突** 新版Final Cut Pro，也就是Ventura后发布的版本，如果在Monterey上使用，会卡崩系统。原因很简单，Final Cut Pro后续对Metal 3优化了。

# 其它配置可用性<br>
## 性能升级<br>
CPU支持12/13/14代Intel桌面平台处理器。大小核心调度一直都是垃圾，想关就自己主板里关掉，我选择不关。另外，升级13/14代需要主板更新BIOS，用后置的BIOS刷写按键可以无CPU写。个人建议，iTX闷罐不建议使用太强的CPU。14700K估计很极限了。显卡只要是免驱都行，RX 5000/6000系都好用，自己找免驱列表。不过温度和风扇传感器的kext自己弄，我只保证6000系能显示。另外不建议讯景显卡。内存最高支持64G，请不要使用96G内存。最高频率可以开5000+，超频不关我事，但是建议先开机稳定运行后再超频，超频后概率导致无法一次成功开机，会重启一次。<br>
## 周边升级<br>
硬盘随你升级，不要用三星硬盘，不要用转接卡转企业级硬盘，作为系统盘大概率无法启动。如果要使用各类光污染，建议换主板，各种光污染可能会占用一个USB 2.0，本不富裕的接口数量雪上加霜。当然也可以直接不要macOS下的光效。显示器随便换，分辨率如果不够的话HiDPI自己搞。主板电池是无线网卡旁边贴的黄黄的东西，如果你要换网卡先得把那玩意后面的胶撕开，挡着一颗螺丝了。<br>
## 换主板<br>
不能保证可用性。目前这块主板除了已知问题其它都正常，换主板最常见的问题是睡眠唤醒问题。（而且你都点进来抄作业了，换主板这种事想必干不出来）<br>

# 安装操作<br>
按照双盘双系统的标准来说，硬盘又不贵。<br>
## 1. 修改BIOS<br>
连接有线或无线接收器键盘。开机狂按F2进简易模式，再F6进Advanced Mode<br>
### 关闭选项<br>
Fast Boot<br>
Secure Boot<br>
VT-d<br>
### 开启选项<br>
VT-x<br>
Above 4G decoding<br>
Hyper- Threading<br>
USB XHCI Hand off<br>
SATA mode<br>
### 修改<br>
CSM --> 全部改为UEFI<br>
### 别动<br>
Intel SGX<br>
CFG lock<br>

## 2. 安装系统<br>
**如何获取macOS镜像以及如何烧录镜像、如何放置EFI分区请自行查阅教程**
建议双系统而不是单系统，出问题了还能抢救一下。先安装Windows，再安装macOS。如果对于我的USB定制不满意，需要在Windows下使用USBToolBox自己定制。<br>
我关闭了```UTBMap.kext```和```USBToolBox.kext```这两个kext，如果自行定制，先关闭```USBPorts.kext```，把关掉的两个打开，自己定制一个```UTBMap.kext```替换kext文件夹里那个，然后安装macOS并使用hackintool完善。如果照抄作业，可以只安装macOS，应该没问题。<br>
**理论上，如果```USBPorts.kext```用起来没啥毛病，```UTBMap.kext```和```USBToolBox.kext```可以直接删除。**

## 3. 创建引导<br>
按照我的情况有些奇怪，Windows并没有创建EFI分区，而是在那块我根本没用过的m.2硬盘上创建了EFI,正常情况下，使用Disk Genius或者安装好macOS后使用OCC挂载EFI分区会看到一个EFI文件夹，里面有一个Microsoft文件夹。使用任意方式再挂载U盘EFI分区，这样可以脱离U盘启动。随后重启进入BIOS，将“UEFI OS”启动项提前到第一个。<br>
**如果是单盘双系统，安装完Windows需要把EFI分区拷贝到其它介质中，防止被覆盖导致无法启动**<br>
![image](https://github.com/Jimmy2004/ASRock-Z690M-ITX-ax-hackintosh/assets/59947552/7cf4cee0-59dd-4e00-a03d-029b6c3ef221)

# 已知问题补充<br>
1. 每次有线键鼠唤醒系统都会有bluetoothd进程崩溃记录，但是不影响功能（Monterey及后续系统特性）<br>
2. BCM94352z的蓝牙芯片组检测为```THIRD_PARTY_DONGLE```（Monterey及后续系统特性）<br>
3. BCM94352z成功驱动Wi-Fi、蓝牙后，打不开设置的共享选项（猜测是由第2条的特性导致的）<br>
4. 控制台无法流式传输Apple Watch的日志信息<br>

# 杂项后记<br>
1. 同款64G内存的话不要超频，不动时序的话Windows下稳定3600，macOS下```hibernatemode```设为```3```的时候睡眠唤醒后过几分钟随机假死。设为```0```的时候没问题，但是唤醒并不快。
