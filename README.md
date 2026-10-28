# MimicAPI

A reflection / helper library for building MelonLoader mods for MIMESIS.

> 🛟 **Need help or found a bug?** Get support at [support.doodesch.de/mimicapi](https://support.doodesch.de/mimicapi).

![MimicAPI in MIMESIS](https://raw.githubusercontent.com/DooDesch-Mods/MimicAPI/main/docs/img/header.jpg)

This is the [DooDesch maintenance fork](https://github.com/DooDesch-Mods/MimicAPI) of
[NeoMimicry/MimicAPI](https://github.com/NeoMimicry/MimicAPI). It keeps the
`MimicAPI.dll` assembly name and public API used by existing mods.

Version 0.4.3 is built against MIMESIS 0.4.0 and MelonLoader 0.7.3.

## Screenshots

Game context only. This project has no standalone gameplay feature.

![Native MIMESIS maintenance scenery used as library context](https://raw.githubusercontent.com/DooDesch-Mods/MimicAPI/main/docs/img/game-context.jpg)

Game context only. MimicAPI is a library and has no standalone visual gameplay feature.

## Installation

Requires MIMESIS and MelonLoader 0.7.3. Install this library when a mod lists
MimicAPI as a dependency. It has no standalone gameplay features or settings.

1. Close MIMESIS.
2. Extract the Nexus package into the MIMESIS game folder so the DLL is at
   `MIMESIS/Mods/MimicAPI.dll`.
3. Keep only one copy of `MimicAPI.dll` in the mod setup; replace an older copy
   when updating.

## Credits and license

Original library: NeoMimicry, copyright 2025. Fork maintenance: DooDesch.
Distributed under the [MIT license](LICENSE), including the original copyright
and permission notice. This fork is maintained independently of NeoMimicry.

## Player and server helpers

Player queries use the current scene's registered players and local avatar.
They exclude monsters and actors left over from other scenes.
`GetCurrentRoom` returns the local avatar's server room. `GetStatManager` and
`GetMovementController` resolve that avatar's server controllers.
These three server helpers return `null` on clients and in the menu, where no
matching server actor exists. The waiting/maintenance maximum-player helpers
return the configured room capacity; member-count helpers return occupancy.

## Building

The build resolves the MIMESIS and MelonLoader assemblies from a local game
install. Point it at your install in any of these ways (highest precedence first):

1. Command line:
   `dotnet build -c Release -p:GamePath="D:\Steam\steamapps\common\MIMESIS"`
2. Environment variable: set `MIMESIS_PATH` to the game install root.
3. A `Directory.Build.user.props` next to `MimicAPI/Directory.Build.props`
   (gitignored - not committed):
   ```xml
   <Project>
     <PropertyGroup>
       <GamePath>D:\Steam\steamapps\common\MIMESIS</GamePath>
     </PropertyGroup>
   </Project>
   ```
4. Auto-detection of a Steam install in the common locations.

Then build:

```
dotnet build -c Release
```

See `MimicAPI/Directory.Build.props` for details, including overriding
`GameAssemblyPath` / `MelonLoaderPath` / `PluginsPath` directly for non-standard
layouts. The game is Mono/net35, so MelonLoader assemblies are taken from
`MelonLoader/net35`.
