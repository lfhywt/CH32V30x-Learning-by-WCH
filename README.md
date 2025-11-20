English version: [README_EN.md](README_EN.md)

# 沁恒 CH32V30x 系列学习教程

**芯片型号**：CH32V307VCT6  
**开发板型号**：CH32F207&V307V-R3-2v0  

本教程详细阐述从获取开发板到成功运行官方演示程序（Demo）的完整过程，旨在为初次使用 CH32V307 系列微控制器的开发者提供严谨、准确的指导。教程基于官方文档和实际操作经验，确保每一步骤的可重复性和可靠性。注意：所有操作需在安全的环境下进行，并遵守相关电子设备使用规范。

## 文件说明
- **CH343SER.ZIP** —— CH343 USB 转串口芯片驱动，用于串口通信支持。
- **WCH-LinkUtility.ZIP** —— 独立本地烧录工具，可用于脱离 IDE 的程序下载（本教程中可选使用）。
- **WCHISPTool Setup.exe** —— 单片机 ISP 编程工具（本教程暂未涉及，如需高级应用可参考官方文档）。
- **Demo** —— 官方演示工程文件夹，必须与 SRC 文件夹搭配使用，否则将缺少必要的外设驱动和启动文件。根据实际需求，可对 Demo 文件进行裁剪优化。
- **SRC** —— 官方提供的驱动文件库，包括外设驱动、启动代码等。建议将 SRC 和 Demo 置于同一路径下，或在工程设置中自定义包含路径（详见后续步骤）。

用户需自行下载并安装 **MounRiver Studio** IDE，该工具集成了 WCH-LinkUtility 烧录功能，并支持代码编译、调试。官方下载地址：https://www.mounriver.com/download。

安装前，请确保系统兼容性（Windows/macOS/Linux 支持），并安装必要的驱动。

> **注意**：Demo 和 SRC 的结合使用是工程编译成功的关键。如果路径配置错误，将导致链接错误或外设初始化失败。请严格按照本教程步骤操作。

## 硬件说明
本节描述硬件准备和连接细节，确保连接正确以避免烧录失败或硬件损坏。

- **开发板**  
  ![Image](https://github.com/user-attachments/assets/58398197-f396-463e-98c0-bb40362a0bd7)

- **烧录器**  
  ![Image](https://github.com/user-attachments/assets/3ab54ca3-66f0-48ea-b7f7-0d5fe531eac1)

使用杜邦线连接开发板与烧录器。连接时需注意以下要点：
- TXD 和 RXD 引脚必须交叉连接：开发板 TX → 烧录器 RX，开发板 RX → 烧录器 TX，以确保串口通信正常。
- 电源使用 Type-C 接口为开发板供电，烧录器可通过 USB 连接电脑供电。
- 连接前，确保所有引脚无短路风险，并断开电源以防静电损坏。

连接引脚对应表（严谨核对）：

| 烧录器引脚 | 开发板引脚 | 功能描述                  |
|------------|------------|---------------------------|
| SWCK      | SWCK      | SWD 时钟线               |
| SWIO      | SWIO      | SWD 数据线               |
| GND       | GND       | 地线                     |
| VDD       | VDD       | 电源（3.3V 或 5V，根据板子规格） |
| TXD       | RXD       | 串口发送（交叉连接）     |
| RXD       | TXD       | 串口接收（交叉连接）     |

连接示意图：  
![Image](https://github.com/user-attachments/assets/4c062033-8bda-4963-97c9-fdc49723bb6d)

> **安全警告**：连接不当可能导致短路或设备损坏。建议使用多米诺测试仪或万用表验证连接。首次操作时，推荐在有经验指导下进行。

## MounRiver Studio 使用教程
本教程仅演示官方 Demo 的运行过程，旨在快速上手。更多高级功能（如代码调试、外围设备配置）请参考官方文档。操作前，确保已安装 CH343SER 驱动并连接硬件。

- **主界面**：启动 IDE 后的默认界面，用于工程管理和代码编辑。  
  <img width="1920" height="996" alt="Image" src="https://github.com/user-attachments/assets/960f4694-5d50-43c4-9f65-f067ec5683a4" />

- **打开工程文件**：选择 Demo 文件夹中的工程文件（.mrs 或类似）。  
  <img width="959" height="600" alt="Image" src="https://github.com/user-attachments/assets/9b9fa999-292c-416d-b29b-1ce1a4fd6fd4" />

- **进入烧录工具**：点击菜单“工具” → “RISC-V Debugger”。  
  <img width="1326" height="779" alt="Image" src="https://github.com/user-attachments/assets/4179f4bb-618f-4df8-aea9-66f8086b48f7" />

- **更改语言**：支持中英文切换，根据个人偏好选择。  
  <img width="756" height="884" alt="Image" src="https://github.com/user-attachments/assets/74727fc7-6165-4cf1-9117-3287219e6ca7" />

- **选择芯片架构和型号**：选择 RISC-V 架构和 CH32V307VCT6 型号(根据实际情况选择)。点击“获取模式”检查烧录器状态。  
  <img width="815" height="950" alt="Image" src="https://github.com/user-attachments/assets/4601f3a8-4956-42c5-9489-c6e7bd3723c1" />

- **切换烧录器模式**：如果当前模式非 WCH-LinkRV，则需更改并设置。成功后，烧录器仅亮红灯，表示处于 RISC-V 模式。  
  <img width="816" height="220" alt="Image" src="https://github.com/user-attachments/assets/9523d733-684a-4451-a285-35373fa646ac" />  
  <img width="789" height="186" alt="Image" src="https://github.com/user-attachments/assets/11c21818-2d6b-4ec8-bfaa-bd74e6083c42" />

- **配置 SRC 路径**：确保 SRC 和 Demo 在同一目录下。驱动文件相对路径示例：..\SRC\Startup。根据需求可自定义修改路径，并在工程属性中更新包含目录。路径错误将导致编译失败。  
  <img width="624" height="199" alt="Image" src="https://github.com/user-attachments/assets/3d36037d-3bd1-4fc0-b258-90f32c934341" />

- **选择调试模式**：提供三种模式（Download、Attach、Run），根据需求选择（如初次测试推荐 Download 模式）。  
  <img width="1271" height="825" alt="Image" src="https://github.com/user-attachments/assets/17b1ff11-c98e-4288-8a33-7ef1955f2c8f" />

- **编译成功**：点击编译按钮，检查无错误。  
  <img width="738" height="219" alt="Image" src="https://github.com/user-attachments/assets/e2dd20a8-2403-4f7a-b53b-805bb829a4e2" />

- **烧录成功**：程序下载到开发板，确认无报错。  
  <img width="555" height="250" alt="Image" src="https://github.com/user-attachments/assets/f5432ce4-3afd-4cde-9c01-c2791b580d58" />

- **查看运行结果**：程序已成功烧录到开发板中。使用串口助手（如 SSCOM 或 Putty）监控输出。  
  <img width="1295" height="820" alt="Image" src="https://github.com/user-attachments/assets/d308450e-9a4b-4815-a52b-aa5788207714" />

- **串口设置**：波特率 115200，数据位 8，停止位 1，无奇偶校验。  
  <img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/860e0fb3-df79-46e7-aa45-7a72fa936805" />

- **运行成功**：观察串口打印信息，确认程序正常执行。  
  <img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/53f5bde5-7962-47c1-9ba8-2fd41b9aa5e8" />

> **常见问题排查**：若烧录失败，检查驱动安装、模式切换和连接线缆；若无串口输出，验证波特率和交叉连接。更多细节请查阅官方文档。

## 官方资料
- 沁恒官网下载中心：https://www.wch.cn/downloads/category/27.html

（包含数据手册、SDK 和工具更新）。

- 沁恒官网CH32V307专区：https://www.wch.cn/products/CH32V307.html
- 所有资料&SDK下载：https://www.wch.cn/downloads/category/27.html

本教程基于 2025 年 11 月 官方版本编写，如有更新，请以官网为准。如对本仓库有疑问或改进建议，欢迎提交 Issue。
