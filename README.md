# Printer configuration

## Slicer notes

### START_PRINT and END_PRINT   
The printer is set up with `START_PRINT` and `END_PRINT` macros to handle bed 
mesh leveling etc., so we need to remove the start code and end code from 
machine settings in the slicer.

In Cura, go to Preferences->Printers->Machine Settings, then replace 
"Start G-Code" with

```gcode
START_PRINT BED_TEMP={material_bed_temperature_layer_0} EXTRUDER_TEMP={material_print_temperature_layer_0}
```

Also replace "End G-Code" with

```gcode
END_PRINT
```

## No prints in a while?

### Mechanical

- Check for loose screws.
- Check play in print head (V-slot wheels). Tighten eccentric nuts if necessary. Move head through full range to check that it's smooth.
- Check play in belts, tighten if necessary.
- Clean extruder gears.
- Blow off dust with canned air.
- Clean with isopropyl alcohol.
- After print, feel temperature at bowden tube connection. Should not be too hot to touch (if so, fan needs cleaning or replacing).

### Calibration

Run `SCREWS_TILT_CALCULATE` to level the bed. This will tell you how much to turn each bed screw to get the printer level. Numbers are given in hours and minutes (60 minutes is one full rotation). Do `PROBE_CALIBRATE` afterwards.


Run `PROBE_CALIBRATE` to calibrate the z-distance between probe and nozzle. Use a piece of paper to gauge the distance between nozzle and bed. This needs to be done every time you swap hotend. Don't forget `SAVE_CONFIG` afterwards.

Go to 'HEIGHTMAP' and click 'Calibrate', or run `BED_MESH_CALIBRATE` from console and then `SAVE_CONFIG` to rerun bed mesh calibration. This needs to be done every now and then.

## Yearly

  - Check end of bowden tube. Cut if burnt
  - Replace nozzle
  - Check V-slot wheels for wear, especially flatspots
  - Tighten all belts

# Resources

  - [BLTouch Complete setup, by PrintsLeo3D](https://youtu.be/5vmjBXvY6BA?si=0OyLlEUCHdVYDECg)
