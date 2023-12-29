# T-Display S3

Support for CircuitPython, Applications and Sensors

It's not yet supported by CircuitPython. A generic ESP32-S3 build works, but the display can't be used. And the parallelbus driver can't be used with a library and driver since it assumes consecutive pins, which is not the case for this board from Lilygo. But there is hope with CircuitPython 9.0.x since other parallel bus displays are supported! It might even work for the [T-HMI](https://github.com/Xinyuan-LilyGO/T-HMI/) and the unique [pin association](https://github.com/Xinyuan-LilyGO/T-HMI/blob/master/examples/lv_benchmark/pins.h).

- Lilygo github page: https://github.com/Xinyuan-LilyGO/T-Display-S3
- Another ESP32-S3 with parallel display bus: https://www.makerfabs.com/esp32-s3-parallel-tft-with-touch-7-inch.html
- The respective page for CircuitPython https://circuitpython.org/board/makerfabs_tft7/
- Board definitions: https://github.com/adafruit/circuitpython/tree/main/ports/espressif/boards/makerfabs_tft7
