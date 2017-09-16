# Marlin-M150-Config

Compile settings:
- Board: Sanguino
- Processor: ATmega1284 16Mhz

Flash cmd line:
avrdude.exe -v -p atmega1284p -c arduino -P com3 -b 57600 -V -U flash:w:Marlin.ino.hex