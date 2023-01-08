# 3d Printer
Settings, configuration, and notes...

Harware
 - Ender-5 (with Dual Z Mod)
 - BIGTREETECH-SKR-mini-E3-V3
 - TFT35 E3 V3.0.1 Touch Screen
 - BLTouch
 
Firmware
 - Marlin: v2.1.x

## Marlin Firmware
### Update
 1. Compile firmware using Platform-IO
     - Compile using the STM32G0B1RE_btt envoirnment
 2. Copy the `firmware.bin` file to an SD card
     - USB drive will not work
     - file location: `.pio/build/STM32G0B1RE_btt/firmware.bin`
 3. Insert SD card onto the printer
 4. Power on the printer (firmware will install)
 5. Clear cached data
     1. Press and hold the touch screen
     2. Select the Merlin interface
     3. Navigate and Select `Main->Configuration->Reset Defaults`


## Slicer Settings

Bed Size: X=220 Y=205

Start G-code
```
M201 X500.00 Y500.00 Z100.00 E5000.00 ;Setup machine max acceleration
M203 X500.00 Y500.00 Z10.00 E50.00 ;Setup machine max feedrate
M204 P500.00 R1000.00 T500.00 ;Setup Print/Retract/Travel acceleration
M205 X8.00 Y8.00 Z0.40 E5.00 ;Setup Jerk
M220 S100 ;Reset Feedrate
M221 S100 ;Reset Flowrate


G28 ;Home
G29 ;Level

G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Z Axis up
G1 X10.1 Y20 Z0.28 F5000.0 ;Move to start position
G1 X10.1 Y200.0 Z0.28 F1500.0 E15 ;Draw the first line
G1 X10.4 Y200.0 Z0.28 F5000.0 ;Move to side a little
G1 X10.4 Y20 Z0.28 F1500.0 E30 ;Draw the second line
G92 E0 ;Reset Extruder
G1 Z2.0 F3000 ;Move Z Axis up
```

End G-code
```
G91 ;Relative positioning
G1 E-2 F2700 ;Retract a bit
G1 E-2 Z0.2 F2400 ;Retract and raise Z
G1 X5 Y5 F3000 ;Wipe out
G1 Z10 ;Raise Z more
G90 ;Absolute positioning

G28 X0 Y0 ;Present print
M106 S0 ;Turn-off fan
M104 S0 ;Turn-off hotend
M140 S0 ;Turn-off bed

M84 X Y E ;Disable all steppers but Z
```

# Tips & Ticks

 * The SKR-mini-E3-V3 seems to fail at updating the framework 3 out of 4 times. If the printer isn't reconized, it could be because of a bad framework.bin, or it could be because it's just failing because it usually fails. 

 * If the z-offset isn't correct, use the Z Offset Wizard to get close to the desired offset. Then fine tune the z-offset, while printing, to get it perfict. The offset can be perminitaly set by updating the `NOZZLE_TO_PROBE_OFFSET` value in the firmware.
 
 * Make sure the Nozzle stays clean while heating. It's best to 1) pre-heat the printer, 2) clean the nozzle with a tool (the best you can), and 3) retract about 10mm before starting printing. Otherwise the filament will leak out. This causes it to glob up onto the nozzle. And as it prints, the filiment sticks to the glob instead of the bed.
