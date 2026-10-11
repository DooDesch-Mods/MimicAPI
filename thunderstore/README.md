# MimicAPI

> 🛟 **Need help or found a bug?** Get support at [support.doodesch.de/mimicapi](https://support.doodesch.de/mimicapi).

Shared library for MIMESIS mods. This is the DooDesch maintenance fork of
[NeoMimicry/MimicAPI](https://github.com/NeoMimicry/MimicAPI).

Version 0.4.2 is built against MIMESIS 0.3.2 and MelonLoader 0.7.3.

Requires MelonLoader 0.7.3. Place `MimicAPI.dll` in `MIMESIS/Mods/` and keep only
one copy in the mod setup. The library has no standalone gameplay features.

Original library: NeoMimicry, copyright 2025. Fork maintenance: DooDesch.
Licensed under MIT; the original copyright and permission notice are included
in the package. Source: [DooDesch/MimicAPI](https://github.com/DooDesch/MimicAPI).

## Known API limitations

`GetCurrentRoom` selects the first playable server room. The waiting/maintenance
maximum-player helpers return member counts. Server `StatManager` and
`MovementController` helpers do not resolve through Unity component lookup.
These inherited helpers are outside the two corrected paths in 0.4.2.
