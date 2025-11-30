# Firmware flashing

To flash the firmware, you'll need an SWD programmer, I'm using an ST-Link V2
and I can't guarantee that anything else will work, but you can try.  

The pinout of the headers on the back of the PCB is as follows:  

| Pin | Function    |
|-----|-------------|
| 1   | SWDIO       |
| 2   | VCC (3.3V)  |
| 3   | SWCLK/BOOT0 |
| 4   | GND         |
| 5   | nRST        |
| 6   | GND         |

Keep in mind, the order is right to left, top to bottom, ask marked on the
silkscreen.  

You'll need STLINK Tools [from this repo](https://github.com/stlink-org/stlink).  

To dump the firmware: `st-flash read firmware.bin 0x0 32k`  
It's recommended to dump the firmware multiple times and compare the checksums
to make sure you have a working firmware dump.  

To flash the firmware: `st-flash --reset --format binary write firmware.bin 0x8000000`  

### Unbricking

Should you ever find yourself unable to flash (happens with Arduino), here's
what works for me.  

Connect SWD as normal, and connect the nRST pin to GND.  
Get the flash command ready in a terminal or your favorite tool, but wait
before launching the flash.  
In another terminal, run this command, it will fail saying it can't find any chip id:
`st-flash --reset --connect-under-reset --format binary write original_firmware_dump.bin 0x08000000`  
Then launch the flash command quickly, as soon as you disconnect the reset pin from GND.  
