# Calibration for the T1 using my Modded printer.cfg

## Bed Level
- Go to your Web interface dashboard.
- Scroll to `Macros`
- Click on `Bed Level 1`
- Wait for it to finish and restart twice.
- Click on `Bed Level 2`
- Wait for it to finish and restart
- Done! with new improved bed level!

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
- Input the new rotation distance value in Klipper unde [extruder] rotation distance.

- That’s it! You’ve successfully calibrated the rotation distance value for your extruder motor

## Dimensional Accuracy

- Download this calibration cube: <a href="https://makerworld.com/en/models/620292">Mnemonic3D</a>

- Slice it and print it. The values ​​of this model are: X=20mm / Y=20mm.

- If you notice a deviation in the measured dimensions, you can apply a correction by following directions below.

- Go to your Web interface then select the `CONSOLE` tab.

- If you notice a deviation in X, enter this command by replacing `**`  by your measured value in X (Note: T is the expected value):

  ```
  M101 X** T20
  ```

- Wait for Klipper to restart.

- If you notice a deviation in Y, enter this command by replacing `**`  by your measured value in Y (Note: T is the expected value):
 
  ```
  M101 Y** T20
  ```

- Wait for Klipper to restart.

- Correction is now applied in your `printer.cfg` file. You can reprint your model to check new accuracy measurements and make extra corrections if desired.