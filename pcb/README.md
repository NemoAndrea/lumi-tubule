### LumiTubule PCB

The LumiTubule PCB is generated with KiCad 6.0

The following plugins were used:

* [Teardrops plugin](https://github.com/NilujePerchut/kicad_scripts/tree/master/teardrops) (manual install - in PCBnew go to `tools` > `external plugins` > `open plugin directory`) 
* [Rounded tracks plugin](https://github.com/mitxela/kicad-round-tracks) (via plugin manager)

### Graphics

The graphics for the board are primarily created in Affinity Designer, with the help of [Inkscape](https://inkscape.org/) for some of the outline traces and image binarisation.



Some weird quirks during drawing process

- KiCad seems really picky about when it will render the hole in the board. The outline of the board has a lot of polygons. I am not sure what property of the inner circle makes it work better, but be aware that some frustrations may occur here if you try to change it.