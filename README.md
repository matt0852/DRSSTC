# DRSSTC
My design for a tabletop Dual Resonant Solid State Tesla Coil that plays music.

![DSCF1054-min](https://user-images.githubusercontent.com/77631844/147196841-2f51533f-dd98-4717-a3a5-8b63a7450f19.JPG)

## Introduction
I wanted to build a small tesla coil. Here were my design considerations.
- Footprint of less than 50cm by 50cm
- Completely solid state (not relying on spark gaps like traditional tesla coils)
- Dual resonant - that is, the primary circuit (tank capacitor and primary coil) is tuned to match the resonant freuency of the secondary circuit (topload and secondary coil)
- Able to produces sparks as tall as itself
- Able to play music with a MIDI interface
- Able to operate on 230VAC

## Specifications
- Bridge: 2x IGW75N65H5XKSA1 IGBTs in a half bridge configuration
- Supply: 230VAC 
- Primary coil: 3D printed standoffs, 12cm dia, 2cm height, 5.6 turns of AWG14 stranded copper wire, 18% detuned for streamer loading
- Tank capacitor: 1x Cornell Dubilier (CDE) 940C30S68K-F capacitor 0.068uF 3kVDC
- Secondary coil: acrylic tube, 6cm diameter, 18.3cm height, ~1350 turns of AWG36 enamelled copper wire
- Topload: styrofoam torus wrapped with aluminum tape, 4.5cm minor dia, 21.5cm major dia
- Resonant frequency: 242kHz
- Spark length: up to 350mm long sparks

## Schematics
I designed this half bridge with the intention of keeping all the components on one double-sided PCB. The copper traces must be designed to withstand high currents (hundreds of amps) while maintaining a low inductance PCB layout. The schematic, PCB layout and gerber files can be found in the source folder. Here is an image for quick reference. I am driving my IGBTs at 24V, with 33V zeners and TVS in series to clamp any sudden voltage spikes.

![combined](https://user-images.githubusercontent.com/77631844/147400215-21d9aaf2-b350-480b-b33e-49f000c4583b.png)

The driver circuit is a modified version of Steve Ward's Universal Driver 1.3. The schematic, PCB layout and gerber files can be found here https://www.stevehv.4hv.org/new_driver.html

For convenience, I used OneTesla's SD card interrupter which can be bought here https://onetesla.com/products/kits/interrupters-all/sd-card-interrupter-kit.html. The signal from the interrupter will be fed to the driver circuit optically via a simple fiber optic setup.

## Construction
I started by winding the secondary coil based on the specifications above. To make my life easier, I built a motorised jig with spare Lego pieces lying around to wind the secondary coil. Took a good 2 days of careful winding.

![Screenshot 2021-12-26 161111](https://user-images.githubusercontent.com/77631844/147403341-2a75f72a-9dc5-49ab-b43f-539acef5f893.png)

The gate drive transformer (GDT) is used to isolate the drive circuitry from the half bridge (refer to the half bridge schematic). Three equal lengths of stranded copper wire were carefully braided together, then I wound the whole bundle onto a ferrite toroid with 15 equally spaced turns. I chose a 37.50mm N30 ferrite toroid with an initial permeability of 4300 and rated for MHz use (Digikey 495-3869-ND). Iron cores don't work and neither do EMI suppression cores. Scoping the two GDT secondaries with a 1MHz function generator hooked to the primary reveals decent square waves.

![Screenshot 2021-12-26 161003](https://user-images.githubusercontent.com/77631844/147403421-e81411cb-434e-4ec1-a477-07cd6583c849.png)

## Credits
Loneocean's DRSSTC 1 https://www.loneoceans.com/labs/drsstc1/

Kaizer's DRSSTC II https://kaizerpowerelectronics.dk/tesla-coils/kaizer-drsstc-ii/

Steve Ward's DRSSTC.5 https://www.stevehv.4hv.org/DRSSTC.5.htm

And special thanks to all the individuals at https://4hv.org/ and https://highvoltageforum.net/ for helping me one way or another
