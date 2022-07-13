# Stationeers-Airlock

## Overview
This is a MIPS assembly script to mimic the functionality of an Advanced Airlock in the game Stationeers, without the frustratingly long pauses. It is designed for environments that have an external atmosphere, such as Mars.

The script will ensure that the airlock is always fully depressurized before pressurizing, to ensure that the external atmosphere doesn't contaminate the base's atmosphere.

## Parts Required
You need to build an airlock (e.g. a 1x1 grid room) that has the following parts, networked together (and powered of course):

| | Part | Stationeers Component | Sub Type | Purpose |
|---|:---|:---|:---|:---|
| 1 | Integrated Circuit | Integrated Circuit (IC10) | | The chip that controls the airlock |
| 2 | IC Housing | Kit (IC Housing) | | Connects the IC10 chip to the network |
| 3 | Gas Sensor | Kit (Sensors) | Gas Sensor | Reads the pressure in the airlock |
| 4 | Interior Vent | Active Vent | | Transfers breathable atmosphere |
| 5 | Exterior Vent | Active Vent | | Transfers external atmosphere |
| 6 | Outer Airlock Hatch | Airlock | | Leads to outside  |
| 7 | Inner Airlock Hatch | Airlock | | Leads into the base |
| 8 | Airlock cycle button(s) | Kit (Switch) | Button | Trigger the cycling process |

You will need one Button in the airlock itself, but I like to have one inside and outside the base too, just in case.

NOTE:
Since the script reads the state of all connected Buttons, I recommend that the airlock's network be isolated from the rest of the base so as not to be triggered inadvertently by a button that you might have set up for a different purpose.

## How to Build
I recommend renaming all the parts using the Labeller tool for easy recognition.

Once the script has been uploaded to the IC, the device screws on the IC Housing will indicate which device needs to be set for each screw.

The Interior Vent can be piped to the base's interior or a breathable gas tank for more complicated setups. Similarly the Exterior Vent is piped to the exterior or a separate tank.

## Operation
The script mimics the functionality of the in-game Advanced Airlock, but without the annoyingly long pause between depressurization and pressurization. Its speed is limited only by the pressure supplied by the Active Vents.

There are two definitions that can be changed in the script:

- `InteriorPressureTarget`
- `ExteriorPressureTarget`

These are the pressure targets in kPa that the airlock will try to reach when pressurizing each phase. Much like the original Airlock, the script will stall if it is unable to reach the target pressures for any reason. If you're worried about being locked out, you can change the Lock settings in the Initialization section of the script to allow you to manually override the hatches and vents.

The airlock can be made to operate even faster in one of the following ways:

- Setting the `ExteriorPressureTarget` definition to 0 in the script, although this means that you will experience sudden pressure changes when the outer hatch is opened.
- Connecting pressurization tanks instead of simply pulling in base or external atmosphere directly.

## Disclaimer
This program works great for me, but you use it at your own risk. If you do use it, you agree that I'm not responsible if a misconfiguration launches your airlock into orbit, or creates a smoking crater where your base used to be, or some other calamity. If you're playing Stationeers that's just a normal day anyway.
