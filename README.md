# pico-pi

This repository contains the source and hardware for a High Altitude
Balloon (HAB) tracker based around a
[Raspberry Pi Zero](https://www.raspberrypi.org/products/pi-zero/). The
Pi Zero V1.3 includes a camera connector, so we can use a
[Sony IMX219 camera](https://uk.farnell.com/raspberry-pi/rpi-8mp-camera-board/raspberry-pi-camera-board-v2/dp/2510728)
to return live images.

This design is optimised for weight-constrained payloads that use
solar panels for power. If you're new to HAB or using a Latex weather
balloon, then check out the awesome
[Pi in the Sky](http://www.pi-in-the-sky.com) project instead!

# Hardware

[README.md](hw/README.md)

# Mass Budget

| Part | Mass |
| ---  | --- |
| Raspberry Pi Zero V1.3 | 9g |
| Raspberry Pi Camera | 3.5g |
| [5F Supercap](http://www.farnell.com/datasheets/1640988.pdf) | 7g |
| Solar panels to supply 400mA @ 4.8V | 15.2g |
| [pico-pi hardware](hw/) | 8g |
| Thermal insulation | 3g |
| Wire for antennas | 3g |

Current Total: `48.7g`
Target: `50g`

# License

[MIT](LICENSE.md)
