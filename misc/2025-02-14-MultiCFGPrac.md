---
layout: post
title: "MultiCFGPrac Command Reference"
permalink: multicfgprac-command-reference
tags: CS2, Metamod, CounterStrikeSharp
---

This command reference is only applicable on my privately hosted *Counter-Strike 2* servers. For those interested in using/writing plugins on CS2 dedicated servers, you can check out [Metamod](https://cs2.poggu.me/){:target="_blank"} and [CounterStrikeSharp](https://docs.cssharp.dev/){:target="_blank"}. The community servers you *probably* know of (running FFA DM, KZ or SURF) make use of such modding frameworks.

<br>
## <u>Features</u>
- Equip weapons from chat
- Automatic map change on empty server
- Deathmatch mode
  - Multiple DM configs (normal/awp/pistol/headshot-only)
  - Persistent client weapon preferences
  - Filter killfeed to individual players
  - Restore player health and (primary and secondary) ammo on kill
  - [WIP] Randomized spawnpoints (Overpass, Ancient, Vertigo, Mirage, Inferno, and Dust 2 are covered thus far)
- Practice mode
  - Save and teleport to grenade lineups
  - Clear thrown grenades on map
  - BOT management system
  - BOT damage and blind duration report
  - Coloured smoke grenades
  - Grenade airtime report (smoke grenades and mollies/incendiaries)
- Custom player models

<br><br><br>
## <u>Commands</u>
> NOTE: This is an example of a `<required>` and `[optional]` parameter.

### General commands
- `!dm` ~ normal deathmatch.
- `!awp` ~ AWP-only deathmatch.
- `!pistoldm` ~ pistol-only deathmatch 
- `!hsdm` ~ headshot-only deathmatch.
- `!prac` ~ nade practice mode.
- `!comp` ~ competitive mode.
- `!retake` ~ retake mode. (uses the [cs2-retakes](https://github.com/B3none/cs2-retakes) plugin)
- `!guns` ~ lists available weapons players can equip.
- `!models` ~ lists custom player models to console. (e.g. type `!flash` to become ⚡**The Flash**⚡)
- `!ogmodel` ~ reverts to the default player model.

<br><br>
### Miscellaneous commands
- `!map <map name>` ~ changes map. (`map name` can be **'de_dust2'** or **'dust2'**)
- `!dropgun` ~ toggles `mp_death_drop_gun` on/off.
- `!showimpacts` ~ toggles `sv_showimpacts` onoff.
- `!pm` ~ private messages a player.
- `!help` ~ displays a small command reference to chat.
- `!chelp` ~ displays a command reference of all commands to console.

<br><br>
### Practice commands
- `!savepos` ~ saves player's current position. (future respawns will inherit this position, until you call `!delpos`)
- `!tpos` ~ teleports to a saved player position.
- `!delpos` ~ deletes the saved player position.
- `!noflash` ~ toggles blinding effect on/off for flashbangs on yourself.
- `!testflash` ~ saves current position for testing flashes against yourself from another position (run the *same* command again to disable it).
- `!breakprops` ~ breaks all unbroken props. (according to a preset list of game props)
- `!restoreprops` ~ restores all broken props.

<br>
#### Bot commands
- `!bot` ~ spawns a bot where player is standing (use `!tbot` or `!ctbot` for specific teams).
- `!crouchbot [bot name]` ~ spawns a crouching bot where player is standing when ran without arguments; and toggles the crouching state of `bot name` when given one.
- `!boost` ~ spawns a bot boosting player (use `!crouchboost` for a crouching bot).
- `!movebot <bot name>` ~ teleports a bot to your position.
- `!nobot <bot name>` ~ removes a bot (use `!nobots` to remove all your spawned bots).
- `!helmet <bot name>` ~ toggles a bot's helmet on/off.
- `!armor <bot name>` ~ toggles a bot's kevlar/full armor on/off.
 
<br>
#### Nade commands
- `!clear` ~ clears all thrown grenades on the map.
> NOTE: Commands below default to the most recently accessed **grenade ID** if none is provided.
- `!nsave <lineup name>` ~ saves a grenade lineup on the server with a name.
- `!nlist [grenade id] [filter]` ~ displays all saved grenade lineups on current map; can be filtered with a `grenade id` or the case-sensitive `filter` (by lineup name) parameter.
- `!ngoto [grenade id]` ~ teleports player to a grenade lineup.
- `!ndesc [grenade id] <description>` ~ passes a description to a grenade lineup, works for updating it as well. (**NOT** necessary for saving a grenade lineup)
- `!nmove [grenade id]` ~ updates the position of an existing grenade lineup.
- `!nrename [grenade id] <new lineup name>` ~ renames an existing grenade lineup.
- `!ndelete <grenade id>` ~ deletes a grenade lineup.

<br><br><br>
## <u>Features to come...</u>
- Practice mode
  - Throw (and rethrow) saved grenade lineups by id
  - Teleport to all T/CT spawnpoints
