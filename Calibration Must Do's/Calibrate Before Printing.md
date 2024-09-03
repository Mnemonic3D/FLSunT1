# Calibration for the T1

## Extruder Rotation
- This is a MUST do!
- Measure from the top of the bowden to 70mm on the filament and mark it with a marker (Don't use a dark filament)
- Go to your Web interface then select the `CONSOLE` tab.
- type # G91 in the console, hit enter
- 
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
