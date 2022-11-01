### LumiTubule PCB

The LumiTubule PCB is generated with KiCad 6.0

The following plugins were used:

* [Teardrops plugin](https://github.com/NilujePerchut/kicad_scripts/tree/master/teardrops) (manual install - in PCBnew go to `tools` > `external plugins` > `open plugin directory`) 
* [Rounded tracks plugin](https://github.com/mitxela/kicad-round-tracks) (via plugin manager)

### Graphics

The graphics for the board are primarily created in Affinity Designer, with the help of [Inkscape](https://inkscape.org/) for some of the outline traces and image binarisation.



Some weird quirks during drawing process

- KiCad seems really picky about when it will render the hole in the board. The outline of the board has a lot of polygons. I am not sure what property of the inner circle makes it work better, but be aware that some frustrations may occur here if you try to change it.

### Considerations

> Note The points below provide some insight into why certain parts were selected. If you spot any errors in the calculations or reasoning, feel free to let me know!

**LED filament current limiting resistor value**

The LED filaments can handle about 100mA current (more in practice seems fine), so let's aim for that value. 

We start with a 5V supply.  These kind of LED filaments [have been reported to drop around 2.56V](https://www.brickstuff.com/store/p198/flexfilament.html), which is consistent with measurements done on a test rig. They seem to all use blue LEDs underneath, so that is a pretty safe maximum drop. The `DMN1045UFR4` MOSFET has a typical R_DSon between 25-32mΩ at 3.3V V_GS according to the datasheet. The voltage drop over the MOSFET will be 0.1A*25mΩ = 2.5mV. We can safely ignore that value. Our resistor value should then be (Vsup - V_LED)/I_LED = (5-2.56) / 0.1 = 24Ω. Let's play it safe and get something slightly higher: 27Ω. 

We then dissipate `P = I^2 * R  = 0.1^2 * 27 = 270mW` in the current limiting resistor. At max power on all 13 filaments this is 13*0.27=3.5W, quite a bit of power. Given that it is a worst-case scenario, it should be acceptable.

