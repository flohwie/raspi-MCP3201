# raspi-MCP3201

This module provides functions to read the MCP3201 (2.7V 12-Bit A/D Converter with SPI Serial Interface).
please refer to the datasheet: http://ww1.microchip.com/downloads/en/DeviceDoc/21290F.pdf

The MSB is clocked out on the falling edge of the 3rd clock pulse. After the first eight clocks have been sent
to the device, the MCU receive buffer will contain two unknown bits (??), the null bit (NB), and the highest order five bits (B11-B7) of the conversion. After the second eight clocks have been sent, the receive buffer will contain the lowest order seven bits (B6-B0) and the B1 bit repeated as the A/D converter has begun to shift out LSB data with the extra (i.e. the 16th) clock.

***Requires SPI:***

dtparam=spi=on in /boot/config.txt

sudo pip3 install spidev (https://pypi.python.org/pypi/spidev)


***Pin setup MCP3201:***

VDD (8) --> 3V3

VREF(1) --> 3V3

VSS (4) --> GND


IN+ (2): positive analog input (min: IN-, max: VREF + IN-)

IN- (3): negative analog input (VSS +- 100 mV), connect to GND


***Raspberry Pi (Model B2, Pi2, and Pi3):***

CD/SHDN (5): chip select/shutdown --> Raspberry Pi BCM GPIO pin 8 (CE0)

CLK (7): serial clock --> Raspberry Pi BCM GPIO pin 11 (SCLK)

DOUT (6): serial data output --> Raspberry Pi GPIO BCM pin 9 (MISO)


