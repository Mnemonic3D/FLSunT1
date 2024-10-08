# Calibration for the T1 using my Modded printer.cfg
## I ONLY USE ORCA SLICER NOW

# IMPORTANT PRIORITY 
### (Skip if your machine is unable, for some unknown reason there are some people are having issues)
# PID Tuning
- Ensure that the hotend and heatbed are at room temperature (30-50c)
- If the hotend has a silicone sock protection for the heatblock, ensure that it’s installed
- If your printer has a magnetic flex plate, ensure that it’s installed
- Enter  `TURN_OFF_HEATERS` in console

# Calibrating Hot End and Hot Bed PID
## Hot Bed (This will take significantly longer than the Hot End so be patient)
- Set all fans to 100%
- Set Nozzle & Bed Heat Target to `0` and let cool down to its maximum ability (Preferably 40c - 50c)
- Once the temp has lowered as much as you think it can
- Run the `PID_CALIBRATE HEATER=heater_bed TARGET=60` command to start the PID tuning process and wait for it to be completed.
- When done run the  `SAVE_CONFIG` command and the new PID settings will be saved to the printer config file.
## Hot End (Should be done every nozzle change)
- Home the printer and adjust the nozzle position to sit in the middle of the bed, with about 5cm of clearance to the bed.
- Set the heatbed temperature to 60C
- Turn on all fans to 100%
- Run command in the console `PID_CALIBRATE HEATER=extruder TARGET=215` to start the PID tuning process and wait for it to be completed.
- When done run the `SAVE_CONFIG` command and the new PID settings will be saved to the printer config file

# CALIBRATIONS AFTER PID
## Bed Level
- Go to your Web interface dashboard.
- Scroll to `Macros`
- Click on `Bed Level 1`
- Wait for it to finish and restart.
- Click on `Bed Level 2`
- Wait for it to finish and restart
- Done! with new improved bed level, you can compare it to the stock bed level to see!

## Resonances
- Go to your Web interface dashboard.
- Scroll to `Macros`
- Click on `Measuring Resonances`
- Wait for it to finish and restart
- Done! with more accurate resonances!

## Extruder Rotation
### This is a MUST do!
- Measure from the top of the teflon tube to 70mm on the filament and mark it with a marker (Don't use a dark filament)
- Heat your filament to its lowest recommended temp
  
- Go to your Web interface then select the `CONSOLE` tab.
- Type `G91`
- Hit enter
- Type `G1 E70 F60`
- Hit enter
- Wait!
- The filament will start extruding out of the nozzle. It’ll take some time to complete the extrusion process.
- Measure the remaining filament from the edge of the extruder to our 70mm mark. The value denotes your "Subsequent Mark Distance."
- If your extruder is over-extruding, it would go beyond the 70mm mark so you will need to go into your printer.cfg and edit the rotation distance under [extruder] and raise the number by 0.5 and repeat until it is perfect meaning you don't need to change anything anymore, its dialed in or at least it begins to under extrude.
- If the extruder is under-extruding, Use the following formula to get the "Actual Extruded Distance."
- `actual_extrude_distance = <initial_mark_distance> - <subsequent_mark_distance>`
- Use the following formula to calculate the rotation distance for your extruder. You can get the previous rotation distance from the printer.cfg file, under the [extruder] section.
- `rotation_distance = "previous_rotation_distance" * "actual_extrusion distance" / "requested_extrusion distance"`
- Input the new rotation distance value in Klipper under [extruder] rotation distance.

- That’s it! You’ve successfully calibrated the rotation distance value for your extruder motor

## Flow Rate: Default 1 & 1 in print settings and 0.98 in filament settings
### Top & Bottom Flow Rate
#### This flow rate should change only your top and bottom surface flow rate in your print settings, not the flow rate in your filament settings.
- Just use the built-in slicer calibration tool `Pass 1` find most acceptable settings, adjust top bottom flow rate in print settings
- Now after adjustments made do `Pass 2` and find settings and change print setting top and bottom flow rate in print settings
- Done!
- Example: Flow rate of -5 shows the best surface, change your top flow and bottom flow rate to 0.95 while leaving the filament flow rate alone.

## Pressure Advance
#### This needs to be done for every filament type
- You can use the slicer calibration pattern tool 0.015 - 0.045 with steps 0.001.
- Look for any gaps in the corners and find where it stops lets say 0.31 set your PA in filament settings to 0.31
- save and done!
  
## Dimensional Accuracy

- Download this calibration cube: <a href="https://makerworld.com/en/models/620292">Mnemonic3D</a>
- Slice it and print it. The values ​​of this model are: X=20mm / Y=20mm.
- If you notice a deviation in the measured dimensions, you can apply a correction by following directions below.
- Go to your Web interface then select the `CONSOLE` tab.
- If you notice a deviation in X, enter this command by replacing `**`  by your measured value in X (Note: T is the expected value): `M101 X** T20`
- Wait for Klipper to restart.
- If you notice a deviation in Y, enter this command by replacing `**`  by your measured value in Y (Note: T is the expected value): `M101 Y** T20`
- Wait for Klipper to restart.
- Correction is now applied in your `printer.cfg` file. You can reprint your model to check new accuracy measurements and make extra corrections if desired.
