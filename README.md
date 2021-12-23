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
Technical specifications
- Secondary coil: acrylic tube, 6cm diameter, 18.3cm height, ~1350 turns of AWG36 enamelled copper wire
- Topload: styrofoam torus wrapped with aluminum tape, 4.5cm minor dia, 21.5cm major dia
- Primary coil: 3D printed standoffs, 12cm dia, 2cm height, 5.6 turns of AWG14 stranded copper wire, 18% detuned for streamer loading
- Tank capacitor: CDE 0.068uF

Half bridge
- IGBTs: IGW75N65H5XKSA1

Measurements
- Resonant frequency: 242kHz
- Coupling: 0.186

## Credits
Loneocean's DRSSTC 1 https://www.loneoceans.com/labs/drsstc1/

Kaizer's DRSSTC II https://kaizerpowerelectronics.dk/tesla-coils/kaizer-drsstc-ii/

Steve Ward's DRSSTC.5 https://www.stevehv.4hv.org/DRSSTC.5.htm

And special thanks to all the individuals at https://4hv.org/ and https://highvoltageforum.net/ for helping me one way or another
