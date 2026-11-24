# Music-Player-ESP32
A dual-core ESP32-S3 MP3 player with a real-time OLED wave visualizer.

## Hardware Used
* **Microcontroller:** ESP32-S3-Zero
* **Display:** 0.96" SSD1306 OLED (128x64, I2C)
* **Amplifier:** MAX98357A I2S Class-D Amp
* **Speaker:** 8-ohm, 1W Speaker

## Wiring
| Component | Pin | ESP32-S3 GPIO |
| :--- | :--- | :--- |
| **OLED (I2C)** | SDA / SCL | GPIO 5 / GPIO 4 |
| **MAX98357A (I2S)** | BCLK / LRC / DIN | GPIO 15 / GPIO 16 / GPIO 17 |

## How It Works
* **Audio:** Decodes an MP3 file stored directly in flash memory (`PROGMEM`) and outputs via I2S.
* **Dual-Core Split:** Uses FreeRTOS to pin MP3 decoding to **Core 0** while **Core 1** handles the OLED wave animation, preventing audio stuttering.

## Libraries Required
* `Adafruit_GFX` & `Adafruit_SSD1306`
* `ESP8266Audio`
