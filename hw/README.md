# Hardware for pico-pi

The folder contains the schematic files for the pico-pi header
board. This provides us with the all the additional hardware
functionality we need for a balloon tracker.

* RFM95W LoRa Radio
* u-Blox MAX-M8Q GPS
* 144MHz and 434MHz Radios
* Microcontroller to act as watchdog
* optional ADXL345 accelerometer

_[Schematics](pico-pi.sch.pdf)_

_[Board Drawings](pico-pi.kicad_pcb.pdf)_

_[3D Rendering](pico-pi.kicad_pcb.png)_

_[Gerbers](gerbers/)_

# Design Features

## GPS Amplifier + Antenna

We include a GPS
[Front End](http://www.infineon.com/dgdl/bgm1034N7.pdf?folderId=db3a30431f848401011fcbf2ab4c04c4&fileId=db3a304334fac4c60134fafa93ce0011)
and a
[Chip Antenna](http://www.johansontechnology.com/datasheets/antennas/1575AT43A0040.pdf). This
choice of antenna trades off sensitivity for low mass, while the Front
End mantains sufficient sensitivity and noise rejection.

## Power Conditioning

Pi Zero uses a
[PAM2306](http://www.mouser.com/ds/2/115/PAM2306-336770.pdf) for
power. Specifically it uses the KE variant for both 1.8V and 3.3V
outputs. The camera supply comes from this 3.3V line.

We can reduce the voltage on the 5V net to about 3.5V as we're not
using either the HDMI or USB sockets. This avoids having to include a
boost regulator, which saves cost and complexity.

A [supercapacitor](http://www.farnell.com/datasheets/1640988.pdf)
prevents voltage droop and brown-out in periods of high demand or
momentary solar panel shadowing. This allows us to use fewer solar
panels, and means we don't need to profile maximum current
consumption.

The Atmel SAMD20 microcontroller enables power to the rest of the
system, and also acts as watchdog. The GPS and RFM95W radio are
supplied by their own 3.3V LDO to reduce the load on the pi zero buck.

## ADXL345

Accelerometer date might be useful, in particular it will give us
pitch when taking photos. Could also be processed to quantify 'turbulence'.

The
[ADXL345](http://www.analog.com/media/en/technical-documentation/data-sheets/ADXL345.pdf)
is an Aerospace Grade part with many common libraries.
