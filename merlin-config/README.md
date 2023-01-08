# Merlin Firmware Config
This configuation is based on the End-3 config for the BigTreeTech SKR Mini E3 3.0 controller board, provided by Merlin (https://github.com/MarlinFirmware/Configurations/tree/import-2.1.x/config/examples/Creality/Ender-3/BigTreeTech%20SKR%20Mini%20E3%203.0).
When updating my firmware, my approch is to:
 1) pull the latest configuration for the board (the ender-3 is the closest printer)
 2) Identify the changes I made from the history
 3) Apply those changes to the latest config
 4) Build and update the firmware

## Config Changes
### Configuration.h
 - Update -> CUSTOM_MACHINE_NAME to "Ender-5"
 - Uncomment -> USE_XMAX_PLUG
 - Uncomment -> USE_YMAX_PLUG
 - Update -> DEFAULT_AXIS_STEPS_PER_UNIT to { 80, 80, 800, 93 }
 - Update -> DEFAULT_MAX_FEEDRATE to { 500, 500, 5, 25 }
 - Update -> DEFAULT_MAX_ACCELERATION to { 500, 500, 100, 10000 }
 - Uncomment -> USE_PROBE_FOR_Z_HOMING
 - Uncomment -> BLTOUCH
 - Update -> NOZZLE_TO_PROBE_OFFSET to { -47, -4, -3.5 }
 - Update -> X_HOME_DIR to 1
 - Update -> Y_HOME_DIR to 1
 - Update -> X_BED_SIZE to 220
 - Update -> Y_BED_SIZE to 205
 - Update -> Z_MAX_POS to 300
 - Uncomment -> AUTO_BED_LEVELING_BILINEAR
 - Comment Out -> MESH_BED_LEVELING
 - Uncomment -> RESTORE_LEVELING_AFTER_G28
 - Comment Out -> ENABLE_LEVELING_AFTER_G28
 - Update -> GRID_MAX_POINTS_X to 3
 - Uncomment -> Z_SAFE_HOMING
 - Update -> HOMING_FEEDRATE_MM_M to { (50*60), (50*60), (4*60) }
 - Update -> PREHEAT_1_TEMP_HOTEND to 200
 - Update -> PREHEAT_1_TEMP_BED to 60
 - Update -> PREHEAT_2_LABEL to "PETG"
 - Update -> PREHEAT_2_TEMP_HOTEND to 235
 - Update -> PREHEAT_2_TEMP_BED to 80
 - Uncomment -> INDIVIDUAL_AXIS_HOMING_MENU
 - Update -> NEOPIXEL_TYPE to NEO_GRBW
 
### Configuration_adv.h
 - Uncomment -> BLTOUCH_DELAY 500
 - Uncomment -> BLTOUCH_HS_MODE true
 - Uncomment -> PROBE_OFFSET_WIZARD
 - Uncomment -> PROBE_OFFSET_WIZARD_START_Z -4.0
 - Uncomment -> BABYSTEP_ZPROBE_OFFSET
 - Update -> FILAMENT_CHANGE_UNLOAD_LENGTH to 550

## Last Tested Commit
Branch: bugfix-2.1.x (https://github.com/MarlinFirmware/Marlin/tree/bugfix-2.1.x)
Commit: 59e19898ce301af0bc870d61e34372fcda594aa5 (https://github.com/MarlinFirmware/Marlin/commit/59e19898ce301af0bc870d61e34372fcda594aa5)
