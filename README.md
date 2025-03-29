# Printer configuration

## Slicer notes

### START_PRINT and END_PRINT   
The printer is set up with `START_PRINT` and `END_PRINT` macros to handle bed 
mesh leveling etc., so we need to remove the start code and end code from 
machine settings in the slicer.

In Cura, go to Preferences->Printers->Machine Settings, then replace 
"Start G-Code" with

```gcode
START_PRINT BED_TEMP = 60 EXTRUDER_TEMP = 210
```

This is a bit sad, as we hardcoded the temperatures. These will be used when 
purging.


In Prusa slicer, we have better parameter passing
```gcode

START_PRINT BED_TEMP={material_bed_temperature_layer_0} EXTRUDER_TEMP={material_print_temperature_layer_0}
```
