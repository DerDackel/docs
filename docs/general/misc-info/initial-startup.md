---
layout: default
title: Initial startup checklist
nav_order: 3
parent: Miscellaneous info # temporarily here to clean up the sidebar links
---


# Initial Startup Checklist

Once you have assembled your VzBot, installed Klipper on your Pi, and successfully flashed your controller board. It is now time to install the printer configuration and perform the initial checks to make sure the assembly went well before starting to print.


## 1. Choose your printer config

Download the provided basic `printer.cfg` file for your printer model to start with:

1. [VzBot 235 Mellow Kit](../../../../assets/printer_configs/vz235_printed/printer.cfg)
2. [VzBot 235 Printed version](../../../../assets/printer_configs/vz235_printed/printer.cfg)
3. [VzBot 330 Mellow Kit](../../../../assets/printer_configs/vz330_mellow/printer.cfg) 
4. VzBot 330 Printed version (TODO)

For all printers, these are common macros to make working with your VzBot easier:

1. [General Quality of Life Macros](../../assets/images/manual/vz235_printed/electronics/Printer_config/Macro.cfg)
2. [Exclude Object for Mainsail and Fluidd](../../assets/images/manual/vz235_printed/electronics/Printer_config/Exclude_Object.cfg)
3. [Print Start and Stop Macros](../../assets/images/manual/vz235_printed/electronics/Printer_config/Start_Stop.cfg)
4. [A Speed Testing Macro](../../assets/images/manual/vz235_printed/electronics/Printer_config/Speed.cfg)

Open your printer's Mainsail frontend in a browser and navigate to the "Machine" tab, then drag and drop all your `.cfg` files into the "Config Files" pane, so it looks like this:

![Machine](../../../../assets/images/manual/vz235_printed/electronics/Printer_config/Machine.PNG)

## 2. Serial Time

TODO

## 3. Check your endstops

To make sure your endstops are actually working, you can trigger them manually and verify that Klipper registers their state. Move the printhead to the center of the bed and move the bed to about half its maximum height to make sure you are not currently hitting any of the endstop switches. Navigate to the machine tab in Mainsail again. You should see a pane named "Endstops".

TODO: Proper screenshot that show a plain machine with endstop pane
![Machine tab](../../../../assets/images/manual/vz330_mellow/electronics/Printer_config/Machine.PNG)

When you press the sync-button ( the cycling arrows icon ), Klipper will query all registered endstops. Initially, X, Y and Z endstops should show up, each with a green bar saying "Open" written on it.

TODO: Probably should get screenshots without a probe
![Endstops in Open state](../../../../assets/images/manual/initial-startup/mainsail_endstops_open.png)

If any of these is currently showing "Triggered", something is wrong with the wiring for that endstop.

In that case, make sure the endstop wires 

* are undamaged,
* are not short-circuiting anywhere,
* have been soldered to the microswitch in the "normally closed" position (the outer pins of the switch),
* are wired to the correct pins on the controller board,
* that said pin is named as endstop pin in the relevant stepper section of your printer.cfg.
* and that the entry in your printer.cfg is not negated (a "!" in front of the pin name)

Now turn to your printer and push the microswitch for the X endstop (located on the left side of the printhead). While holding down the switch, hit the sync button again. Your X endstop should only now show a red bar saying "Triggered". If you stop pushing the microswitch and refresh again, it should turn back to "Open".

TODO: Probably should get screenshots without a probe
![X endstop triggered](../../../../assets/images/manual/initial-startup/mainsail_endstops_x_triggered.png)

If your endstop does not change to "Triggered", check if your endstop wires are connected to the pin referenced in your printer.cfg and that the pin is not negated in the configuration. The most likely reason for this to happen is that the endstop wires have gotten mixed up with some other periphery that closes the circuit. If ANOTHER endstop changed to triggered, you know which one. In the worst case, your endstop switch may be broken and stay closed.

Once you verified your X endstop is working, repeat this process for the other endstops.

## 4. Check your motor movements & XY Homing

TODO

## 5. Adjust your Z endstop & Z Homing

TODO

## 6. Thermistors, heaters and fans

TODO

## 7. PID Tuning

TODO

## 8. Bed Levelling

TODO

## 9. Extruder Calibration

TODO

## 10. Slicer setup

TODO (which slicers)

## 11. Your first print and getting a serial number

TODO
