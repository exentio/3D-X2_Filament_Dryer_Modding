# 3D-X2 Filament Dryer Modding

This is a filament dryer that can be found for cheap on Aliexpress, by word
salad brands like Kingroon and Keepang.  

I paid €27,48 for mine after discounts and I bought it with the intention to
build a custom PCB for it with a better temperature sensor and an ESP32, sure
to be able to reuse the fan, heater, and other hardware like the bearing and
rods to make the filament roll when pulled by the printer.  

What I wasn't expecting was that the PCB would've been so simple to
reverse-engineer, and to find an STM32 (precisely, STM32G030F6P6), not only
with SWD pins exposed, but also with no flash protection whatsoever.  

The repo of this goal is to document my progress with modding this dryer and
make it available to everyone.  

### Hardware specifications and other details

+ Rated voltage/power: 24V 2A (48W)  
+ Included power supply: 24V 2.5A (mine came with this, may vary)  
+ Timer settings (stock firmware): 0.5 to 24 hours with a continuous on mode  
+ Heating temperatures (stock firmware): 50/60/70°C  
+ Heating element: polyimide flexible heater, glued onto a curved metal sheet
sitting under the filament roll  
+ Fan: 24V 40mm blower (actual fan diameter 30mm)  
+ Sensors:
  + SMD thermistor, likely 10KΩ rated value, soldered in the middle of the heater  
  + 2-pin relative humidity sensor glued on the bottom of the dryer, likely a
  CJ-HR31D resistive humidity sensor  
+ Other hardware info:  
  + Bearing sizes: 11mm outer diameter, 4mm internal hole, 4mm thickness  
  + Filament rolling rods: 6mm diameter, 4mm diameter taper at ends, 83mm long
  without taper, 91mm with taper (4mm on each side)  
