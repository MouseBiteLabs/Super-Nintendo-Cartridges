# Super Nintendo Basic UV Cartridge (SNES-4NJ8D-01C) 
# UNDER CONSTRUCTION!! Most information is inaccurate.

# Order at your own risk -- v1.0 is untested

This is an updated design of my old <a href="https://mousebitelabs.com/2019/08/12/how-to-make-a-snes-reproduction-cartridge-quick-guide/">SNES Basic cartridge boards</a>, which can use the original mask ROM chips from SNES carts, or the older 27C160 UV EPROM chips. Functionally, this design is the same as the older one, but under the hood I have ported the project over from Eagle to KiCad, and heavily cleaned up the schematic and some of the trace routings. I also added support for the MAD-1 chip from a donor board. This version is also fully open source.

![image](https://github.com/user-attachments/assets/2b6deb7c-9e4e-4d77-85bd-fbfdab6b56cd)

![image](https://github.com/user-attachments/assets/ec4ccdeb-2f1e-4232-8ff9-c5fff1db542f)

This cartridge covers a large portion of the SNES library, capable of any standard cartridge **but not those with co-processors, such as SA-1 or SuperFX.** You can backup games onto it with the following settings:
- HiROM and LoROM memory maps
- Up to 4 MB of ROM space
- Up to 128 KB of RAM space

All gerbers and source files can be found in this repo, as again, this project is fully open source. Please read all instructions before attempting the project.

## Important Things Before You Start

1) <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki">Please review the wiki for more information about using the circuit boards, instructions for how to program them, and example builds.</a>
2) When soldering parts on, it's a good idea to put kapton tape or otherwise cover the bottom cartridge edge. You do not want to get solder on the cartridge contacts.
3) I am not responsible for any damage you do to your self or your property. Attempt this project at your own risk.
4) I do not guarantee design compatibility. You may encounter issues with certain games. There is also a chance I have made an error in the design or the BOM - if this is the case, I will do everything I can to address the problem as quickly as possible.
5) If you are using this board to make games other than for personal use, you must have permission from the originator to use and distribute any ROM images or other related material. You are responsible for making sure you adhere to any license requirements.

DO NOT use my circuit boards for profiting from stolen work - this especially includes homebrew content, ROM hacks, and using fan-made labels without permission from the originator. **Support ALL original creators!**

## Board Characteristics and Order Information

The zipped folder contains all the gerber files for this board. The following options **must** be chosen when ordering boards for yourself.

- Thickness: 1.2mm
- Surface Finish: ENIG
- Gold Fingers: Yes, 30° chamfer

**I sell this blank circuit board on Etsy, so you don't have to buy a bunch of multiples if you don't want to.** (Click the banner!)

<a href="https://mousebitelabs.etsy.com/"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- You need a way to program the ROM chip(s). There are two ways I have programmed them in the past:
  - Using the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with my <a href="https://github.com/MouseBiteLabs/27C322-TL866-Adapter">27C322 to TL866 Programming Adatper</a> board. The programming adapter is compatible with the T48, and it allows you to program the 42-pin EPROMs (27C160 and 27C322) with the 40-pin T48 programmer.
  OR
  - Using the <a href="https://www.mcumall.com/store/index.php?route=product/product&path=66&product_id=85">GQ4x4 programmer</a> with the ZIF adapter board that comes with it.
- This cartridge uses the PIC12F629 with the <a href="https://sd2snes.de/blog/cool-stuff/supercic">SuperCIC code</a> to fake out the lockout chip. You will need a way to program these PIC chips. I use the T48 to do so, but you can also use something like the <a href="https://www.microchip.com/en-us/development-tool/pg164130">PICkit 3.</a> Note that if you have region modded your SNES, you won't need the lockout chips in the cartridges.

## How to Program

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

This board is highly customizable. You *do not* need every single part on this board to make a game. The game you want to make is mainly dependent on the memory mapping (LoROM, HiROM, etc), the ROM size, and the RAM size. Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section. You will also need to configure the game with the various solder jumpers on the back of the board.

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Advanced-UV">**I highly recommend checking out the various examples of board configurations on the wiki.**</a>

### Components Required

I've split up the requisite parts into a few different "Groups" which you can find a comprehensive list for in the BOM section a few sections down from this one.

- **Every board needs Group A components.** You can make LoRom or HiROM games that have no RAM and are up to 4 MB large with this configuration.
- If you need RAM space, **add Group B components.** This will add up to 128 KB of RAM space.
- If your game is larger than 4 MB, it will use the ExLoROM or ExHiROM memory mapping. **Add Group C components for this.**
- For multicarts, you can make a board with two games on it up to 4 MB each. You will need Group C components, **as well as Group D components.**

#### Socket Configurations

If your game is the LoROM or ExLoROM mapping type, solder U3 (and U4 if necessary) in the bottom set of sockets (labeled "LO" on the left side). If your game is of the HiROM or ExHiROM mapping type, solder U3 (and U4 if necessary) in the top set of sockets (labeled "HI" on the left side). Furthermore, if you are making a LoROM or ExLoROM game that has SRAM, then populate the U8L socket. If you are making a HiROM or ExHiROM game that has SRAM, then populate the U8H socket. Note that you can populate both U8L and U8H without issue, if you want.

If you are making a multicart, both games must be of the *same* mapping type. You cannot make one HiROM and one LoROM game in a multicart.

Keep in mind that the 27C160 can hold up to 2 MB of ROM data, and the 27C322 can hold up to 4 MB. You can use either of those chips in ROM slots 1 and 2, but if you are going to make an ExLoROM or ExHiROM game, ROM1 needs to be a 27C322. ROM2 in this case *can* be a 27C160, but only if the ROM is 6 MB total in size.

### Solder Jumpers

There are two types of solder jumper pads on the board - the 2-segment and 3-segment. For the 2-segment pads, if they need to be connected, simply bridge the two with solder. For the 3-segment pads, use a solder bridge on the middle pad to either side depending on the option you need.

#### U8 Bypass

This is the only set of pads on the front of the board. If your game does not use SRAM, then you must solder these pads together. **Do not solder these pads if your game uses SRAM.**

#### U3/U4 Configuration

On the reverse side of U3 and U4 are three sets of pads used to set what kind of EPROM you are using, and in the case of the 27C322, what mapping type you are using.

![image](https://github.com/user-attachments/assets/54c27dd1-dc9c-45ff-80d2-0bd233a7c004)

Keep in mind that if you are using both ROM1 and ROM2, both EPROMs *must* be in the same mapping type sockets - either both LoROM or both HiROM. You cannot mix the two mapping types between EPROMs. You can however use one 27C322 in ROM1 and a 27C160 in ROM2 for EX-mode games, or 27C160 in ROM1 as well if making a multicart.

#### LoROM/HiROM

These are all 3-segment pads. They only need to be configured on the back if you are making a game that contains SRAM.

#### Single/Multi

The pads on the bottom right of the back of the board are mandatory for every game. Solder the middle pad to the top for single game configuration, or to the bottom for multicart configuration. The pads on the top middle of the back of the board only need to be configured if your cartridge uses SRAM.

#### SRAM Size

The set of pads at the top left underneath the SRAM chip configure the size of the SRAM that the SNES will see. All pads must be configured if you are using SRAM, and each set of 2 should be soldered in the same direction. The example picture below shows a game configured for 256 Kbit of SRAM. **It is important to note these numbers represent the SRAM in BITS, not BYTES. To figure out the BYTES of SRAM, take the numbers here and divide by 8.**

![image](https://github.com/user-attachments/assets/51d948bd-0b3d-4d43-90a9-a83ab34eb02d)

Note: If you want to set the RAM size to zero, but still have a RAM chip installed, then simply unsolder the right-most HIROM/LOROM solder pads on the backside of the board.

![image](https://github.com/user-attachments/assets/a1aeb08d-7458-4dc5-a13e-d5602d0cf16b)

### Multicart Configuration

If you are setting you cartridge up for a multicart, you must bend out pin 2 (AS6C1008) or pin 1 (AS6C62256) on the SRAM chip and solder it to the outside hole.

![image](https://github.com/user-attachments/assets/15bea794-99e1-43f8-b5bb-4e3f0d860b4b)

## Estimating Battery Life

To accurately estimate the battery life, measure the voltage across R1 using a multimeter in DC mV mode, touching the probes to the two test point pads on either side of R1. You should read something around 1 mV or less. If you are severely higher than 10 mV, like in the 100's of mV, then you have a problem on your board.

Once you have a suitable voltage, find the milliamp-hour rating of your selected battery (preferrably from a datasheet). For example, a Renata CR2032 battery is rated for 225 mAh.

Now to estimate battery life, take the voltage measurement in mV and the battery rating in mAh, and plug it into this equation: 

Time (years) = Resistance of R1 (ohms) * Battery capacity (mAh) / Voltage (mV) / 8760

The factor of 8760 is for converting years to hours (24 hours in a day, 365 days in a year). The resistance of R1 is 1000 ohms. So for an example, if you measured 1 mV on R1 and are using a Renata CR2032, you would get 1000 * 225 / 1 / 8760 = **25.7 years.**

## Troubleshooting

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Troubleshooting-Tips">Please check out the wiki pages for troubleshooting tips.</a>

## Bill of Materials (BOM)

The component groups required for the build you want to make are detailed above.

### Mouser Shopping Cart

The following cart has *the maximum amount* of parts you would potentially need on a single board (essentially, a multicart), plus a few extras of the passive components due to price breaks. Importantly, though, this does not include the UV EPROM chips (27C160 and 27C322) because those are only available as old stock from places like AliExpress and/or eBay.

https://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=686eaad9eb

### Group A - 4 MB ROM, No RAM

| Reference | Value/Part Number | Package              | Description                     | Source                                           |
| --------- | ----------------- | -------------------- | ------------------------------- | ------------------------------------------------ |
| C1        | 22u               | Radial 2.5mm spacing | Aluminum Electrolytic Capacitor | [https://mou.sr/4lzfiK1](https://mou.sr/4lzfiK1) |
| C2        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| C3        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| C6        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| C7        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| C9        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| U2A       | PIC12F629         | DIP-8                | PIC Microcontroller             | [https://mou.sr/3XuEZzO](https://mou.sr/3XuEZzO) |
| U2B       | PIC12F629         | SOIC-8               | PIC Microcontroller             | [https://mou.sr/4dSUh90](https://mou.sr/4dSUh90) |
| U3        | 27C322, 27C160    | DIP-42               | UV EPROM                        | AliExpress, eBay                                 |
| U6        | 74HCT257          | DIP-16               | Multiplexer                     | [https://mou.sr/3EvChVI](https://mou.sr/3EvChVI) |
| U7        | 74HCT257          | DIP-16               | Multiplexer                     | [https://mou.sr/3EvChVI](https://mou.sr/3EvChVI) |
| U9        | 74HCT139          | DIP-16               | Decoder                         | [https://mou.sr/441VXuJ](https://mou.sr/441VXuJ) |

### Group B - adds 32 KB of RAM

| Reference | Value/Part Number | Package              | Description                     | Source                                           |
| --------- | ----------------- | -------------------- | ------------------------------- | ------------------------------------------------ |
| B1        | CR2025            | CR2032               | Coin Cell Battery               | [https://mou.sr/3QhcXXc](https://mou.sr/3QhcXXc) |
| CB        | 22u               | Radial 2.5mm spacing | Aluminum Electrolytic Capacitor | [https://mou.sr/4lzfiK1](https://mou.sr/4lzfiK1) |
| C5        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| C8        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor               | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| D1        | BAT85             | DO-35-2              | Schottky Diode                  | [https://mou.sr/49GVT4m](https://mou.sr/49GVT4m) |
| D2        | BAT85             | DO-35-2              | Schottky Diode                  | [https://mou.sr/49GVT4m](https://mou.sr/49GVT4m) |
| D3        | BAT85             | DO-35-2              | Schottky Diode                  | [https://mou.sr/49GVT4m](https://mou.sr/49GVT4m) |
| Q1        | 2N3904            | TO-92-3 / SOT-23-3   | NPN BJT                         | THT: [https://mou.sr/3HlkU91](https://mou.sr/3HlkU91), SMT: [https://mou.sr/3C8piaZ](https://mou.sr/3C8piaZ) |
| R1        | 1k                | Axial                | Resistor                        | [https://mou.sr/4hYkrZr](https://mou.sr/4hYkrZr) |
| R2        | 100k              | Axial                | Resistor                        | [https://mou.sr/3Ib4SgO](https://mou.sr/3Ib4SgO) |
| R3        | 10k               | Axial                | Resistor                        | [https://mou.sr/42AN0WU](https://mou.sr/42AN0WU) |
| R4        | 10k               | Axial                | Resistor                        | [https://mou.sr/42AN0WU](https://mou.sr/42AN0WU) |
| R5        | 10k               | Axial                | Resistor                        | [https://mou.sr/42AN0WU](https://mou.sr/42AN0WU) |
| U5        | AS6C62256         | DIP-28               | SRAM                            | [https://mou.sr/3HlZ0mh](https://mou.sr/3HlZ0mh) |
| U8        | 74HCT139          | DIP-16               | Decoder                         | [https://mou.sr/441VXuJ](https://mou.sr/441VXuJ) |

### Group B (Optional) - adds 128 KB of RAM (instead of 32 KB)

Replace U5 in Group B above with the part detailed here, and add the other three components. **I personally recommend sticking to the AS6C62256 SRAM chip unless you absolutely need more RAM space.**

| Reference | Value/Part Number | Package | Description | Source                                           |
| --------- | ----------------- | ------- | ----------- | ------------------------------------------------ |
| Q2        | 2N3904            | TO-92-3 | NPN BJT     | [https://mou.sr/3HlkU91](https://mou.sr/3HlkU91) |
| R6        | 100k              | Axial   | Resistor    | [https://mou.sr/3Ib4SgO](https://mou.sr/3Ib4SgO) |
| R7        | 10k               | Axial   | Resistor    | [https://mou.sr/42AN0WU](https://mou.sr/42AN0WU) |
| U5        | AS6C1008          | DIP-32  | SRAM        | [https://mou.sr/3hNkGxg](https://mou.sr/3hNkGxg) |

### Group C - Adds 4 MB ROM for ExLoROM/ExHiROM or multicarts

| Reference | Value/Part Number | Package              | Description       | Source                                           |
| --------- | ----------------- | -------------------- | ----------------- | ------------------------------------------------ |
| C4        | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| U4        | 27C322, 27C160    | DIP-42               | UV EPROM          | AliExpress, eBay                                 |

### Group D - Enables multicart mode

| Reference | Value/Part Number | Package              | Description       | Source                                           |
| --------- | ----------------- | -------------------- | ----------------- | ------------------------------------------------ |
| C10       | 0.1u              | Radial 2.5mm spacing | Ceramic Capacitor | [https://mou.sr/481ILov](https://mou.sr/481ILov) |
| U10       | 74HCT74           | DIP-14               | Flip-flop         | [https://mou.sr/3YEiVo8](https://mou.sr/3YEiVo8) |

## Revision History

### v1.0 - Re-release

- Release of the KiCad-ported version of my original SNES Advanced cart design
- Removed the "SRAM Enable" pads and made the SRAM always enabled
- HOTFIX: changed QR code, added open source hardware logo

## Acknowledgements

- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade. This design was one of my original ones that was improved through their help and feedback when I was first starting out.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2025
