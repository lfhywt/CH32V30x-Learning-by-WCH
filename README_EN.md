中文版: [README.md](README.md)

WCH — CH32V30x Series

Chip model: CH32V307VCT6
Development board model: CH32F207 & V307V-R3-2v0

This document describes a tutorial on how to go from receiving the development board to getting it running.

File description

CH343SER.ZIP —— Driver

WCH-LinkUtility.ZIP —— Local flashing tool

WCHISPTool Setup.exe —— MCU programming tool (not used in this tutorial)

Demo must be used together with SRC, otherwise driver files are missing; you may trim demo files as needed.

SRC Official driver files. SRC and Demo need to be placed under the same path or a custom path — instructions for customizing follow.

Users must download MounRiver_Studio themselves. This IDE integrates the above WCH-LinkUtility and can build the programs.

Hardware description

Development board


Programmer


Use jumper wires to connect the development board’s SWCK, SWIO, GND, VDD, TXD, RXD to the programmer. Note that the TX and RX of the development board and the programmer must be crossed, i.e. (board TX) -> (programmer RX), (board RX) -> (programmer TX). Power the development board via Type-C as shown below:


MounRiver_Studio usage tutorial (this document demonstrates only the Demo case; consult the official site for full details)

Main interface:

<img width="1920" height="996" alt="Image" src="https://github.com/user-attachments/assets/960f4694-5d50-43c4-9f65-f067ec5683a4" />

Open project file:

<img width="959" height="600" alt="Image" src="https://github.com/user-attachments/assets/9b9fa999-292c-416d-b29b-1ce1a4fd6fd4" />

Click Tools to enter the programming tool:

<img width="1326" height="779" alt="Image" src="https://github.com/user-attachments/assets/4179f4bb-618f-4df8-aea9-66f8086b48f7" />

You can change the language; both Chinese and English are supported:

<img width="756" height="884" alt="Image" src="https://github.com/user-attachments/assets/74727fc7-6165-4cf1-9117-3287219e6ca7" />

Select the chip architecture and model carefully, then select the WCH-Link mode:

<img width="815" height="950" alt="Image" src="https://github.com/user-attachments/assets/4601f3a8-4956-42c5-9489-c6e7bd3723c1" />

If the mode is not WCH-LinkRV, change the mode and configure it:

<img width="816" height="220" alt="Image" src="https://github.com/user-attachments/assets/9523d733-684a-4451-a285-35373fa646ac" />

A prompt indicates RISC-V mode; at this point the programmer will light red only, which means the configuration succeeded.

<img width="789" height="186" alt="Image" src="https://github.com/user-attachments/assets/11c21818-2d6b-4ec8-bfaa-bd74e6083c42" />

After configuring the programmer, you can start running the example source code. First ensure the SRC path is correct. Make sure SRC and Demo are in the same directory. Example relative path for driver files (one example): ..\SRC\Startup; you can modify this later as needed.

<img width="624" height="199" alt="Image" src="https://github.com/user-attachments/assets/3d36037d-3bd1-4fc0-b258-90f32c934341" />

Three modes are available — choose according to your needs:

<img width="1271" height="825" alt="Image" src="https://github.com/user-attachments/assets/17b1ff11-c98e-4288-8a33-7ef1955f2c8f" />

Build succeeded:

<img width="738" height="219" alt="Image" src="https://github.com/user-attachments/assets/e2dd20a8-2403-4f7a-b53b-805bb829a4e2" />

Programming succeeded:

<img width="555" height="250" alt="Image" src="https://github.com/user-attachments/assets/f5432ce4-3afd-4cde-9c01-c2791b580d58" />

At this point the program has been successfully programmed into the development board. Open a serial terminal to inspect:

<img width="1295" height="820" alt="Image" src="https://github.com/user-attachments/assets/d308450e-9a4b-4815-a52b-aa5788207714" />

Settings:

<img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/860e0fb3-df79-46e7-aa45-7a72fa936805" />

Run successful:

<img width="1371" height="869" alt="Image" src="https://github.com/user-attachments/assets/53f5bde5-7962-47c1-9ba8-2fd41b9aa5e8" />

Official resources: https://www.wch.cn/downloads/category/27.html
