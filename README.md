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

Run `BED_MESH_CALIBRATE` and then `SAVE_CONFIG` to rerun bed mesh calibration.
