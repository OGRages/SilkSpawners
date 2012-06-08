SilkSpawners - harvest mob spawners with silk touch

Ever wanted to move a mob spawner? With SilkSpawners, you can now pick up and move 
monster spawners using tools with the "silk touch" enchantment.

**[Download SilkSpawners 2.0](http://dev.bukkit.org/server-mods/silkspawners/files/14-silk-spawners-2-0/)** - released 2012/06/07

Features:

* Spawner retains creature type
* Works on legit spawners
* Optional showing of creature type when spawners are placed or broken
* Optional /spawner command to view creature type of spawner you are looking at 
* Optional /spawner [creature] to change an existing spawner in the world, if in your crosshairs
* Optional /spawner [creature] to put a new spawner item in your empty hand
* Optional /spawner [creature]egg to put a new spawn egg in your empty hand
* Optional crafting of spawners using monster eggs + eight iron bars ([as seen here](http://imgur.com/KrWGI), [source](http://www.reddit.com/r/Minecraft/comments/oodql/great_idea_mob_spawner_recipe/)) 
* Optional left-click spawner with spawn egg to change type (ops only by default)
* Optional changing spawner type with spawn egg (either consuming or not consuming egg)
* Optional permissions support
* Optional support for custom mobs added by client/server mods
* Optional support for spawning any entity with spawn eggs (dragons, non-creature entities, etc.)
* Optional support for dumping entity ID map on startup for debugging mods
* Compatible with CraftBukkit++ (see spawnersUnstackable)
* Compatible with MCPC and ported mods (auto-detects IDs)
* Compatible with Not Enough Items (newer builds only)
* Compatible with Spout (optional)
* Flexible creature type names on input (pigman, zombiepigman, pigzombie, etc. all accepted), official names on output (Magma Cube, not "LavaSlime")

## Usage
Acquire a tool with Silk Touch, break a mob spawner using said tool, place the spawner. Your spawner has now been moved. 

Many additional features can be enabled if desired, see below.

[Forum thread](http://forums.bukkit.org/threads/mech-fix-info-admn-silkspawners-v1-0-harvest-mob-spawners-1-1-r4.59077/)

## Configuration
*usePermissions* (false) - Whether to use Bukkit's superperms system, or the defaults below.

*useWorldGuard* (true) - Whether to use [WorldGuard](http://dev.bukkit.org/server-mods/worldguard/) protection, if present.

*minSilkTouchLevel* (1) - Minimum enchantment level required for Silk Touch to harvest spawners. Normally Silk Touch I is required, but you can set this to 0 to make no enchantment required, or 2+ to require non-standard (normally unobtainable) enchantments.

*destroyDropEgg* (false) - Whether to give a spawn egg when spawner is destroyed without Silk Touch.

*destroyDropXP* (0) - Experience points to drop when spawner is destroyed.

*destroyDropBars* (0) - Iron bars to drop when spawner is destroyed.

*ignoreFakeBreakEvents* (true) - Ignore subclassed spawner block break events sent by other plugins (such as mcMMO with superbreaker).

*consumeEgg* (true) - Consume spawn eggs used to change spawners, or otherwise keep the egg in the player's inventory.

*useReflection* (true) - Use reflection to get/set mob IDs, or otherwise use Bukkit's wrapper. Required for custom mobs.

*spawnEggOverride* (false) - Override CraftBukkit's spawn egg routine and allow you to spawn [any entity](http://www.minecraftwiki.net/wiki/Data_values#Entity_IDs) whatsoever by right-clicking the appropriate spawn eggs -- any entity is allowed, including enderdragons, ender crystals, primed TNT, boats, or even invalid entities, so be careful (note that SilkSpawners won't give you an egg for any item using /ss if it isn't in the config) -- although IDs can be disabled with the option below. Mainly intended for testing purposes, or if you want to spawn modded items not recognized by CraftBukkit.

*spawnEggOverrideSpawnDefault* (true) - If no *enableSpawnEggOverrideAllowSpawn* is given per-creature, use this instead.

*enableCreatureDefault* (true) - If no *enable* is given per-creature, use this instead.

*verboseConfig* (false) - Log verbose configuration information on load.

*spawnerCommandReachDistance* (6) - How close you have to be to use the /spawner command.

*craftableSpawners* (false) - Enable crafting mob spawners using spawner egg in center surrounded by 8 iron bars.  Once enabled, crafting spawners for individual creatures can be disabled by setting *enableCraftingSpawner* to false in the *creatures* section below (if omitted, will default to true, but both config options must be enabled for spawners to be craftable).

*useSpout* (true) - Set to false to not use Spout features even if Spout plugin is present. If Spout is not detected, this option has no effect.

*notifyOnClick* (true) - Whether to notify a player the spawner type when clicking a spawner in inventory.

*notifyOnHold* (true) - Whether to notify a player the spawner type when holding a spawner.

*spawnersUnstackable* (false) - Prevent spawners from stacking, by setting max stack size to 1. Useful on CraftBukkit++ to prevent spawners from stacking when dropped as items. Not needed on vanilla CraftBukkit builds.

*defaultCreature* (null) - When generic spawner items are placed, spawn this creature (or null for Minecraft's default, pigs).

All spawner items obtained using SilkSpawners will have the creature type stored, but the default creature will be used if the spawner is obtained using:

* /give player 52
* 1.9 beta pre-release 6 silk touch
* other plugins not knowledgeable of SilkSpawners' conventions


*creatures* - Mapping between internal mob ID string for spawners, and other crucial information. Keys include:

*creatures.X.aliases*: An optional list of aliases to recognize as alternate names for the mob.

*creatures.X.displayName*: The human-readable name of the mob.

*creatures.X.enable* (true): If false, this entity is skipped entirely and not recognized by SilkSpawners.  Useful to exclude non-mob entities.  If this key is missing, *enableCreatureDefault* will be checked instead.  Note that entities not auto-detected are always skipped, so this key is safe to leave false for entities for mods you don't have installed.

*creatures.X.enableCraftingSpawner* (true): If *craftableSpawners* is enabled (see above), then a crafting recipe will be enabled for this mob unless this config option is false.

*creatures.X.enableSpawnEggOverrideAllowSpawn* (true): If *spawnEggOverride* is enabled, allow spawn eggs to be used for this creature. Set to false to block spawn eggs. If this key is missing, *spawnEggOverrideSpawnDefault* will be checked instead.  Note that if *spawnEggOverride* is disabled, this option has no effect.

## Permissions
**Permission support is optional** and off by default. When turned off, the settings shown in parentheses below are used, intended to allow for easy setup with minimal configuration. 

For more advanced setup, set *usePermissions: true* in config.yml, and all permission nodes will be set to *false*, allowing for flexible configuration through your permission plugin as desired.

*silkspawners.info* (true) - Allows you to see informative messages about the spawners as you place and break them

*silkspawners.silkdrop* (true) - Allows you to use silk touch to acquire mob spawner items

*silkspawners.destroydrop* (true) - Allows you to destroy mob spawners to acquire mob spawn eggs / iron bars / XP (as configured)

*silkspawners.viewtype* (true) - Allows you to view the spawner type using /spawner

*silkspawners.changetype* (op) - Allows you to change the spawner type using /spawner [creature]

*silkspawners.changetypewithegg* (op) - Allows you to change the spawner type by left-clicking with a spawn egg

*silkspawners.freeitem* (op) - Allows you to get spawner items in your hand for free using /spawner [creature]

*silkspawners.freeitemegg* (op) - Allows you to get spawn eggs in your hand for free using /spawner [creature]egg

## Technical Details
SilkSpawners stores the entity ID of creature in two places within the mob spawner item:

* Durability (damage value), if possible.  SilkSpawners does not rely on this field, although it will use it if it is available on newer builds which allow storing data on mob spawner items (see [BUKKIT-329](https://bukkit.atlassian.net/browse/BUKKIT-329)).

* Enchantment SILK\_TOUCH level

When a spawner block is broken, a spawner item drops with the appropriate entity ID stored, obtained from the creature spawner tile entity (CraftCreatureSpawner).  When a spawner block is placed, the entity ID is read from the item and the spawner creature type is set (using the CreatureSpawner BlockState). 

*For plugin developers*: if you want to interoperate with SilkSpawners' monster spawner items, use `entityID = (short)item.getEnchantmentLevel(Enchantment.SILK_TOUCH)` or `item.addUnsafeEnchantment(Enchantment.SILK_TOUCH, entityID)` on the `ItemStack`, the enchantment level storing the creature type [Entity ID](http://www.minecraftwiki.net/wiki/Data_values#Entity_IDs).

Bukkit provides an [EntityType](http://jd.bukkit.org/apidocs/org/bukkit/entity/EntityType.html) wrapper, but it is implemented using an enum which cannot be easily extended by mods (without using reflection, as they do for the ItemStack wrapper), so SilkSpawners does not use this enum when possible, and instead directly accesses the net.minecraft.server classes if it can. If it fails or if useReflection is false, SilkSpawners will fallback to the EntityType wrapper.

## Limitations
SilkSpawners only changes the spawner type, it does not manage the spawning itself; the spawning algorithm remains up to Minecraft. Other plugins offer more control.

If creaturebox is also installed, drops two spawners. Install either SilkSpawners or creaturebox, not both.

Not Enough Items may show all spawners as "Pig", because it does not recognize how SilkSpawners stores the spawner creature type (should be fixed after [BUKKIT-329](https://bukkit.atlassian.net/browse/BUKKIT-329)).

In the inventory window, item description is "Monster Spawner" for all kinds of spawners.  Fixing this requires a client-side mod.

## See Also
Want to make Silk Touch yet more useful? Also try Pickaxe + Silk Touch II from [EnchantMore](http://dev.bukkit.org/server-mods/enchantmore/).

Other relevant plugins:

* [creaturebox](http://dev.bukkit.org/server-mods/creaturebox/)
* [MonsterBox](http://dev.bukkit.org/server-mods/monsterbox/)
* [Mob Spawner Changer](http://forums.bukkit.org/threads/misc-mech-mob-spawner-changer-v0-3-change-what-a-mob-spawner-spawns-1337.26038/)
* [SilkierTouch](http://dev.bukkit.org/server-mods/silkiertouch/)
* [ChangeSilkTouch](http://dev.bukkit.org/server-mods/changesilktouch/)
* [felega.block](http://forums.bukkit.org/threads/multiple-felegas-plugin-pile.54916/)
* [SuperSimpleSpawners](http://dev.bukkit.org/server-mods/supersimplespawners/)
* [MobSpawnerEggChanger](http://dev.bukkit.org/server-mods/sec/)

***[Fork me on GitHub](https://github.com/mushroomhostage/SilkSpawners)***

