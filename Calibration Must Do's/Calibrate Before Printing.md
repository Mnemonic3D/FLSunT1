# Calibration for the T1

## Extruder Rotation
- This is a MUST do!
- Measure from the top of the bowden to 70mm on the filament and mark it with a marker (Don't use a dark filament)
- Heat your filament to its lowest recommended temp
- 
- Go to your Web interface then select the `CONSOLE` tab.
- Type G91 in the console then hit enter
- Type G1 E70 F60
- Wait!
- The filament will start extruding out of the nozzle. It’ll take some time to complete the extrusion process.
- Measure the remaining filament from the edge of the extruder to our 70mm mark. The value denotes your "Subsequent Mark Distance."
- If your extruder is over-extruding, it would go beyond the 70mm mark so you will need to go into your printer.cfg and edit the rotation distance under [extruder] and raise the number by 0.5 and repeat until it is perfect meaning you don't need to change anything anymore, its dialed in or at least it begins to under extrude.
- If the extruder is under-extruding, Use the following formula to get the "Actual Extruded Distance."
- `actual_extrude_distance = <initial_mark_distance> - <subsequent_mark_distance>`
- 

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
