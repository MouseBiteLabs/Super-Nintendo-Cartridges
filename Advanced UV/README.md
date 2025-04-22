# Super Nintendo Advanced UV Cartridge (SNES-8XJ8D-01C)

# UNDER CONSTRUSTION

# Order at your own risk -- v1.0 is untested

This is an updated design of my old <a href="https://mousebitelabs.com/2020/07/08/multi-function-snes-reproduction-board-guide/">SNES Advanced cartridge boards</a>, which utilize older UV EPROM chips 27C160 and/or 27C322. Functionally, this design is the same as the older one, but under the hood I have ported the project over from Eagle to KiCad, and heavily cleaned up the schematic and some of the trace routings. This version is also fully open source.

![image](https://github.com/user-attachments/assets/de87eabf-a550-4653-a665-b4e5072f717e)

![image](https://github.com/user-attachments/assets/d9397b29-cf2b-4d8e-aeef-eaf4a468632c)

This cartridge covers over 95% of the entire SNES library, capable of any standard cartridge **but not those with co-processors, such as SA-1 or SuperFX.** You can backup games onto it with the following settings:
- All memory maps supported: LoROM, HiROM, ExLoROM, and ExHiROM
- Can be programmed to operate as a multicart, changing games by pressing the SNES reset button
- Up to 8 MB of ROM space for a single game or 4 MB of ROM space for two games
- Up to 128 KB of RAM space for a single game or two separate banks of 64 KB RAM space for two games

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

<a href="https://mousebitelabs.etsy.com/listing/836162227"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- You need a way to program the ROM chip(s). There are two ways I have programmed them in the past:
  - Using the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with my <a href="https://github.com/MouseBiteLabs/27C322-TL866-Adapter">27C322 to TL866 Programming Adatper</a> board. The programming adapter is compatible with the T48, and it allows you to program the 42-pin EPROMs (27C160 and 27C322) with the 40-pin T48 programmer, or
  - Using the <a href="https://www.mcumall.com/store/index.php?route=product/product&path=66&product_id=85">GQ4x programmer</a>.
- This cartridge uses the PIC12F629 with the <a href="https://sd2snes.de/blog/cool-stuff/supercic">SuperCIC code</a> to fake out the lockout chip. You will need a way to program these PIC chips. I use the T48 to do so, but you can also use something like the <a href="https://www.microchip.com/en-us/development-tool/pg164130">PICkit 3.</a> Note that if you have region modded your SNES, you won't need the lockout chips in the cartridges.

## How to Program

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

You *do not* need every single part on this board to make a game. The game you want to make is mainly dependent on the memory mapping (LoROM, HiROM, etc), the ROM size, and the RAM size. Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section.

Keep in mind that the 27C160 can hold up to 2 MB of ROM data, and the 27C322 can hold up to 4 MB. You can use either of those chips in ROM slots 1 and 2, but if you are going to make an ExLoROM or ExHiROM game, ROM1 needs to be a 27C322. ROM2 in this case *can* be a 27C160, but only if the ROM is 6 MB total in size.

- **Every board needs Group A components.** You can make LoRom or HiROM games that have no RAM and are up to 4 MB large with this configuration.
- If you need RAM space, **add Group B components.** This will add up to 128 KB of RAM space.
- If your game is larger than 4 MB, it will use the ExLoROM or ExHiROM memory mapping. **Add Group C components for this.**
- For multicarts, you can make a board with two games on it up to 4 MB each. You will need Group C components, **as well as Group D components.**

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
