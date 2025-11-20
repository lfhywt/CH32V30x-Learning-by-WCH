中文版: [README.md](README.md)

# CH32V307 Quick Start Guide (English)

**Chip**: CH32V307VCT6  
**Development Board**: CH32F207 & V307V-R3-2v0  
**Goal**: Get your board up and running with official demos in under 30 minutes using MounRiver Studio.

This repository contains everything you need to go from unboxing to blinking LEDs/serial output on the CH32V307.

## Repository Contents
- `CH343SER.ZIP` – USB-to-UART driver
- `WCH-LinkUtility.ZIP` – Standalone programmer (optional)
- `WCHISPTool Setup.exe` – ISP tool (not used in this guide)
- `Demo/` – Official example projects (require SRC folder)
- `SRC/` – Official peripheral drivers and startup files

> **Important**: Demo projects must be used together with the `SRC` folder, otherwise compilation will fail due to missing drivers.

You need to download **MounRiver Studio** separately (it already includes the programmer):  
https://www.mounriver.com/download

## Hardware Connections

### Required Hardware
- CH32V307 development board
- WCH-LinkE / WCH-Link (DAPLink clone)
- Several Dupont wires
- USB Type-C cable (for board power)

### Wiring Table (WCH-Link ↔ Development Board)

| WCH-Link Pin | Development Board Pin | Note                  |
|--------------|------------------------|-----------------------|
| SWCK         | SWCK                   |                       |
| SWIO         | SWIO                   |                       |
| GND          | GND                    |                       |
| 3V3          | VDD                    | Power from programmer |
| TXD          | RXD                    | Cross-connect         |
| RXD          | TXD                    | Cross-connect         |

Connection diagram:  
![Wiring](https://github.com/user-attachments/assets/4c062033-8bda-4963-97c9-fdc49723bb6d)

## Step-by-Step with MounRiver Studio

1. Install MounRiver Studio and the CH343 driver.
2. Open any project in the `Demo` folder.
3. Make sure `SRC` and `Demo` are in the same directory, or adjust the include path:
   - Example relative path: `../SRC/Startup`
   - See screenshot:  
     ![Path](https://github.com/user-attachments/assets/3d36037d-3bd1-4fc0-b258-90f32c934341)

4. Open the programmer: **Tools → RISC-V Debugger**

5. Critical Settings:
   - Target: **RISC-V** + **CH32V307VCT6**
   - Debug Probe: Select your programmer → **Mode must be WCH-LinkRV**  
     (If it's in DAP mode, change it. Red LED only = correct RISC-V mode)

6. Build → Download → Run

7. Open any serial terminal (115800 baud) to see printf output.

Full screenshot guide (click to enlarge):

| Step                  | Screenshot |
|-----------------------|------------|
| Open project          | ![1](https://github.com/user-attachments/assets/9b9fa999-292c-416d-b29b-1ce1a4fd6fd4) |
| Programmer settings   | ![2](https://github.com/user-attachments/assets/4601f3a8-4956-42c5-9489-c6e7bd3723c1) |
| Switch to WCH-LinkRV  | ![3](https://github.com/user-attachments/assets/9523d733-684a-4451-a285-35373fa646ac) |
| Build success         | ![4](https://github.com/user-attachments/assets/e2dd20a8-2403-4f7a-b53b-805bb829a4e2) |
| Download success      | ![5](https://github.com/user-attachments/assets/f5432ce4-3afd-4cde-9c01-c2791b580d58) |
| Serial output         | ![6](https://github.com/user-attachments/assets/53f5bde5-7962-47c1-9ba8-2fd41b9aa5e8) |

## Official Resources
- WCH CH32V307 page: https://www.wch.cn/products/CH32V307.html
- All datasheets & tools: https://www.wch.cn/downloads/category/27.html
- MounRiver Studio: https://www.mounriver.com/

---

**Star this repo if it helped you get started!**  
Issues and pull requests are welcome.
