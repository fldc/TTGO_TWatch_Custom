# LilyGO T-Watch Custom Firmware

## Introduction

The goal of this project is to provide a custom firmware for the LilyGO T-Watch S3 for my own enjoyment. The firmware is based on the official [LilyGO T-Watch Library]

## Installation

1. Install [Visual Studio Code](https://code.visualstudio.com/) and [Python](https://www.python.org/)
2. Search for the `PlatformIO` plugin in the `VisualStudioCode` extension and install it.
3. After the installation is complete, you need to restart `VisualStudioCode`
4. After restarting `VisualStudioCode`, select `File` in the upper left corner of `VisualStudioCode` -> `Open Folder` -> select the `TTGO_TWatch_Library` directory
5. Wait for the installation of third-party dependent libraries to complete
6. Click on the `platformio.ini` file, and in the `platformio` column, cancel the sample line that needs to be used, please make sure that only one line is valid
7. Click the (✔) symbol in the lower left corner to compile
8. Connect the board to the computer USB
9. Click (→) to upload firmware
10. Click (plug symbol) to monitor serial output

## ESP32 basic examples

- [BLE Examples](https://github.com/espressif/arduino-esp32/tree/master/libraries/BLE)
- [WiFi Examples](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi)
- [SPIFFS Examples](https://github.com/espressif/arduino-esp32/tree/master/libraries/SPIFFS)
- [OTA Examples](https://github.com/espressif/arduino-esp32/tree/master/libraries/ArduinoOTA)
- [FFat Examples](https://github.com/espressif/arduino-esp32/tree/master/libraries/FFat)
- For more examples of esp32 chip functions, please refer to [arduino-esp32-libraries](https://github.com/espressif/arduino-esp32/tree/master/libraries)

## FAQ

1. Unable to upload to watch
    1. Make sure that the T-Watch is turned on, you can check it according to the following method, open the computer device manager, check the port, plug the USB port into the computer, and if the new COM device is displayed, it has been turned on, if it is not displayed, press the crown Press the button on the button for one second, and then the device port will pop up, click upload at this time
2. The USB port keeps flashing in the computer

- This is a phenomenon caused by the abnormal operation of the program, or the selection of the wrong configuration, and the continuous restart of the esp32. At this time, the problem of not being able to upload can only be solved by manually entering the download mode of the watch
Please follow the steps below
   1. Remove the back cover
   2. Insert Micro-USB
   3. Open Windows Device Manager
   4. Press and hold the crown of the watch until the USB device does not appear in the Windows COM port
   5. Press the button in the picture below and keep pressing
    ![Button location for manual download mode](./images/BUTTON.jpg)
   6. Press the crown button for one second
   7. Now the COM port is fixed
   8. Select Port in Arduino IDE
   9. Click Upload

3. Where to query the pin definition?
    1. Look [here](./src/utilities.h)
4. The screen is not displayed after uploading the sketch?
    1. Please check the fourth line of [Arduino IDE Quick Start]()
5. Power Domain

    | Power Domain | Role                          |
    | ------------ | ----------------------------- |
    | ALDO1        | RTC backup battery (3.1-3.3v) |
    | ALDO2        | Backlight                     |
    | ALDO3        | 3V3 for FT6336 and st7889     |
    | ALDO4        | SX1262                        |
    | BLDO2        | DRV2605 Enable pin            |
    | DC1          | ESP32 3V3                     |
    | VRTC         | Nothing                       |

6. Battery
   1. Lilygo T-Watch fits 502530 size (5x25x30mm) batteries of any chemistry supported by the AXP2101.
7. **esp_vad.h: No such file or directory**
   - **Please use 2.0.9. The new version has changed too much and has not yet been adapted.**
