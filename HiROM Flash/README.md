# Super Nintendo Advanced Flash Cartridge - HiROM (SHVC-8XH8S-01A)

# **THIS REPOSITORY IS UNFINISHED AND THE GERBERS ARE UNTESTED!**

This is a new and improved Super Nintendo cartridge circuit board design that is capable of being flashed via the <a href="https://github.com/sanni/cartreader">Open Source Cart Reader (OSCR) by sanni</a>. Alternatively, you can also flash the ROM chips before soldering them to the board through the use of a programmer like the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a>. This cartridge is made entirely from **brand new off the shelf components.** No donors are required, and you don't need to rely on AliExpress or eBay for parts!

This is the **HiROM-only variant** of the <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges">Advanced Flash cartridge</a>.

![image](https://github.com/user-attachments/assets/cba9c11b-9970-4ec6-a183-312bec8bb5bb)

This cartridge is capable of any standard cartridge with the HiROM or ExHiROM mapping **but not those with co-processors, such as SA-1 or SuperFX.** You can backup games onto it with the following settings:
- Can be programmed to operate as a multicart, changing games by pressing the SNES reset button (this includes the ability to make two games of the same memory map, or one of each)
- Up to 8 MB of ROM space for a single game or 4 MB of ROM space for two games
- Up to 128 KB of RAM space for a single game or two separate banks of 32 KB RAM space for two games
- All these settings can be changed via DIP switch for easy on-the-fly modifications without soldering

All gerbers and source files can be found in this repo, as this project is fully open source. Please read all instructions before attempting the project.

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

(COMING SOON)

<a href="https://mousebitelabs.etsy.com/"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/97127539/239718536-5c9aefe3-0628-4434-b8d8-55ff80ac3bbc.png" alt="PCB from Etsy" /></a> 

You can use the zipped folder at any board fabricator you like. You may also buy the board from PCBWay using this link (disclosure: I receive 10% of the sale value to go towards future PCB orders of my own):

<a href="https://www.pcbway.com/"><img src="https://www.pcbway.com/project/img/images/frompcbway-1220.png" alt="PCB from PCBWay" /></a>

## Required Equipment

- You will need basic tools, like a soldering iron, hot plate, and/or hot air rework station.
- You need a way to program the ROM chip(s).
  - This can be done with the <a href="https://github.com/sanni/cartreader">OSCR</a> to load the game and save data onto the catridge, after the cartridge is assembled.
  - Alternatively, the <a href="https://xgecu.myshopify.com/products/xgecu-new-t48-tl866-3gprogrammer-v12-01-support-28000-ics-for-spi-nor-nand-flash-emmc-bga153-162-169-100-221-tsop-sop-plcc">T48 programmer</a> with the <a href="https://xgecu.myshopify.com/products/100-original-xgecu-adp_f48_ex-1-tsop48-special-adapter-for-nor-flash-only-use-on-t48-tl866-3g-programmer">TSOP48 adapter</a> can program the ROM chip(s). The downside to this is that if you screw up the programming, you'll have to desolder the chips and program them again.
- This cartridge uses the PIC12F629 with the <a href="https://sd2snes.de/blog/cool-stuff/supercic">SuperCIC code</a> to fake out the lockout chip. You will need a way to program these PIC chips. I use the T48 to do so, but you can also use something like the <a href="https://www.microchip.com/en-us/development-tool/pg164130">PICkit 3.</a> Note that if you have region modded your SNES, you won't need the lockout chips in the cartridges.

## How to Program

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Preparing-the-ROM">Please check out the wiki pages on how to prepare the ROM and program the cartridge.</a>

## Board Configurations

You *do not* need every single part on this board to make a game. The game you want to make is mainly dependent on the memory mapping (LoROM, HiROM, etc), the ROM size, and the RAM size. Depending on your needs, you only need to solder on certain components, which you can find below in the BOM section.

- **Every board needs Group A components.** You can make HiROM games that have no RAM and are up to 4 MB large with this configuration. (If your game is only 2 MB, you do not need to include U9 and C9)
- If you need RAM space, **add Group B components.** This will add 32 KB of RAM space. (Multicarts will need the AS6C1008 chip for the RAM)
- If your game is larger than 4 MB, it will use the ExHiROM memory mapping. **Add Group C components for this.**
- For multicarts, you can make a board with two games on it up to 4 MB each. You will need Group C components, **as well as Group D components.** (If one of the two games you want to program is only 2 MB, you do not need to include U9 and C9 for Game 1, and/or U12 and C12 for Game 2.)
- Finally, if you *really* need the extra RAM space for the odd game that uses 128 KB of RAM, solder **Group E components**.

## Switches

For SW1 through SW5, you can either use the DIP switch as indicated in the BOM below (in the "Optional" sections), or you can jumper the pads underneath the switch to turn the switch "ON". In this example, positions 1 and 2 are "ON"; 3 and 4 are "OFF":

![image](https://github.com/user-attachments/assets/ef28e52b-cb4e-4246-bc94-9d3e4eb2fbbe)

### Switch 2 - SRAM Size

This sets the RAM size for the game, assuming you have the RAM chip installed. The maximum addressable space for single cartridges is 128 KB (necessitates SW6 if you need more than 32 KB), and for multicarts it's 32 KB per game. You *will* need the 128 KB chip (AS6C1008) for multicarts (but not SW6). Some games will care that you have the correct RAM size, or else they will activate piracy protection, so you should try to match the settings your game calls for. Note that DIP positions 1/2, and 3/4 should be changed together simultaneously:

- For 2 KB of RAM, set all switches OFF.
- For 8 KB of RAM, set positions 1 and 2 ON, and 3 and 4 OFF.
- For 32 KB of RAM, set all positions ON.

*Note: If you have a v1.1 board, please read the section below, as the instructions are slightly different to set the RAM size correctly.*

### Switch 6 - SRAM Size (for single games with RAM larger than 32 KB)

SW6 is pretty self-explanatory, and only usable for non-multicarts. It's only required if you want to switch between games with more than 32 KB of RAM and ones that don't. The number of games that use RAM larger than 32 KB is pretty small so you probably won't need this part.

### Switch 3 - Ex Mode

Switch this ON for the ExHiROM mapping, or OFF for regular HiROM. (The ExHiROM mode on this board includes both the "true" ExHiROM mapping as well as HiROM games that just have more than 4 MB of ROM space.)

### Switch 4 and 5 - Multicart Configurations

These two sets of switches control the multicart features on the board. Here is how to use the switches to program the two games:

- Put SW4A (MULTICART) to "YES"
- Set SW4B (MULTI MODE) to "PRG" (for programming)
- Program the first game by putting SW5 in "GAME 1" position; program the second by putting SW5 in "GAME 2" position
- After both games are programmed, set SW4B to "PLAY"

Note that if you put SW4A to "NO", you will keep the game in a single-game mode, and the game that boots up will be determined by the position of SW5.

## Fix for v1.0

There's a minor issue with v1.0 of the board. **This does not affect versions after v1.0.** 

For setting the SRAM size using SW2, you must do the following:

- For 2 KB of RAM, set all switches OFF.
- For 8 KB of RAM, set positions 1 and 2 ON, and 3 and 4 OFF. **REMOVE R8 AND R9 FROM THE BOARD.**
- For 32 KB of RAM, set all positions ON. **REMOVE R8, R9, R10, AND R11 FROM THE BOARD.**

SW6 cannot be used on this board, so games are restricted to 32 KB of RAM maximum.

If you *do not* remove the resistors as defined above, your save battery life will be severely impacted. Speaking of which...

## Estimating Battery Life

To accurately estimate the battery life, you must first solder the battery in, and then either program your game in the OSCR or power it on in a Super Nintendo.

After that, measure the voltage across R1 using a multimeter in DC mV mode, touching the probes to the two test point pads on either side of R1. You should read something around 10 mV or less. If you are severely higher than 10 mV, like in the 100's of mV, then you have a problem on your board.

Once you have a suitable voltage, find the milliamp-hour rating of your selected battery (preferrably from a datasheet). For example, a Renata CR2032 battery is rated for 225 mAh.

Now to estimate battery life, take the voltage measurement in mV and the battery rating in mAh, and plug it into this equation: 

Time (years) = Resistance of R1 (ohms) * Battery capacity (mAh) / Voltage (mV) / 8760

The factor of 8760 is for converting years to hours (24 hours in a day, 365 days in a year). The resistance of R1 is 10000 ohms. So for an example, if you measured 10 mV on R1 and are using a Renata CR2032, you would get 10000 * 225 / 10 / 8760 = **25.7 years.**

## Troubleshooting

<a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki/Troubleshooting-Tips">Please check out the wiki pages for troubleshooting tips.</a>

## Bill of Materials (BOM) (UPDATE)

The component groups required for the build you want to make are detailed above. Note that the "optional" groups mostly only contain the switches, as you can manually set the switch position with a 0-ohm resistor (or, lack of a resistor). Remember, shorting the pads means the switch is ON, and keeping the pads depopulated means the switch is OFF.

### Mouser Shopping Cart

The following cart has *the maximum amount* of parts you would potentially need on a single board (essentially, a multicart), plus a few extras of the passive components due to price breaks. This also includes **four M29F160 chips and both the AS6C62256 and AS6C1008.** You can remove the chips you don't need from the shopping cart before ordering, according to the component group assignments below.

https://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=f8afa5ad01

### Group A - 4 MB ROM, No RAM

Note: If your game is only 2 MB, you do not need U9 and C9.

| Reference | Value/Part Number | Package       | Description      | Source                                           |
| --------- | ----------------- | ------------- | ---------------- | ------------------------------------------------ |
| C1        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C2        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C3        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C4        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C7        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C8        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C9        | 0.1u              | 0603          | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| CC        | 22u               | 1206          | Capacitor (MLCC) | [https://mou.sr/4e4zShm](https://mou.sr/4e4zShm) |
| R2        | 100k              | 0603          | Resistor         | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| R3        | 10k               | 0603          | Resistor         | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R4        | 100k              | 0603          | Resistor         | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| R5        | 10k               | 0603          | Resistor         | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| U1        | PIC12F629         | DIP-8, SOIC-8 | Lockout Chip     | [https://mou.sr/3XuEZzO](https://mou.sr/3XuEZzO) |
| U2        | SN74CBT3257CPWR   | TSSOP-16      | Multiplexer      | [https://mou.sr/3MKJwd1](https://mou.sr/3MKJwd1) |
| U3        | SN74CBT3257CPWR   | TSSOP-16      | Multiplexer      | [https://mou.sr/3MKJwd1](https://mou.sr/3MKJwd1) |
| U4        | SN74CBT3257CPWR   | TSSOP-16      | Multiplexer      | [https://mou.sr/3MKJwd1](https://mou.sr/3MKJwd1) |
| U7        | 74LS139           | TSSOP-16      | Decoder          | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |
| U8        | M29F160           | TSOP-48       | Flash EEPROM     | [https://mou.sr/3MNWQ0b](https://mou.sr/3MNWQ0b) |
| U9        | M29F160           | TSOP-48       | Flash EEPROM     | [https://mou.sr/3MNWQ0b](https://mou.sr/3MNWQ0b) |

### Group A (Optional) - Programming header, Lo/Hi switch/jumper

Note: J1 is a space that allows you to program the PIC using the standard ISP pinout while the chip is on-board. It is not a required component. If you wish to use it, you will need to pick out a component yourself to use here, as there are different ways to go about using it.

| Reference | Value/Part Number   | Package                  | Description        | Source                                           |
| --------- | ------------------- | ------------------------ | ------------------ | ------------------------------------------------ |
| J1        | \--                 | 2x3 pins, 2.54mm spacing | Header (see note)  | N/A                                              |
| RS1       | 0 ohm               | 0603                     | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| SW1       | DS04-254-2-01BK-SMT | 1-position DIP           | DIP Switch (1-pos) | [https://mou.sr/3MK4Lvz](https://mou.sr/3MK4Lvz) |

### Group B - adds 32 KB of RAM

Note: If you are making a multicart, you must use the AS6C1008 for U10.

| Reference | Value/Part Number   | Package        | Description        | Source                                           |
| --------- | ------------------- | -------------- | ------------------ | ------------------------------------------------ |
| B1        | CR2032              | CR2032         | Coin Cell Battery  | [https://mou.sr/3QhcXXc](https://mou.sr/3QhcXXc) |
| C5        | 0.1u                | 0603           | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C6        | 0.1u                | 0603           | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C10       | 0.1u                | 0603           | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C11       | 0.1u                | 0603           | Capacitor (MLCC)   | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| CB        | 22u                 | 1206           | Capacitor (MLCC)   | [https://mou.sr/4e4zShm](https://mou.sr/4e4zShm) |
| R1        | 10k                 | 0603           | Resistor           | [https://mou.sr/3riR7IH](https://mou.sr/3riR7IH) |
| R6        | 130k                | 0603           | Resistor           | [https://mou.sr/3MjXliy](https://mou.sr/3MjXliy) |
| R7        | 49.9k               | 0603           | Resistor           | [https://mou.sr/3BBcDgp](https://mou.sr/3BBcDgp) |
| R8        | 100k                | 0603           | Resistor           | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| R9        | 100k                | 0603           | Resistor           | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| R10       | 100k                | 0603           | Resistor           | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| R11       | 100k                | 0603           | Resistor           | [https://mou.sr/49bgMnu](https://mou.sr/49bgMnu) |
| U5        | 74LS139             | TSSOP-16       | Decoder            | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |
| U6        | 74LS139             | TSSOP-16       | Decoder            | [https://mou.sr/4eqzppn](https://mou.sr/4eqzppn) |
| U10       | AS6C62256, AS6C1008 | SOP-28, SOP-32 | SRAM               | [https://mou.sr/3ZxG6jd](https://mou.sr/3ZxG6jd) |
| U11       | TPS3613             | MSOP-10        | Battery Management | [https://mou.sr/45Ir2kh](https://mou.sr/45Ir2kh) |

### Group B (Optional) - RAM size switch/jumpers

| Reference | Value/Part Number   | Package        | Description        | Source                                           |
| --------- | ------------------- | -------------- | ------------------ | ------------------------------------------------ |
| RS2A      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| RS2B      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| RS2C      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| RS2D      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| SW2       | DS04-254-2-04BK-SMT | 4-position DIP | DIP Switch (4-pos) | [https://mou.sr/3MPsI4o](https://mou.sr/3MPsI4o) |

### Group C - Adds 4 MB ROM for ExLoROM and ExHiROM

Note: If your Ex-mode game is 6 MB large, you don't need U13 and C13.

| Reference | Value/Part Number | Package | Description      | Source                                           |
| --------- | ----------------- | ------- | ---------------- | ------------------------------------------------ |
| C12       | 0.1u              | 0603    | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| C13       | 0.1u              | 0603    | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| U12       | M29F160           | TSOP-48 | Flash EEPROM     | [https://mou.sr/3MNWQ0b](https://mou.sr/3MNWQ0b) |
| U13       | M29F160           | TSOP-48 | Flash EEPROM     | [https://mou.sr/3MNWQ0b](https://mou.sr/3MNWQ0b) |

### Group C (Optional) - Ex Mode switch/jumper

| Reference | Value/Part Number   | Package        | Description        | Source                                           |
| --------- | ------------------- | -------------- | ------------------ | ------------------------------------------------ |
| RS3       | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| SW3       | DS04-254-2-01BK-SMT | 1-position DIP | DIP Switch (1-pos) | [https://mou.sr/3MK4Lvz](https://mou.sr/3MK4Lvz) |

### Group D - Enables multicart mode

Note: If your game(s) are 2 MB, you do not need U9 and C9 (for Game 1) and/or U12 and C12 (for Game 2).

| Reference | Value/Part Number | Package   | Description      | Source                                           |
| --------- | ----------------- | --------- | ---------------- | ------------------------------------------------ |
| C14       | 0.1u              | 0603      | Capacitor (MLCC) | [https://mou.sr/3ENc15O](https://mou.sr/3ENc15O) |
| R13       | 1k                | 0603      | Resistor         | [https://mou.sr/3U0EvS4](https://mou.sr/3U0EvS4) |
| U14       | 74HC74            | TSSOP-14  | Flip-Flop        | [https://mou.sr/4eroZpu](https://mou.sr/4eroZpu) |

### Group D (Optional) - Multicart mode switches/jumpers

| Reference | Value/Part Number   | Package        | Description        | Source                                           |
| --------- | ------------------- | -------------- | ------------------ | ------------------------------------------------ |
| RS4A      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| RS4B      | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| RS5       | 0 ohm               | 0603           | Resistor (Jumper)  | [https://mou.sr/4e1ABQg](https://mou.sr/4e1ABQg) |
| SW4       | DS04-254-2-02BK-SMT | 2-position DIP | DIP Switch (2-pos) | [https://mou.sr/3B7BqZr](https://mou.sr/3B7BqZr) |
| SW5       | DS04-254-2-01BK-SMT | 1-position DIP | DIP Switch (1-pos) | [https://mou.sr/3MK4Lvz](https://mou.sr/3MK4Lvz) |

## Revision History (UPDATE)

### v1.2 - Release

- Fixed C9 and C12 positions on PCB
- Added resistors under all switches as alternative
- Changed R8 through R11 to pull-down resistors
- Added Q1 to ensure RAM start-up at correct time
- Simplified multicart circuit to reduce battery current draw, lower the BOM count/cost and simplify the design

### v1.1

- Change reference designators CC1 to CC, CB1 to CB
- Make silkscreen thicker, pin 1 indicators bigger, add boxes around passives
- Round the cart edge for easier insertion, add cart edge pin numbers
- Add pin 1 indicators to switches and U1; move U2-U7 reference designators
- Change Prog/Play to more descriptive language
- Add pads for resistors instead of switches

### v1.0

- Prototype version

## Acknowledgements

- Extremely huge thanks to sanni for firstly creating the OSCR, and secondly for adding programming support for the cartridges.
- Continual thanks to all in the nesdev community for their resources, design tips, and support throughout the past half-decade.

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2024
