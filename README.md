# Marlin-M150-Config

Compile settings:
- Board: Sanguino
- Processor: ATmega1284 16Mhz

##Flash cmd line:
avrdude.exe -v -p atmega1284p -c arduino -P com3 -b 57600 -V -U flash:w:Marlin.ino.hex

##Flash trough Arduino:
1. Install U8glib
    * `Sketch` -> `Include Library` -> `Manage Libraries...`
    * Search for and install `U8glib` by oliver

2. Install Sanguino
    * `File` -> `Preferences`
    * Add
    `https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json`
    to `Additional Boards Manager URLs`

3. Modify Sanguino `boards.txt`
    * Close Arduino
    * Locate Arduino15 folder
        - `C:\Users\<username>\AppData\Local\Arduino15` for Windows
        - `~/.arduino15` for Linux

    * Locate `boards.txt` in `packages/Sanguino/hardware/avr/1.0.2`
    (version number may change)
    * Add the following to the end of `boards.txt`
    (note that it is the same as sanguino.menu.cpu.atmega1284p but with
    a different name and upload speed)

            ## Malyan M150 W/ ATmega1284P 16MHz
            sanguino.menu.cpu.malyan_m150=Malyan M150
            sanguino.menu.cpu.malyan_m150.upload.maximum_size=130048
            sanguino.menu.cpu.malyan_m150.upload.maximum_data_size=16384
            sanguino.menu.cpu.malyan_m150.upload.speed=57600
            sanguino.menu.cpu.malyan_m150.bootloader.file=optiboot/optiboot_atmega1284p.hex
            sanguino.menu.cpu.malyan_m150.build.mcu=atmega1284p
            sanguino.menu.cpu.malyan_m150.build.f_cpu=16000000L

4. Configure Marlin
    * Copy `_Bootscreen.h`, `Configuration.h`, and `Configuration_adv.h` to `Marlin`

5. Flash Marlin
    * Turn on printer while pressing scroll wheel button
    * Plug printer in to computer with USB cable
    * Open `Marlin/Marlin.ino` with Arduino
    * Configure Arduino
        - `Tools` -> `Board` -> `Sanguino`
        - `Tools` -> `Processor` -> `Malyan M150`
        - `Tools` -> `Port` -> Select your port

    * `Sketch` -> `Upload` or click arrow in top right corner