# Changelog

All changes to MimicAPI are in this file.
The format follows [Keep a Changelog](https://keepachangelog.com/), and the project uses Semantic
Versioning.

## [0.4.3] - 2026-10-27

- Build against MIMESIS 0.4.0 while retaining existing public API signatures.
- Resolve the local avatar and player lists from the current scene. Player lists exclude monsters and actors from other scenes.
- Return the local avatar's actual server room instead of the first playable room.
- Resolve StatManager and MovementController from the matching server actor. These server-only helpers return null on clients.
- Return configured waiting and maintenance room capacity instead of current occupancy.

## [0.4.2]

### Fixed
- Read the player alive state from the client actor's `dead` property instead of looking for a server method on a Unity component.
- Read room currency through the inherited public property so derived room types return their actual balance.

### Changed
- Build the DooDesch maintenance fork against MIMESIS 0.3.2 references.
- Include the original MIT license and fork attribution in the Nexus package.
- Set the local build version to 0.4.2 while keeping the `MimicAPI` assembly and public API names.

## [0.4.1]

### Fixed
- The release carries the DLL of that build. `thunderstore/MimicAPI.dll` was in the repository, and the release job copied the folder over the fresh DLL, thus every release up to 0.4.0 shipped old code under a new version.

## [0.4.0]

### Added

- `McpPlugin`: a set of static delegates that a MelonLoader MCP bridge finds by reflection. It gives
  the commands `get_session_state`, `get_world_state`, `list_rooms`, `get_room` and `get_players`,
  and it tells the bridge if this machine is the host. All types in the signatures come from the
  standard library, thus no assembly must reference the other one.
- `ServerNetworkAPI.GetPlayerCountInSession()`: the number of players in the session.
- `ServerNetworkAPI.GetSteamServerSocket()`: the `ServerSocket` of the Steam transport. It is a
  private field of the `FishySteamworks` component, not a field of `VWorld`.

### Changed

- `ServerNetworkAPI.GetMaximumClients()` now reads the limit of the server, as the name says. Before
  it gave the number of players in the session. With FakePlayers the two numbers are close together,
  thus the mistake was not visible.
- The version of the DLL comes from the tag. Before, every build said 1.0.0.

### Fixed

- The Thunderstore job runs only in the upstream repository. Only that repository can publish in the
  namespace NeoMimicry, thus a tag on a fork made a failed run.
- The package description on Thunderstore says what the package is.
