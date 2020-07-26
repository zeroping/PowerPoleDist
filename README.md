# PowerPoleDist

An Anderson PowerPole DC power distribution box.

## What is this thing?

Amateur radio hobbyists (among others) have lots of electronic gear running off of 12 VDC, and to keep the wiring a little cleaner, many of them use PowerPole connectors from Anderson Power Products. These handy little connectors can handle up to 45 amps, and have become a defacto standard.

One of the common accessories is a power breakout, basically a “power strip” for these 12 V connections. These are available from several vendors for under $100, but I wanted some slightly different features (namely, right-angle connectors), so I designed my own.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/finished.jpg" alt="The finished design" width="100%"/>

It can handle at least 30 amps, but past that, you might want to order the PCB with 2 oz/inch copper, or solder copper wires to the PCB to lower the trace resistance.

This design is as open as I can easily make it, so if you want to change something, add something, etc, you can. The one catch is that I don't have the full 3D models for the case published (license issues), but I do have the resulting 2D shapes, so you can order your own case or make simple modifications.

## What does it take to build one?

This design consists of:
- A custom circuit board that you can (design files provided)
- Electronic components that you can order from most suppliers (I used Digikey)
- A few harder-to-get components (the power connectors) available from more specialized shop (I used [Powerwerx](https://powerwerx.com/anderson-power-powerpole-sb-connectors))
- An aluminum case that you can order from a place like SendCutSend (design files provided)
- Some spacers and bolts and such that you can order from a mechanical parts supplier (I used McMaster-Carr)
 
It takes some through-hole soldering and some assembly, but the largest issue with the design is the shipping costs and one-time costs for the custom parts. The parts cost is around $30 per system, but you would spend more than 3x that if you ordered just one of these, since you’re buying parts from five different vendors.

As a result, I think this design is most useful for someone building several for all their amateur radio friends, or someone who is looking for a design to modify or extend.

## Ordering Components

###  PCB files

The PCB production files are in the PCB/gerbers directory. You should be able to use the zip file as-is for most PCB manufacturers. I recommend the wonderful [PCB Shopper](https://pcbshopper.com/) to price-compare for a 2-layer, 40 x 130mm board. You might want to [check for any github issues](https://github.com/zeroping/PowerPoleDist/issues) before you order.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/PCB_Layout_v1_1.png" alt="PCB layout" width="69%"/>
<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/PCB_Schematic_v1_1.png" alt="schematic" width="30%"/>

The original PCB design files are in the [PCB directory](https://github.com/zeroping/PowerPoleDist/tree/master/PCB). It's designed in the open-source PCB design package [KiCad](https://kicad-pcb.org/).

### Components

A reasonable list of the parts and costs [is available here](https://github.com/zeroping/PowerPoleDist/raw/master/Docs/PowerPole_Distribution_Board_Costs.ods).

You can order all of these parts [from Digi-Key using this cart link] (https://www.digikey.com/short/zb19f1), but you may want to order the [Anderson PowerPole parts from Powerwerx](https://powerwerx.com/anderson-power-powerpole-sb-connectors) to get better prices. The links are also in [the parts list spreadsheet](https://github.com/zeroping/PowerPoleDist/raw/master/Docs/PowerPole_Distribution_Board_Costs.ods).

You'll also want to add some [Mini/APM/ATM fuses](https://www.digikey.com/product-detail/en/eaton-bussmann-electrical-division/BK-ATM-30/283-2332-ND/264848) of whatever rating you want.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/parts.jpg" alt="The finished design" width="100%"/>

### Case

The case can be ordered by uploading the files in the [Mechanical directory](https://github.com/zeroping/PowerPoleDist/tree/master/Mechanical) to a place like [SendCutSend](https://sendcutsend.com/), in one of their 0.063” / 1.6 mm materials. I used their [5052 Aluminum](https://sendcutsend.com/aluminum/), and these are tight-fit parts, so you might want to adjust the files a tad for other materials. Be aware that they currently have a $29 minimum per material, so either order more than one, or see what else you want to get cut from metal.

There are also some M3 screws, spacers, and nuts that hold the whole thing together. I ordered these from [McMaster-Carr](https://www.mcmaster.com/), but they all come in packs of 100 – you wanted to build 25 of these, right? The links are available in [the parts list spreadsheet](https://github.com/zeroping/PowerPoleDist/raw/master/Docs/PowerPole_Distribution_Board_Costs.ods).

## Assembly

Start by putting the right-angle contacts into the Anderson PowerPole housings, and slotting the red and black housings side by side. Be sure to check which side the red goes on!

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/powerpoles.jpg" alt="Powerpoles assembled" width="100%"/>

Next, solder the high-current components into the board: the PowerPole contacts, and the fuse holders. These will all take a bit of heat from your soldering iron due to the large traces, and will take lots of solder. I haven’t managed to use too much solder yet. The fuse holders particularly don’t like to wick solder to their surfaces without enough solder on them.

I recommend using some clever supporting on a heat-resistant surface to get all of these parts held in place while you solder them. You especially want to make sure the PowerPole contacts aren’t in crooked.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/fuseholders.jpg" alt="Fues holder top placement" width="100%"/>

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/highcurrentsolder.jpg" alt="high current solder junctions" width="100%"/>

Then, solder all of the smaller through-hole components. This should be relatively straight forward.

The LEDs can be soldered directly on the board, or you can raise them up to get them to poke through the top of the case. If you raise them up, I recommend measuring and cutting 10 little scraps of wire insulation, and using that wire insulation to get the LEDs at the right height.

Decide if you want the LEDs to be on all the time, or just when you press the fuse check button. If you want them on all the time, short JP1 with some solder. Be aware, the current-limiting resistors for the LEDs were chosen to be pretty bright, so you might choose larger resistances for R1-R10 if you want them on all the time.

Also decide if you want the case connected to GND. If you do, then short jumper JP101 with some solder. I don’t recommend it, as the fuses will probably short 12V to the case if you decided to unplug one of them while the system is powered.

Next, start assembling the case. Start by threading the ‘front’ panel down between the PowerPole housings. This panel is just barely not reversible – the PowerPole housings are slight off-center and closer to the end of the board with the tactile switch. Add that to the list of fixes for the next version!

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/allcomponentssolder.jpg" alt="all of the components soldered down" width="100%"/>

Once you have the front panel in place, you can put the top on, threading the LEDs in place as as you go. You can start to fit the front panel into the top by tapping it gently with a hammer. This aluminum will bend if you’re not careful, but it makes for a satisfyingly tight fit when it goes together.

This is now your last chance to check everything over and put the spacers in before you finish assembling the case. The taller spacer go on the top of the board, and the shorter ones go below, so put those in place, and thread the long M3 screws through the case top, the spacers, and PCB. From this point on, you will want to leave the M3 screws in place to keep the spacers lined up. You might want to  put the nuts on for now to hold them in place.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/stackup.jpg" alt="M3 screw stackup" width="100%"/>
<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/casetwosides.jpg" alt="case assembly" width="100%"/>

Now, add the case back and sides. Again, you might want to use a hammer to tap them in. Use a board edge or something to let you put the top against a firm surface, since there are now M3 screw heads sticking out of the top.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/casefivesides.jpg" alt="case assembly" width="100%"/>

At this point, you can take the M3 nuts back off and add the case bottom. You might want to again thread the M3 nuts on to hold the screws in place while you tap the aluminum together.

<img src="https://github.com/zeroping/PowerPoleDist/raw/master/Docs/images/casesixsides.jpg" alt="case assembly" width="100%"/>

Once you get the case all slotted together, you can try adding rubber feet. The ones I found don’t fit perfectly, but they squish just enough to let these nuts thread on to the M3 screw. I have found that squishing the feet (with nuts in place) just a little bit helps me get it started, and after that, the nuts seem to lock in place enough to let you tighten them. I’d like to have better feet, but these are the best ones I’ve found that are cheap.

## Issues

Github has a way to handle [reporting issues](https://github.com/zeroping/PowerPoleDist/issues), so submit any problems there, and look there for issues that other people have hit. The nice thing about handling it here is that, even if I'm not attentive, at least the issues will all be public.

## Reuse of this design

I want this design to be open for anyone to use for hobbiest use. If you’re selling them for a profit, give me some attribution and link to this git repo. If you’re selling more than 100 for a profit, let me know - I will probably still be ok with it.

I’ll work on picking a proper license at some point, but for now, just be reasonable.
