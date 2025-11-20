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

