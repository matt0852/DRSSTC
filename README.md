# DRSSTC
My design for a tabletop Dual Resonant Solid State Tesla Coil that plays music.

https://www.youtube.com/watch?v=nWpaaL6Mb5Y

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
- Supply: 325VDC (from rectified 230VAC)
- Primary coil: 3D printed standoffs, 12cm dia, 2cm height, 5.6 turns of AWG14 stranded copper wire, 18% detuned for streamer loading
- Tank capacitor: 1x Cornell Dubilier (CDE) 940C30S68K-F capacitor 0.068uF 3kVDC
- Secondary coil: acrylic tube, 6cm diameter, 18.3cm height, ~1350 turns of AWG36 enamelled copper wire
- Topload: styrofoam torus wrapped with aluminum tape, 4.5cm minor dia, 21.5cm major dia
- Resonant frequency: 242kHz
- Spark length: up to 350mm long sparks

## Schematics
I designed this half bridge with the intention of keeping all the components on one double-sided PCB. The copper traces must be designed to withstand high currents (hundreds of amps) while maintaining a low inductance PCB layout. I decided to drive my IGBTs at 24V with 33V gate-source zeners to clamp any sudden voltage spikes that would destroy the IGBTs. Schematic, PCB layout and gerber files can be found in this repository.

![Screenshot 2021-12-26 232746](https://user-images.githubusercontent.com/77631844/147412915-eb769b25-65c0-4c6e-8dac-e1655a04adde.png)

The driver circuit is a modified version of Steve Ward's Universal Driver 1.3. It relies on feedback from the primary coil to ensure that the entire system is oscillating as close to its resonant frequency as possible. The driver features P/N mosfet pairs for robust gate drive at 24V, and also includes over-current detection for safety. The schematic, PCB layout and gerber files can be found here https://www.stevehv.4hv.org/new_driver.html

![Screenshot 2021-12-26 190458](https://user-images.githubusercontent.com/77631844/147406119-414e0b2b-2fcf-4fe5-a980-b168c493c503.png)

For convenience, I used OneTesla's SD card interrupter which can be bought here https://onetesla.com/products/kits/interrupters-all/sd-card-interrupter-kit.html. The signal from the interrupter will be fed to the driver circuit optically via a simple fiber optic setup.

## Construction
I started by winding the secondary coil based on the specifications above. To make my life easier, I built a motorised jig with spare Lego pieces lying around to wind the secondary coil. Took a good 2 days of careful winding.

![Screenshot 2021-12-26 161111](https://user-images.githubusercontent.com/77631844/147403341-2a75f72a-9dc5-49ab-b43f-539acef5f893.png)

The gate drive transformer (GDT) is used to isolate the drive circuitry from the half bridge (refer to the half bridge schematic). Three equal lengths of stranded copper wire were carefully braided together, then I wound the whole bundle onto a ferrite toroid with 15 equally spaced turns. I chose a 37.50mm N30 ferrite toroid with an initial permeability of 4300 and rated for MHz use (Digikey 495-3869-ND). Iron cores don't work and neither do EMI suppression cores. Scoping the two GDT secondaries with a 1MHz function generator hooked to the primary reveals decent square waves. It is CRUCIAL to have an oscilloscope for debugging purposes!

![Screenshot 2021-12-26 161003](https://user-images.githubusercontent.com/77631844/147403421-e81411cb-434e-4ec1-a477-07cd6583c849.png)

I used Allpcb's service (https://allpcb.com/) to fabricate my PCBs at a low cost. Here is the completed driver circuit with the GDT and feedback transformers hooked up. The feedback transformers rely on feedback from the primary coil. They are made of the same ferrite toroids as the GDT and have a 1:1000 primary:secondary ratio (two cascaded 1:33 transformers).

![Screenshot 2021-12-26 165540](https://user-images.githubusercontent.com/77631844/147403908-294ef39f-fdab-4b35-ba35-01309a868e3f.png)

Here is the half bridge PCB with almost all components in place. Heatsinks were attached to each IGBT for heat dissipation. I was really happy with how it turned out!

![Screenshot 2021-12-26 173756](https://user-images.githubusercontent.com/77631844/147404371-0a68236d-ddc5-4f0a-b5f6-a76aa75915d5.png)

Construction of the rest of the tesla coil was straightforward. I used a suitably large piece of acrylic as a base, and glued the secondary coil in place. The topload was created by carefully pasting aluminum tape onto a styrofoam toroid, and a breakout point made of copper tubing was attached. The primary coil was wound and supported with eight 3D-printed standoffs. I then secured everything in place with more glue and cable ties. I added a mains step-down transformer to provide 24VDC for the driver circuit. You can also see the large tank capacitor (in white) in series with the primary coil and the larger electrolytic capacitor behind. Refer to the specifications and the half bridge schematic (C1 and C5) for more details regarding these components. Finally I added a makeshift Faraday's cage over the driver circuit with a plastic box wrapped with aluminum tape.

![Screenshot 2021-12-26 174341](https://user-images.githubusercontent.com/77631844/147404478-f517c696-4d7b-4f2b-9d1a-aadb5f6030d4.png)

## Testing and more pictures

The driver circuit worked well after fixing some bad mechanical connections. Scoping the GDT output shows clean 24V square waves with minimal distortion. First light was achieved at 30VDC. 

![Screenshot 2021-12-26 175753](https://user-images.githubusercontent.com/77631844/147404788-7031a692-fb9c-47b5-af43-35ce83d6d894.png)

## Credits
Loneocean's DRSSTC 1 https://www.loneoceans.com/labs/drsstc1/

Kaizer's DRSSTC II https://kaizerpowerelectronics.dk/tesla-coils/kaizer-drsstc-ii/

Steve Ward's DRSSTC.5 https://www.stevehv.4hv.org/DRSSTC.5.htm

And special thanks to all the individuals at https://4hv.org/ and https://highvoltageforum.net/ for helping me one way or another
