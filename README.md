## Description

Magpie test code to do the core activities of the system - Setting up ADC, DMA, SDHC, external RTC.  The RTC can be initialized and set a date.  Afterward, the date can be retrived to use for filename date/time stamp as well as assigning the same date/time stamp to the file system on the SD Card.  The code contains decimation filters for various sampling rate.

MSDK library modules that are used for the program got imported locally inside the project so that the code can be tweaked without modifying the original MDSK library modules.


## Software
ADI-MSDK

### Project Usage

Universal instructions on building, flashing, and debugging this project can be found in the **[MSDK User Guide](https://analogdevicesinc.github.io/msdk/USERGUIDE/)**.

### Project-Specific Build Notes
Currently CUSTOM is chosen for the board since it's modeled after Max32650 Ev-Kit which is the actual board being tested.

Modify .vscode/seetings.json line 18 "board":"CUSTOM" to correctly choose the board you are working with. 
The board options are
```
CUSTOM  (based on MAX32650 EV-Kit V1)

```
## Required Connections

-   Connect a USB cable between the PC and the USB/PWR-UART connector on the MAX32650 EV-Kit
-   Open an terminal application on the PC and connect to the console UART at 115200, 8-N-1.
-   Connect all the wires from MAX32650 Ev-Kit to match the FTHR2 pins on the GTC Board.  The updated connection from MAX32650 is in Red color. [EDIT 09/06/25]  We discovered that SPI1 cannot be used because we required QSPI 3-Wire mode for the ADC to send the data correctli to the MAX32650.  The updated connection from the Red Color is replaced by Purple Color.  Also, all the enable Voltage regulator pins should be disconnected if the jumper to enable the voltages are used otherwise the voltages go into the pins and preventing the SDHC from working correctly.  Might need to set the pin to high-z mode if we want to keep them connected.  Easier to not connect them for now since the GTC board doesn't need to have GPIO control of the power.

<img width="3415" height="1502" alt="image" src="https://github.com/user-attachments/assets/de14ba10-eb2b-454e-8030-009893900035" />

<br><br>
*** For Reference Only: Connections Prior to discovering that SPI3 is needed instead of SPI1
<img width="2284" height="1426" alt="image" src="https://github.com/user-attachments/assets/354c5a0f-5232-4afe-a2f9-01c7b723d1b7" />

<img width="2259" height="892" alt="image" src="https://github.com/user-attachments/assets/51d715ae-c319-4d2e-b445-c87b3a023cff" />


## Expected Output



