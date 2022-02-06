---
description: Vouchers configuration for v2.0.0
---

# vouchers.yml

## Format

{% code title="vouchers.yml" %}
```yaml
vouchers:
  voucherId:
    item:
      #
      # REQUIRED VALUES
      #
      # The name of a material https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html
      material: String # default: PAPER
      #
      # OPTIONAL VALUES
      #
      lore: List<String> # default: empty
      name: String # default: empty
      damage: Short # default: 0
      glow: Boolean # default: false
      customModelData: Integer # default: 0 | 1.14.4+
      texture: TextureString # default: none
      color: ColorString # default: none | Available only for leather armor
      enchantments: EnchantmentString # default: empty
      flags: List<ItemFlag> # default: empty
      unbreakable: Boolean # default: false
      banner:
        patterns: PatternString # default: empty
    actions: List<Action> # default: empty
    #
    # A list of actions that are executed when multiple vouchers are used.
    # Leave this empty to execute 'actions' n times (n = vouchers redeemed)
    #
    bulkActions: List<Action> # default: empty
    #
    # Starting with v2.0.0, all settings are optional
    #
    settings:
      #
      # Messages sent when the voucher is received and redeemed
      #
      messages:
        #
        # {amount} - how many vouchers were received
        #
        receive: Message # default: none
        #
        # {amount} - how many vouchers were redeemed
        #
        redeem: Message # default: none
      #
      # Sounds played when the voucher is received or redeemed
      #
      sounds:
        receive: SoundObject # default: none
        redeem: SoundObject # default: none
      #
      # Make the voucher usable only by the player who received it
      #
      bindToReceiver:
        enabled: Boolean # default: false
        #
        # {player} - the name of the player who can redeem the voucher
        #
        message: Message # default: none
        sound: SoundObject # default: none
      #
      # Whether multiple vouchers can be redeem at one time
      #
      bulkOpen:
        enabled: Boolean # default: false
        limit: Integer # default: MAX
      #
      # Whether the player has to confirm the redeem through a GUI
      #
      confirmation:
        enabled: Boolean # default: false
      #
      # Put the voucher on a cooldown after each usage
      #
      cooldown:
        enabled: Boolean # default: false
        cooldown: TimeString # default: none
        #
        # {left} - the time left
        #
        message: Message # default: none
        sound: SoundObject # default: none
      #
      # Limit how many times a voucher can be used by a player or global
      #
      limit:
        enabled: Boolean # default: false
        type: LimitType # default: NONE
        limit: Long # default: MAX
        message: Message # default: none
        sound: SoundObject # default: none
      #
      # Allow or disallow players to use this voucher based on their permissions
      #
      permissions:
        #
        # Players with one of thes permissions can't use this voucher
        #
        blacklist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players with one of these permissions can use this voucher
        #
        whitelist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
      #
      # REQUIRE WORLDGUARD 6.X.X or 7.X.X https://dev.bukkit.org/projects/worldguard
      # Allow or disallow players to use this voucher based on the region they
      # are standing on
      #
      regions:
        #
        # Players that are in any of these regions can't use this voucher
        #
        blacklist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players that are in any of these regions can use this voucher
        #
        whitelist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
      #
      # Allow or disallow players to use this voucher based on their world
      #
      worlds:
        #
        # Players that are in any of these worlds can't use this voucher
        #
        blacklist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players that are in any of these worlds can use this voucher
        #
        whitelist:
          list: List<Option> # default: emty
          message: Message # default: none
          sound: SoundObject # default: none
```
{% endcode %}

## Resources

* Java (8)
  * [Boolean](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html)
  * [Integer](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html)
  * [Long](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html)
  * [Short](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html)
  * [String](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)
* [MiniMessage](https://docs.adventure.kyori.net/minimessage)
* [RegEx](https://www.w3schools.com/java/java\_regex.asp)
* Spigot (latest)
  * [DyeColor](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html#enum-constant-summary)
  * [Enchantment](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html#field-summary)
  * [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html#enum-constant-summary)
  * [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html#enum-constant-summary)
  * [PatternType](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/block/banner/PatternType.html#enum-constant-summary)

#### ColorString

Format: `<red>,<green>,<blue>` or `RRGGBB` ([HEX](https://htmlcolorcodes.com/color-picker/), without **#**)

#### **EnchantmentString**

Format: `Enchantment;<level>`

* **Enchantment**: String, the name of an [Enchantment](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html#field-summary) (MENDING), for 1.13+ could also use the `namespace:key` format (`minecraft:mending`)
* **\<level>**: Integer, the level of the enchantment

#### LimitType

Values: GLOBAL, PERSONAL, NONE (default, if disabled)

#### Message

Format: `Type;<message>` or `<message>` and CHAT will be the default `Type`

* **Type**: ACTION\_BAR, CHAT, TITLE
* **\<message>**: String, the actual message that will be sent, use `[n]` for TITLE to separate the title from subtitle

#### Option

Format: `regex:<expression>` for [RegEx ](https://www.w3schools.com/java/java\_regex.asp)or just a normal String

Example: Allow the voucher to be used at `spawn` or on a "player world", same thing applies for permissions or regions.

```yaml
worlds:
  whitelist:
    list:
      # When using normal Strings, you can also use %args% but your
      # String must be 1:1 with the world name (e.g. 'Spawn' is not
      # the same as 'spawn')
      - spawn
      # This will match all worlds that start with 'player_world-'
      - regex:player_world-.+
```

#### PatternString

Format: `PatternType;DyeColor`

* **PatternType**: String, the name of a [PatternType](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/block/banner/PatternType.html#enum-constant-summary) (`CREEPER`)
* **DyeColor**: String, the name of a [DyeColor](vouchers.yml.md#format) (`RED`)

#### SoundObject

```yaml
<section-name>:
  sound: (1) # Required
  source: (2) # Optional | default: MASTER
  volume: (3) # Optional | default: 1
  pitch: (4) # Optional | default: 1
```

1. String, the name of a sound ('[namespace:path](https://minecraft.fandom.com/wiki/Resource\_location)' or just 'path' if the namespace is 'minecraft'), example: `minecraft:block.note_block.pling` or `block.note_block.pling`
2. String, the name of a sound [Source](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/sound/Sound.Source.html#enum.constant.summary), example: `MASTER`
3. Float, the volume of the sound, example: `0.25`
4. Float, the pitch of the sound, example: `1.50`

#### TextureString

Format: `Type;<value>` or `<value>` and BASE64 will be the default `Type`

* **Type**: BASE64, HDB, PLAYER
* **\<value>**:
  * BASE64: String, texture value (`BASE64;eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZGNlYjE3MDhkNTQwNGVmMzI2MTAzZTdiNjA1NTljOTE3OGYzZGNlNzI5MDA3YWM5YTBiNDk4YmRlYmU0NjEwNyJ9fX0=`)
  * HDB: Integer, the id of a head from [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (`HDB;21899`)
  * PLAYER: String, the name of a player `(PLAYER;MHF_Chest`)
