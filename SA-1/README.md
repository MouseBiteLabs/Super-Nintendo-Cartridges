# Super Nintendo SA-1 Cartridge (SNES-4SA8S-01C)

# Order at your own risk -- v1.0 is untested

This is a SNES cartridge circuit board that houses the proprietary SA-1 processor that was used in a variety of more advanced SNES games. This board should be able to be used as a replacement for all released SA-1 games, as well as many (if not all) SA-1 homebrews or enhanced games. The ROM can be programmed to the popular 27C160 or 27C322 UV EPROM chips, or if you want to use more modern and new components, you can use <a href="https://github.com/MouseBiteLabs/ROM-Adapter-Boards/tree/main/29F160%20to%20UV%20EPROM">my 29F160 to UV EPROM adapter boards</a>. I have also included two options for battery management - a donor MM1026 chip from an original SA-1 cartridge (that has it), or if an MM1026 is not available to use you can use the modern TPS3613 battery management IC.

<img width="2360" height="1308" alt="image" src="https://github.com/user-attachments/assets/c4c97f1e-9861-4b32-8cf9-ef1d52ecd5c1" />

<img width="2360" height="1308" alt="image" src="https://github.com/user-attachments/assets/6679a73b-16fa-4c80-9bdd-f03faa869fb8" />


The board can fit in SNES shells for games that used enhancement chips, as well as standard SNES games (with some minor cutting), and provides:
- Up to 4 MB of ROM space
- Up to 128 KB of RAM space

All gerbers and source files can be found in this repo, as again, this project is fully open source. Please read all instructions before attempting the project.

## Important Things Before You Start

1) <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki">Please review the wiki for more information about using the circuit boards, instructions for how to program them, and example builds.</a>
2) This project requires you remove the SA-1 chip from an original SA-1 SNES cartridge - <a href="https://en.wikipedia.org/wiki/List_of_Super_NES_enhancement_chips#List_of_Super_NES_games_with_enhancement_chips">you can find a list of SA-1 games that you can use as a donor here (make sure you sort by chip type)</a>. This will require a hot air rework station or a hot plate. This will also require extensive soldering capabilities - do not attempt this project if you do not have sufficient soldering experience.
3) When soldering parts on, it's a good idea to put kapton tape or otherwise cover the bottom cartridge edge. You do not want to get solder on the cartridge contacts.
4) I am not responsible for any damage you do to your self or your property. Attempt this project at your own risk.
5) I do not guarantee design compatibility. You may encounter issues with certain games. There is also a chance I have made an error in the design or the BOM - if this is the case, I will do everything I can to address the problem as quickly as possible.
6) If you are using this board to make games other than for personal use, you must have permission from the originator to use and distribute any ROM images or other related material. You are responsible for making sure you adhere to any license requirements.

DO NOT use my circuit boards for profiting from stolen work - this especially includes homebrew content, ROM hacks, and using fan-made labels without permission from the originator. **Support ALL original creators!**

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. The following options **must** be chosen when ordering boards for yourself.

- Thickness: 1.2mm
- Surface Finish: ENIG
- Gold Fingers: Yes, 30° chamfer

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!) (NOT YET AVAILABLE)

<a href="https://mousebitelabs.etsy.com"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like (NOT YET AVAILABLE). You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- This board is **NOT** flashable with any cart flasher (until someone adds that capability) so you need a way to program the ROM chip(s) before soldering them on. There are a few ways I accomplish this:
  - Using the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with my <a href="https://github.com/MouseBiteLabs/27C322-TL866-Adapter">27C322 to TL866 Programming Adatper</a> board. The programming adapter is compatible with the T48, and it allows you to program the 42-pin EPROMs (27C160 and 27C322) with the 40-pin T48 programmer.
  OR
  - Using the <a href="https://www.mcumall.com/store/index.php?route=product/product&path=66&product_id=85">GQ4x4 programmer</a> with the ZIF adapter board that comes with it.
  OR
  - If you are using the 29F160 ROM adapter boards to place into the 27C322 footprint, you can program the 29F160 chips with the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a> can program the ROM chip(s).
- You will need to do some shell cuts to get the board to fit if you're using a standard SNES cartridge shell (detailed later). I recommend using a file set - <a href="https://www.amazon.com/gp/product/B07R3R9461">I bought this one.</a> 

## How to Program

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

On this board, there are two sets of solder jumpers that need to be either bridged or not bridged. Furthermore, there are three two-way solder jumpers that are labeled SJx. Solder from the middle pad to the left or right pads as determined by the game you're making and parts you're using.

### JP1 - Internal RAM (IRAM) Configuration

This pad is bridged **by default**. If you wish to disconnect JP1, you must use a knife to cut the copper trace between the two pads of JP1. The only time this is applicable is for extremely specific SA-1 games that use the SA-1's internal RAM to save, instead of external RAM. There is only **one** instance of this that I was able to find - a Japan-only game called <a href="https://superfamicom.org/info/pachi-slot-monogatari-pal-kougyou-special">Pachi-Slot Monogatari: PAL Kougyou Special.</a> After severing JP1, you will need to connect a wire to the pad directly below JP1 to the battery bus (accessible on the positive pin of CB).

<img width="478" height="305" alt="image" src="https://github.com/user-attachments/assets/b9313ec2-6659-4cbe-846a-3d2c71e37305" />

### JP2 - Battery Bypass Pads

If your game does not require the use of a backup battery because it doesn't save data, then you need to bridge the pads on JP2. You will notice that this is located underneath U4, which is the battery backup chip. Therefore you will not be able to bridge these pads if you are using U4. If you are instead using U5 for the battery management, then be sure **not** to bridge JP2.

### SJ1 - Region Selection

Solder the middle pad (SA-1 pin 127) to GND for NTSC or VCC for PAL. 

### SJ2 - SRAM Chip

If your game uses SRAM, and you are using the 6264 size of SRAM (like the AS6C6264), then solder to the left pad accordingly. If your game uses the 62256 or 1008 size SRAM, then solder to the right pad.

**NOTE:** If you are using a 6264 SRAM chip, you **must** populate R12 and R13 with 10k ohm resistors (see BOM section below).

### SJ3 - UV EPROM Selection

This is pretty self explanatory. Solder according to the UV EPROM part number you are using (or faking with my ROM adapter board).

## Shell Cut Guide

The board shape takes into account both enhancement chip SNES games (like the ones that used the SA-1 chip) as well as the standard SNES shells for regular SNES games. The enhancement chip games add the two extra sets of 8 pins on either side of the cartridge edge, so if you're using a standard SNES shell, you'll need to cut spaces for those pins to stick through. <a href="https://github.com/MouseBiteLabs/Super-Game-Boy-Plus#standard-46-pin-snes-shell-cuts">Here are the example pictures from my Super Game Boy Plus guide on how to do this</a>. Simply mark with a sharpie on the shell where to cut, then use a file or some other tool to make those cuts to allow the extra pins to stick through.

<img width="1020" height="768" alt="370103546-1bbc2b1e-a284-4a2d-8b2a-e84a3a882a5d" src="https://github.com/user-attachments/assets/6f579039-8b66-4807-b176-25117aede685" />

<img width="1029" height="274" alt="370104005-20fd10d5-1b87-485e-89ae-0a075d0c2f13" src="https://github.com/user-attachments/assets/beba59b7-85fa-4b46-b6dc-0c33b5918720" />

## Extra Components

There are a handful of components on the board that never appear in any SA-1 game, and some that show up in a few but not all. A deeper analysis could provide more insight into the functions and rationale behind these added footprints, but that's not something I'm interested in performing myself. Generally, you should be ok to omit these parts. To indicate these, I bordered the components that are *usually* not required with a dashed line instead of solid lines. Those components are:

- R4, which is normally shorted on every cartridge (if you want to add a series resistor here, you must first cut the trace between the pads)
- FB1-FB8, which are ferrite beads for filtering high frequency noise, seen in a handful of cart types but likely not required (like R4, these are shorted by default)
- C15, a 33pF capacitor, which as far as I can tell appears only on <a href="https://snescentral.com/pcbboards.php?chip=SHVC-1L5B-20">SHVC-1L5B-20 boards</a> and on <a href="https://snescentral.com/pcbboards.php?chip=SNSP-1L0N3S-01">SNSP-1L0N3S-01 boards</a> (where it is called C14) - as such, this can likely be omitted from your design
- C13 and C14 *never* appear populated on any SA-1 board from what I can find on SNES Central
- R12 and R13 will be populated *only if* you are using a 6264 SRAM chip, and if you are using anything larger these will remain unpopulated (these parts are stand-ins for some of the unmarked and masked off components near the battery on original boards)

If you run into weird issues with your games, perhaps some of these components could aid in fixing them. Feel free to update me with any information you wish to share in this regard and I will update accordingly.

## Extra Pads (Experimental Use)

I added a few pads to access unused pins if anyone wants to experiment with them.

- RA22 and RA23 go to SA-1 pins 80 and 81, respectively. These are extra ROM address pins. Using RA22 can increase the addressible ROM space to 8 MB, and RA23 can further expand it to 16 MB. This functionality is, as far as I know, theoretical. If someone knows of any homberew games that use this extra space, feel free to let me know.
- /ROMSEL is not used on this cartridge, but along with /WR, perhaps these could be wired up to a breakout board with ROM chips on them for programming through the cart edge using something like the <a href="https://github.com/sanni/cartreader">OSCR</a>. Again, this is theoretical and may not be possible - but the pads are there for whoever wants to experiment.
- The SRAM maxes out at 128KB, however one pin on the SA-1 (pin 104) that is unused has been reported to be an extra SRAM pin, which could theoretically expand the size of the SRAM to a maximum of 256KB. This extra address pin is connected to pin 1 on the SRAM package, which is an NC pin for DIP-32 SRAM chips linked in the BOM section.

## Estimating Battery Life

To accurately estimate the battery life, measure the voltage across R1 using a multimeter in DC mV mode, touching the probes to the two test point pads on either side of R1 (on the back of the board). You should read something around 1 mV or less. If you are severely higher than 10 mV, like in the 100's of mV, then you have a problem on your board. (Did you inappropriately populate R12 and/or R13?)

Once you have a suitable voltage, find the milliamp-hour rating of your selected battery (preferrably from a datasheet). For example, a Renata CR2032 battery is rated for 225 mAh.

Now to estimate battery life, take the voltage measurement in mV and the battery rating in mAh, and plug it into this equation: 

Time (years) = Resistance of R1 (ohms) * Battery capacity (mAh) / Voltage (mV) / 8760

The factor of 8760 is for converting years to hours (24 hours in a day, 365 days in a year). The resistance of R1 is 1000 ohms. So for an example, if you measured 1 mV on R1 and are using a Renata CR2032, you would get 1000 * 225 / 1 / 8760 = **25.7 years.**

## Troubleshooting

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Troubleshooting-Tips">Please check out the wiki pages for troubleshooting tips.</a>

## Bill of Materials (BOM)

- Populate Group A for all carts. It will be the only group of components you need if you have no SRAM on the board.
- Populate Group B to add SRAM and battery back-up, **and then** populate *either* Group C1 or C2 depending on the battery management IC you want to use.
- Populate Group D **only if** you are using 6264 SRAM from Group B - other SRAM types (62256 or 1008) **do not use** Group D components.

### Group A - All Carts

| Reference | Value/Part Number | Package              | Description                     | Source                                           |
| --------- | ----------------- | -------------------- | ------------------------------- | ------------------------------------------------ |
| C1        | 22u               | Radial 2.5mm spacing | Aluminum Electrolytic Capacitor | [https://mou.sr/4lzfiK1](https://mou.sr/4lzfiK1) |
| C2        | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C4        | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C6        | 0.1uF             | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C7        | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C8        | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C9        | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C10       | 0.01uF            | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| C12       | 33pF              | 0603                 | Capacitor (MLCC)                | [https://mou.sr/4cYZLxw](https://mou.sr/4cYZLxw) |
| R2        | 510k              | 0603                 | Resistor                        | [https://mou.sr/3zi8ayj](https://mou.sr/3zi8ayj) |
| R3        | 1k                | 0603                 | Resistor                        | [https://mou.sr/3U0EvS4](https://mou.sr/3U0EvS4) |
| R5        | 1.5k              | 0603                 | Resistor                        | https://mou.sr/4aiZKUE                           |
| R6        | 220               | 0603                 | Resistor                        | [https://mou.sr/3ARwrf3](https://mou.sr/3ARwrf3) |
| U1        | 27C322, 27C160    | DIP-42               | UV EPROM                        | AliExpress, eBay                                 |
| U3        | SA-1              | QFP-128              | Co-processor                    | Donor cartridge                                  |

### Group B - Adds SRAM and Battery Backup

You will also need to add either Group C1 or C2 if you need Group B components.

| Reference | Value/Part Number   | Package              | Description                     | Source                                           |
| --------- | ------------------- | -------------------- | ------------------------------- | ------------------------------------------------ |
| B1        | CR2032              | CR2032               | Coin Cell Battery               | [https://mou.sr/3QhcXXc](https://mou.sr/3QhcXXc) |
| CB        | 22u                 | Radial 2.5mm spacing | Aluminum Electrolytic Capacitor | [https://mou.sr/4lzfiK1](https://mou.sr/4lzfiK1) |
| C5        | 0.01uF              | 0603                 | Capacitor (MLCC)                | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| R1        | 1k                  | 0603                 | Resistor                        | [https://mou.sr/3U0EvS4](https://mou.sr/3U0EvS4) |
| U2        | AS6C6264/62256/1008 | SOP-28/SOP-32        | SRAM                            | https://mou.sr/4qIDtZh                           |

### Group C1 - Adds Battery Management IC (Donor Cart)

Use parts from Group C1 **OR** C2. Do not use both. Group C1 or C2 are required if SRAM is on the board.

| Reference | Value/Part Number | Package | Description        | Source                                           |
| --------- | ----------------- | ------- | ------------------ | ------------------------------------------------ |
| C11       | 0.01uF            | 0603    | Capacitor (MLCC)   | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| U4        | MM1026            | SOIC-8W | Battery Management | Donor cartridge                                  |

### Group C2 - Adds Battery Management IC (New Parts)

Use parts from Group C1 **OR** C2. Do not use both. Group C1 or C2 are required if SRAM is on the board.

| Reference | Value/Part Number | Package | Description        | Source                                           |
| --------- | ----------------- | ------- | ------------------ | ------------------------------------------------ |
| C16       | 0.01uF            | 0603    | Capacitor (MLCC)   | [https://mou.sr/3AsRwK1](https://mou.sr/3AsRwK1) |
| R9        | 130k              | 0603    | Resistor           | [https://mou.sr/3MjXliy](https://mou.sr/3MjXliy) |
| R10       | 49.9k             | 0603    | Resistor           | [https://mou.sr/3BBcDgp](https://mou.sr/3BBcDgp) |
| U5        | TPS3613           | MSOP-10 | Battery Management | [https://mou.sr/45Ir2kh](https://mou.sr/45Ir2kh) |

### Group D - Only If Using 6264 SRAM

ONLY populate these parts if you are using 6264 SRAM.

| Reference | Value/Part Number | Package | Description | Source                                           |
| --------- | ----------------- | ------- | ----------- | ------------------------------------------------ |
| R12       | 10k               | 0603    | Resistor    | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R13       | 10k               | 0603    | Resistor    | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |

## Revision History

### v1.0 - Initial Release

## Acknowledgements

- Special thanks to Bonzo for providing an SA-1 board that I used for board scans and component measurements to develop the majority of this board!
- Huge, endless thanks to the following people for their hard work and resources:
  - <a href="https://problemkaputt.de/fullsnes.htm#snescartsa1games">nocash's SNES resources</a> were the single most helpful resource for this project.
  - <a href="https://github.com/VitorVilela7/SNES-SA-1-doc">VitorVilela's GitHub page</a> helped for filling out information about some of the pins, their connections, and component values.
  - <a href="https://snescentral.com/pcblisting.php">SNES Central's PCB archives</a> provided pictures of all the other major SA-1 game PCBs I did not have myself.
  - <a href="https://snescentral.com/pcblisting.php">This thread detailing Arthrimus/Markfrizb's SA-1 boards</a> helped for cross-referencing component values.
- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade. This design was one of my original ones that was improved through their help and feedback when I was first starting out.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
