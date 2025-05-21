# Super Nintendo Game Cartridges

This is a repository listing all of my Super Nintendo Cartridge board variants. These *do not* include variants with special chips, such as SA-1 or the Super Game Boy boards. This repository is for the "standard" mapping types.

Use the following table (or navigate the above folders) for information on each specific baord type. <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/wiki">Please also review the wiki for more information.</a>

Note that the boards listed below are planned for development. No dates for upload are guaranteed.

## SNES Board Variants

| **Board Name**                                                                                                     | **Board Number**   | **Max ROM Size** | **Max RAM Size** | **Mappings Supported**         | **Multicart Support?**            | **Memory Family Used** |
|--------------------------------------------------------------------------------------------------------------------|--------------------|------------------|------------------|--------------------------------|-----------------------------------|------------------------|
| <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/tree/main/Advanced%20Flash">Advanced Flash</a> | SNES-8XJ4D-01A     | 8 MB             | 32 KB            | LoROM, HiROM, ExLoROM, ExHiROM | Yes (2 games; 4MB ROM, 32KB RAM)  | Type A (M29F160)       |
| <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/tree/main/LoROM%20Flash">LoROM Flash</a>       | SNES-8XL8D-01A     | 8 MB             | 128 KB           | LoROM, ExLoROM                 | Yes (2 games; 4MB ROM, 32KB RAM)  | Type A (M29F160)       |
| <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/tree/main/HiROM%20Flash">HiROM Flash</a>       | SNES-8XH8D-01A     | 8 MB             | 128 KB           | HiROM, ExHiROM                 | Yes (2 games; 4MB ROM, 32KB RAM)  | Type A (M29F160)       |
| <a href="https://github.com/MouseBiteLabs/Super-Nintendo-Cartridges/tree/main/Advanced%20UV">Advanced UV</a>       | SNES-8XJ8D-01C     | 8 MB             | 128 KB           | LoROM, HiROM, ExLoROM, ExHiROM | Yes (2 games; 4MB ROM, 32KB RAM)  | Type C (27C322)        |
| <a href="https://mousebitelabs.com/2019/08/12/how-to-make-a-snes-reproduction-cartridge-quick-guide/">Basic UV</a> | SNES-4NJ8D-01C     | 4 MB             | 128 KB           | LoROM, HiROM                   | No                                | Type C (27C160)        |

## Naming Convention

| SNES                                | \- | 8                 | X               | J              | 4            | D                                    | \- | 01       | A                                       |
| ----------------------------------- | -- | ----------------- | --------------- | -------------- | ------------ | ------------------------------------ | -- | -------- | --------------------------------------- |
| Super Nintendo Entertainment System |    | Max ROM Size (MB) | Ex Mode Support | Mapper Type(s) | Max RAM Size | Multicart Support                    |    | Revision | Memory Family                           |
|                                     |    | 1                 | N = No          | L = LoROM      | 0 = None     | S = Single game                      |    |          | A = New EEPROM (M29F160)                |
|                                     |    | 2                 | X = Yes         | H = HiROM      | 1 = 2 KB     | D = Multicart (split max ROM space)  |    |          | B = NOS EEPROM (29F016, 29F032, 29F033) |
|                                     |    | 4                 |                 | J = Both       | 2 = 8 KB     | M = Multicart (double max ROM space) |    |          | C = UV EPROMs (27C160, 27C322, etc)     |
|                                     |    | 6                 | SA =            | SA1            | 4 = 32 KB    |                                      |    |          |                                         |
|                                     |    | 8                 |                 |                | 8 = 128 KB   |                                      |    |          |                                         |

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>. You are able to copy and redistribute the material in any medium or format, as well as remix, transform, or build upon the material for any purpose (even commercial) - but you **must** give appropriate credit, provide a link to the license, and indicate if any changes were made.

©MouseBiteLabs 2024
