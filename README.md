# 沁恒-CH32V30x系列
芯片型号:CH32V307VCT6 开发板型号:CH32F207&V307V-R3-2v0


本文将描述如何从拿到开发板到跑通的教程


## 文件说明
- CH343SER.ZIP  —— 驱动
- WCH-LinkUtility.ZIP  —— 本地烧录工具
- WCHISPTool Setup.exe  ——单片机编程工具(暂未使用)
- Demo 必须搭配SRC使用，否则会缺少驱动文件，可根据需要裁剪demo文件
- SRC 官方的驱动文件，需要将SRC和Demo放在同一路径或自定义路径，后续会说如何自定义


用户需自己下载MounRiver_Studio，这款IDE集成了上述的WCH-LinkUtility并且可以编译程序.

## 硬件说明
- 开发板
![Image](https://github.com/user-attachments/assets/58398197-f396-463e-98c0-bb40362a0bd7)


- 烧录器
![Image](https://github.com/user-attachments/assets/3ab54ca3-66f0-48ea-b7f7-0d5fe531eac1)

使用杜邦线将开发板的SWCK，SWIO，GND，VDD ，TXD，RXD与烧录器相连，注意开发板与烧录器的TX和RX需要交叉连接，即(开发板TX)->(烧录器RX)，(开发板RX)->(烧录器TX).使用type-C 给开发板供电，如下图所示：
![Image](https://github.com/user-attachments/assets/4c062033-8bda-4963-97c9-fdc49723bb6d)

- MounRiver_Studio使用教程(本文只演示Demo案例，具体详细查询官网)

主界面:

<img width="1920" height="996" alt="Image" src="https://github.com/user-attachments/assets/960f4694-5d50-43c4-9f65-f067ec5683a4" />


打开工程文件：

<img width="959" height="600" alt="Image" src="https://github.com/user-attachments/assets/9b9fa999-292c-416d-b29b-1ce1a4fd6fd4" />


点击工具，进入烧录工具

<img width="1326" height="779" alt="Image" src="https://github.com/user-attachments/assets/4179f4bb-618f-4df8-aea9-66f8086b48f7" />


可以更改语言，支持中英文

<img width="756" height="884" alt="Image" src="https://github.com/user-attachments/assets/74727fc7-6165-4cf1-9117-3287219e6ca7" />


选择好芯片的架构和型号，一定看仔细了，点击获取WCH-Link的模式

<img width="815" height="950" alt="Image" src="https://github.com/user-attachments/assets/4601f3a8-4956-42c5-9489-c6e7bd3723c1" />


如果模式不是WCH-LinkRV，更改模式，然后设置

<img width="816" height="220" alt="Image" src="https://github.com/user-attachments/assets/9523d733-684a-4451-a285-35373fa646ac" />


提示处于RISC-V模式，此时的烧录器只会亮红灯，说明设置成功。

<img width="789" height="186" alt="Image" src="https://github.com/user-attachments/assets/11c21818-2d6b-4ec8-bfaa-bd74e6083c42" />



配置好烧录器后，就可以开始跑例程源码了，首先确保SRC的路径是否正确。先确保SRC和Demo在同一个路径下面。驱动文件的相对路径举例(其中之一)：..\SRC\Startup，根据需求后续可自行修改。

