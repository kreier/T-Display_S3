# History for this project for students

The current solution traces back to 2015 and my first steps with physical computing and __Arduino Uno__. The [temp.hofkoh.de](https://github.com/kreier/temp.hofkoh.de) project from 2013 was not yet student centered. Some of the constraints will be visible with this comparison table:

| Board              | MHz | kByte RAM | kByte Flash | USB drive |   input  | output | display | WiFi | Bluetooth | LiPo |  notes  |
|--------------------|----:|----------:|------------:|:---------:|:--------:|:------:|:-------:|:----:|:---------:|:----:|:-------:|
| Arduino Uno        |  16 |         2 |          16 |           |   none   |   led  |   16x2  |      |  external |      |         |
| Arduino Mega       |  16 |         8 |         256 |           |   none   |   led  |         |      |  external |      |         |
| ESP8266            |  80 |        80 |        4000 |           |   GPIO0  |   led  |  128x64 |   x  |           |      |         |
| T-Display ESP32    | 240 |       520 |        4000 |           | 2 button |   led  | 240x135 |   x  |    4.0    |   x  |         |
| T8 ESP32-S2 ST7789 | 240 |      8000 |        4000 |     x     |   GPIO0  |        | 240x135 |   x  |    BLE    |   x  | SD card |
| T-Display rp2040   | 133 |       264 |        4000 |     x     | 2 button |   led  | 240x135 |      |           |   x  |         |
| T-PicoC3           | 133 |       264 |        4000 |     x     | 2 button |   led  | 240x135 |   x  |           |   x  |         |
| T-Display S3       | 240 |      8000 |       16000 |     x     | 2 button |   led  | 320x170 |   x  |    BLE    |   x  |         |

At one point or another you run into these limitations, and spend a lot of time to overcome them.

## 2015 Start with Arduino Uno

I got my first Arduino Uno and had the onboard LED blinking as the "Hello world!" of MCUs. Soon I added 1602 and 2004 displays with the i2c bus, and then sensors like a BME180 for pressure.

This combination with a 9V battery as energy source went right into praxis for my "science explorer" class in Scheeßel 2015-2016 with visiting grade 4 students. Look here:

video of vacuum machine.

I was not sure if my Nexus 4 would survice the vacuum "for scientific reasons".

## 2019 Robotics class at AISVN

4 wheels and Arduino Uno with shield. Limit with the only 3 available timers. Bluetooth as extra serial module attached. No more pins left. 1602 display

![robot](https://raw.githubusercontent.com/kreier/T400/main/docs/T400-robotarm.jpg)

## 2020 Upgrade to ESP8266

https://github.com/kreier/T400

## 2023 Circuitpython for T-Display rp2040 available

We are lacking the Wifi, but other than that it is a great deal for just 10 Dollars. Only the implementation of Circuitpython hit a roadblock for more than a year because of a missing USB-PID that the manufacturer LilyGo was not providing.

The solution: We applied for it as a student project. And now we have it registered as Nr. 2023 for our SSIS robotics club! 

## 2024 Support for parallel bus displays on the T-Display S3

I made further progress in Circuitpython and compiling my own firmwares. Installed again on my Windows 11 PC as WSL Ubuntu 22.04 it works without problems. Limor Fried (Lady Ada from Adafruit) explains the history of MicroPython and CircuitPython [in this video at the Espressif DevCon22](https://youtu.be/1eZQzn0PX-A?si=4XkupHrjkIC9J43_). The Espressif boards need a different toolchain and build process than all the other ports, as [explained here in the "Building CircuitPython" tutorial by Dan Halbert](https://learn.adafruit.com/building-circuitpython/espressif-build). The reason was explained by [Scott Shawcroft](https://github.com/tannewt) in his [2 hour deep dive podcast](https://www.youtube.com/watch?v=5zq8RHXVdSI) from April 2020 when support for the ESP32-S2 was in development. It is because the architecture used by Espressif is a [Tensilica](https://en.wikipedia.org/wiki/Tensilica) Xtensa LX6 or LX7 core with its own 32-bit instruction set. All other boards use some from of ARM architecture ([Cortex-M0](https://en.wikipedia.org/wiki/ARM_Cortex-M) for raspberry pico rp2040, [Cortex-M4](https://en.wikipedia.org/wiki/ARM_Cortex-M) for STM32F411 and Cortex M7 for the NXP iMX RT1011 in the [Metro M7](https://www.adafruit.com/product/4950)). So it's ARM or Cadence ...

Now I actually made some contributions to CircuitPython:

- Updated [T-Display rp2040](https://circuitpython.org/board/lilygo_t_display_rp2040/)
- Included T-PicoC3
- Included T-Display 4M
- Included 01Space QTPy OLED
- Working on T-Display S3 with parallel bus to display

This will be a challenge - support a parallel display. Let's see ...
