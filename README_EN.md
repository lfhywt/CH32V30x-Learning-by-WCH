中文版: [README.md](README.md)

# WCH CH32V30x Series Learning Tutorial

**Chip Model**: CH32V307VCT6  
**Development Board Model**: CH32F207&V307V-R3-2v0  

This tutorial provides a detailed explanation of the complete process from acquiring the development board to successfully running the official demonstration programs (Demos). It aims to offer rigorous and accurate guidance for developers using the CH32V307 series microcontroller for the first time. The tutorial is based on official documentation and practical operational experience, ensuring the reproducibility and reliability of each step. Note: All operations should be performed in a safe environment and in compliance with relevant electronic device usage standards.

## File Descriptions
- **CH343SER.ZIP** — CH343 USB-to-Serial chip driver, used for serial communication support.
- **WCH-LinkUtility.ZIP** — Standalone local programming tool, which can be used for program downloading independent of the IDE (optional in this tutorial).
- **WCHISPTool Setup.exe** — Microcontroller ISP programming tool (not covered in this tutorial; refer to official documentation for advanced applications).
- **Demo** — Official demonstration project folder, which must be used in conjunction with the SRC folder; otherwise, essential peripheral drivers and startup files will be missing. The Demo files can be trimmed and optimized according to specific needs.
- **SRC** — Official driver file library, including peripheral drivers, startup code, etc. It is recommended to place SRC and Demo in the same directory, or customize the include paths in the project settings (see subsequent steps for details).

Users must download and install the **MounRiver Studio** IDE themselves. This tool integrates the WCH-LinkUtility programming function and supports code compilation and debugging. Official download address: https://www.mounriver.com/download. Before installation, ensure system compatibility (supports Windows/macOS/Linux) and install the necessary drivers.

> **Note**: The combined use of Demo and SRC is critical for successful project compilation. Incorrect path configuration will lead to linker errors or peripheral initialization failures. Please follow the tutorial steps strictly.

## Hardware Description
This section describes the hardware preparation and connection details to ensure correct connections and avoid programming failures or hardware damage.

- **Development Board**  
  ![Image](https://github.com/user-attachments/assets/58398197-f396-463e-98c0-bb40362a0bd7)

- **Programmer**  
  ![Image](https://github.com/user-attachments/assets/3ab54ca3-66f0-48ea-b7f7-0d5fe531eac1)

Use Dupont wires to connect the development board to the programmer. Pay attention to the following points during connection:
- The TXD and RXD pins must be cross-connected: Development board TX → Programmer RX, Development board RX → Programmer TX, to ensure normal serial communication.
- Use a Type-C interface for powering the development board; the programmer can be powered via USB connection to the computer.
- Before connecting, ensure there is no risk of short circuits on any pins, and disconnect power to prevent electrostatic damage.

Connection Pin Mapping Table (Verify Rigorously):

| Programmer Pin | Board Pin | Function Description              |
|----------------|-----------|-----------------------------------|
| SWCK           | SWCK      | SWD clock line                    |
| SWIO           | SWIO      | SWD data line                     |
| GND            | GND       | Ground                            |
| VDD            | VDD       | Power (3.3V or 5V, based on board specifications) |
| TXD            | RXD       | Serial transmit (cross-connected) |
| RXD            | TXD       | Serial receive (cross-connected)  |

Connection Diagram:  
![Image](https://github.com/user-attachments/assets/4c062033-8bda-4963-97c9-fdc49723bb6d)

> **Safety Warning**: Improper connections may cause short circuits or device damage. It is recommended to use a multimeter or continuity tester to verify connections. For first-time operations, it is advisable to proceed under experienced guidance.

## MounRiver Studio Usage Tutorial
This tutorial demonstrates only the process of running the official Demos for quick onboarding. For more advanced features (such as code debugging or peripheral configuration), please refer to the official documentation. Before operating, ensure the CH343SER driver is installed and the hardware is connected.

- **Main Interface**: The default interface after launching the IDE, used for project management and code editing.  
  <img width="1920" height="996" alt="Image" src="https://github.com/user-attachments/assets/960f4694-5d50-43c4-9f65-f067ec5683a4" />

- **Open Project File**: Select the project file (.mrs or similar) from the Demo folder.  
  <img width="959" height="600" alt="Image" src="https://github.com/user-attachments/assets/9b9fa999-292c-416d-b29b-1ce1a4fd6fd4" />

- **Enter Programming Tool**: Click the menu "Tools" → "RISC-V Debugger".  
  <img width="1326" height="779" alt="Image" src="https://github.com/user-attachments/assets/4179f4bb-618f-4df8-aea9-66f8086b48f7" />

- **Change Language**: Supports switching between Chinese and English; select based on personal preference.  
  <img width="756" height="884" alt="Image" src="https://github.com/user-attachments/assets/74727fc7-6165-4cf1-9117-3287219e6ca7" />

- **Select Chip Architecture and Model**: Choose the RISC-V architecture and CH32V307VCT6 model (select according to the actual model). Click "Get Mode" to check the programmer status.  
  <img width="815" height="950" alt="Image" src="https://github.com/user-attachments/assets/4601f3a8-4956-42c5-9489-c6e7bd3723c1" />

- **Switch Programmer Mode**: If the current mode is not WCH-LinkRV, change and set it. Upon success, the programmer will show only a red light, indicating RISC-V mode.  
  <img width="816" height="220" alt="Image" src="https://github.com/user-attachments/assets/9523d733-684a-4451-a285-35373fa646ac" />  
  <img width="789" height="186" alt="Image" src="https://github.com/user-attachments/assets/11c21818-2d6b-4ec8-bfaa-bd74e6083c42" />

- **Configure SRC Path**: Ensure SRC and Demo are in the same directory. Driver file relative path example: ..\SRC\Startup. Customize the path as needed and update the include directories in the project properties. Path errors will cause compilation failures.  
  <img width="624" height="199" alt="Image" src="https://github.com/user-attachments/assets/3d36037d-3bd1-4fc0-b258-90f32c934341" />

- **Select Debug Mode**: Provides three modes (Download, Attach, Run); choose based on needs (recommend Download mode for initial testing).  
  <img width="1271" height="825" alt="Image" src="https://github.com/user-attachments/assets/17b1ff11-c98e-4288-8a33-7ef1955f2c8f" />

- **Successful Compilation**: Click the compile button and check for no errors.  
  <img width="738" height="219" alt="Image" src="https://github.com/user-attachments/assets/e2dd20a8-2403-4f7a-b53b-805bb829a4e2" />

- **Successful Programming**: Download the program to the development board and confirm no errors.  
  <img width="555" height="250" alt="Image" src="https://github.com/user-attachments/assets/f5432ce4-3afd-4cde-9c01-c2791b580d58" />

- **View Operation Results**: The program has been successfully programmed to the development board. Use a serial terminal (such as SSCOM or PuTTY) to monitor the output.  
  <img width="1295" height="820" alt="Image" src="https://github.com/user-attachments/assets/d308450e-9a4b-4815-a52b-aa5788207714" />

- **Serial Settings**: Baud rate 115200, data bits 8, stop bits 1, no parity, no flow control.  
  <img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/860e0fb3-df79-46e7-aa45-7a72fa936805" />

- **Successful Execution**: Observe the serial print information to confirm normal program execution.  
  <img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/53f5bde5-7962-47c1-9ba8-2fd41b9aa5e8" />

> **Common Troubleshooting**: If programming fails, check driver installation, mode switching, and connection cables; if there is no serial output, verify the baud rate and cross-connections. For more details, refer to the official documentation.

## Official Resources
- WCH Official Download Center: https://www.wch.cn/downloads/category/27.html (includes datasheets, SDKs, and tool updates).
- WCH CH32V307 Page: https://www.wch.cn/products/CH32V307.html
- All Datasheets & Tools: https://www.wch.cn/downloads/category/27.html

This tutorial is based on the official version as of November 2025; for any updates, please refer to the official website. If you have questions or suggestions for improvement regarding this repository, feel free to submit an Issue.
