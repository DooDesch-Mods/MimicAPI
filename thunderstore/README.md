# MimicAPI

> 🛟 **Need help or found a bug?** Get support at [support.doodesch.de/mimicapi](https://support.doodesch.de/mimicapi).

Shared library for MIMESIS mods. This is the DooDesch maintenance fork of
[NeoMimicry/MimicAPI](https://github.com/NeoMimicry/MimicAPI).

Version 0.4.3 is built against MIMESIS 0.4.0 and MelonLoader 0.7.3.

Requires MelonLoader 0.7.3. Place `MimicAPI.dll` in `MIMESIS/Mods/` and keep only
one copy in the mod setup. The library has no standalone gameplay features.

Original library: NeoMimicry, copyright 2025. Fork maintenance: DooDesch.
Licensed under MIT; the original copyright and permission notice are included
in the package. Source: [DooDesch/MimicAPI](https://github.com/DooDesch-Mods/MimicAPI).

## Player and server helpers

Player queries use the current scene's registered players and local avatar,
excluding monsters and actors left over from other scenes. `GetCurrentRoom`,
`GetStatManager` and `GetMovementController` resolve the matching server actor.
They return `null` on clients and in the menu. The waiting/maintenance capacity
helpers return the configured limit, while member-count helpers return occupancy.
