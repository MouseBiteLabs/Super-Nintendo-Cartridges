# Super Nintendo Game Cartridges

This is a repository listing all of my Super Nintendo Cartridge board variants. These *do not* include variants with special chips, such as SA-1 or the Super Game Boy boards. This repository is for the "standard" mapping types.

## SNES Board Links

| **Board Name** | **Board Number**   | **Max ROM Size** | **Max RAM Size** | **Mappings Supported**         | **Multicart Support?**            | **Memory Family Used** |
|----------------|--------------------|------------------|------------------|--------------------------------|-----------------------------------|------------------------|
| Advanced Flash | SHVC-8XJ4D-01A     | 8 MB             | 32 KB            | LoROM, HiROM, ExLoROM, ExHiROM | Yes (2 games; 4MB ROM, 32KB RAM)  | Type A (M29F160)       |
| LoROM Flash    | SHVC-8XL8S-01A     | 8 MB             | 128 KB           | LoROM, ExLoROM                 | No                                | Type A (M29F160)       |
| HiROM Flash    | SHVC-8XH8S-01A     | 8 MB             | 128 KB           | HiROM, ExHiROM                 | No                                | Type A (M29F160)       |
| Advanced UV    | SHVC-8XJ8D-01C     | 8 MB             | 128 KB           | LoROM, HiROM, ExLoROM, ExHiROM | Yes (2 games; 4MB ROM, 32KB RAM)  | Type C (27C322)        |
| Basic UV       | SHVC-4NJ8D-01C     | 4 MB             | 128 KB           | LoROM, HiROM                   | No                                | Type C (27C160)        |

## Naming Convention

| SNES                                | \- | 8                 | X               | J              | 4            | D                                    | \- | 01       | A                                       |
| ----------------------------------- | -- | ----------------- | --------------- | -------------- | ------------ | ------------------------------------ | -- | -------- | --------------------------------------- |
| Super Nintendo Entertainment System |    | Max ROM Size (MB) | Ex Mode Support | Mapper Type(s) | Max RAM Size | Multicart Support                    |    | Revision | Memory Family                           |
|                                     |    | 1                 | N = No          | L = LoROM      | 0 = None     | S = Single game                      |    |          | A = New EEPROM (M29F160)                |
|                                     |    | 2                 | X = Yes         | H = HiROM      | 1 = 2 KB     | D = Multicart (split max ROM space)  |    |          | B = NOS EEPROM (29F016, 29F032, 29F033) |
|                                     |    | 4                 |                 | J = Both       | 2 = 8 KB     | M = Multicart (double max ROM space) |    |          | C = UV EPROMs (27C160, 27C322, etc)     |
|                                     |    | 6                 | SA =            | SA1            | 4 = 32 KB    |                                      |    |          |                                         |
|                                     |    | 8                 |                 |                | 8 = 128 KB   |                                      |    |          |                                         |
