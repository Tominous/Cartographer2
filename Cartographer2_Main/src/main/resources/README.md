# Cartographer 2
*The best minimap plugin for Bukkit*
![Falcon's Rock](https://i.imgur.com/RCkxvQ4.png)

## What is this?
Cartographer 2 aims to be a better version of the original Cartographer. It is unfortunately not a lightweight plugin by any means. However, it has been optimized to be as fast as possible and provide the best results. It saves map data asynchronously to minimize the impact of file IO. The processing of each chunk is also done on separate threads so that loading chunks is done fast and efficiently. Rendering the map on the items, which requires the most amount of processing power, is multi-threaded to distribute the load and finish as fast as possible. Color conversion and mixing is done by Jetp250's image util, which dithers and matches colors extremely fast for almost no delay. In addition to speed, Cartographer2 features a module system and an (almost) fully featured API to customize everything easily.

## How to install
- Place in the `plugins/` folder and restart server
- Delete this file to regenerate any missing files/folders, such as the built in palettes, or images.

## Commands
**Ⓟ** - Player command only
**₵** - Command line only
- `/cartographer  <create|get|delete|reload|unload|load|module|settings> ...` - Requires `cartographer`.
  - `/cartographer create <id>` - Create a minimap with the given id. Minimaps can span worlds, so normally one is enough. Requires `cartographer.map.create`.
  - `/cartographer delete <id>` - Delete the minimap with the given id. Removes it from the server and from disk. Requires `cartographer.map.delete`.
  - **Ⓟ** `/cartographer get <id>` - Get a map item for the minimap with the given id. Requires `cartographer.map.get`.
  - `/cartographer get <id> <player> [slot]` - Give a map item for the minimap with the given id to the specified player with an optional slot. Requires `cartographer.map.give`.
  - `/cartographer reload` -  Reload Cartographer2's config. Requires `cartographer.reload`.
  - `/cartographer reload <id>` -  Reload a minimap. Requires `cartographer.map.reload`.
  - `/cartographer unload <id>` - Unload a minimap with the given id. Requires `cartographer.map.unload`.
  - `/cartographer load <id>` - Load an unloaded minimap with the given id. Requires `cartographer.map.load`.
  - `/cartographer module <list|reload|enable|disable> ...` Requires `cartographer.module`.
    - `/cartographer module list` - List all the modules, regardless if they are disabled. Requires `cartographer.module.list`.
    - `/cartographer module reload` - Reload all the modules. Requires `cartographer.module.reload`.
    - `/cartographer module enable <id>` - Enable the specified module. Requires `cartographer.module.enble`.
    - `/cartographer module disable <id>` - Disable the specified module. Requires `cartographer.module.disable`.
    - `/cartographer module load <file>` - Load the specified file. Requires `cartographer.module.load`.
    - `/cartographer module unload <id>` - Unload the specified module. Requires `cartographer.module.unload`.
  - `/cartographer settings <set|get|setother|getother> ...` - Requires `cartographer.settings`.
    - **Ⓟ** `/cartographer settings set <property> <value>` - Set a setting to a given property. Requires `cartographer.settings.set.<property>`.
    - **Ⓟ**  `/cartographer settings get <property>` - Get the value of the property. Requires `cartographer.settings.get.<property>`.
    - **Ⓟ** `/cartographer settings setother <player> <property> <value>` - Set the given property of another player. Requires `cartographer.settings.setother.<property>`.
    - **Ⓟ** `/cartographer settings getother <player> <property>` - Get the value of the property of another player. Requires `cartographer.settings.getother.<property>`.
    - **₵** `/cartographer settings set <player> <property> <value>` - Set the property of another player from the console. Requires `cartographer.settings.setother.<property>`.
    - **₵** `/cartographer settings get <player> <property>` - Get the property of another player from the console. Requires `cartographer.settings.getother.<property>`.

## Permissions
- `cartographer` - Allows access to the cartographer command.
- `cartographer.admin` - Master permission.
- `cartographer.reload` - Reload Cartographer2's settings and images.
- `cartographer.map` - Allows access to the map related commands.
- `cartographer.map.admin` - Master permission for maps.
- `cartographer.map.list` - List all minimaps.
- `cartographer.map.reload` - Reload a minimap.
- `cartographer.map.unload` - Unload a minimap.
- `cartographer.map.load` - Load a minimap.
- `cartographer.map.give` - Give a minimap to someone. Inherits `cartographer.map.get`
- `cartographer.map.get` - Get a minimap for yourself.
- `cartographer.map.create` - Create a new minimap.
- `cartographer.map.delete` - Delete a minimap.
- `cartographer.module` - Allows access to the module sub-command.
- `cartographer.module.admin` - Master permission for modules.
- `cartographer.module.list` - List all modules.
- `cartographer.module.reload` - Reload all modules. Inherits `cartographer.module.load` and `cartographer.module.unload`
- `cartographer.module.load` - Load a given module.
- `cartographer.module.unload` - Unload a given module.
- `cartographer.module.disable` - Disable a given module.
- `cartographer.module.enable` - Enable a given module.
- `cartographer.settings` - Allows access to the settings sub-command.
- `cartographer.settings.admin` - Master permission for settings
- `cartographer.settings.set` - Set and get the values for properties of yourself. Inherits `cartographer.settings.get`
- `cartographer.settings.get` - Get the values for properties of yourself.
- `cartographer.settings.setother` - Set and get values for properties of other people and yourself. Inherits `cartographer.settings.getother` and `cartographer.settings.set`
- `cartographer.settings.getother` - Get the values for properties of others and yourself. Inherits `cartographer.settings.get`
- `cartographer.settings.set.cursor` - Set the value for the cursor property of yourself. `true` by default. Inherits `cartographer.settings.get.cursor`.
- `cartographer.settings.get.cursor` - Get the value for the cursor property of yourself. `true` by default
- `cartographer.settings.setother.cursor` - Set the value of the cursor property for another player. Inherits `cartographer.settings.getother.cursor`.
- `cartographer.settings.getother.cursor` - Get the value of the cursor property for another player. Inherits `cartographer.settings.getother`.
- `cartographer.settings.set.rotate` - Set the rotate property for yourself. `true` by default. Inherits `cartographer.settings.get.rotate`.
- `cartographer.settings.get.rotate` - Get the value for the rotate property of yourself. `true` by default
- `cartographer.settings.setother.rotate` - Set the value of the rotate property for another player. Inherits `cartographer.settings.getother.rotate`.
- `cartographer.settings.getother.rotate` - Get the value of the rotate property for another player. Inherits `cartographer.settings.getother`.

## Settings:
- `cursor` - Whether or not the cursor is active and visible. Can be set to `true` or `false`.
- `rotate` - Whether or not rotation is on. Can be set to `true`, `false`, or `unset`.

## Module ideas
- Show land claims
- Draw animated beacons
- Located nearby entities and mark players
- Add a sepia filter to the worldmap
- Show a treasure hunt
- Display pathfinding points
- Show locations and statistics
- Cool looking HUD
- RPG style waypoints

## TODO
- Add vanilla module integration
- Fix the wiki
- Add factionsuuid and Residence integration
- Lands integration - Put on hold unfortunately

## More information
- [Github](https://github.com/BananaPuncher714/Cartographer2)
- [Wiki](https://github.com/BananaPuncher714/Cartographer2/wiki)
- [Spigot](https://www.spigotmc.org/resources/46922/)

## Credits
- `BananaPuncher714` - Creator, Developer, Maintainer
- `Jetp250` - Developer
- `REjoin` - Supporter