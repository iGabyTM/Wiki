---
description: Vouchers configuration for v2.0.0
---

# vouchers.yml

## <mark style="color:red;">Format</mark>

Below you will find a detailed structure of a voucher, with all the available options and what values they require. Please see to the [Resources ](vouchers.yml.md#resources)section to learn more about each type of value.

<pre class="language-yaml" data-title="vouchers.yml" data-full-width="true"><code class="lang-yaml">vouchers:
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
      lore: List of String # default: empty
      name: String # default: empty
      damage: Short # default: 0
      glow: Boolean # default: false
      customModelData: Integer # default: 0 | 1.14.4+
      texture: TextureString # default: none
      color: ColorString # default: none | Available only for leather armor
      enchantments: List of EnchantmentString # default: empty
      flags: List of ItemFlag # default: empty
      unbreakable: Boolean # default: false
      banner:
        patterns: List of BannerPatternString # default: empty
    actions: List of Action # default: empty
    #
    # A list of actions that are executed when multiple vouchers are used.
    # Leave this empty to execute 'actions' n times (n = vouchers redeemed)
    #
    bulkActions: List of Action # default: empty
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
        limit: Long # default: <a data-footnote-ref href="#user-content-fn-1">max value</a>
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
          list: List of Option # default: empty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players with one of these permissions can use this voucher
        #
        whitelist:
          list: List of Option # default: empty
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
          list: List of Option # default: empty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players that are in any of these regions can use this voucher
        #
        whitelist:
          list: List of Option # default: empty
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
          list: List of Option # default: empty
          message: Message # default: none
          sound: SoundObject # default: none
        #
        # Only players that are in any of these worlds can use this voucher
        #
        whitelist:
          list: List of Option # default: empty
          message: Message # default: none
          sound: SoundObject # default: none
</code></pre>

## <mark style="color:red;">Resources</mark>

* Java (8)
  * [Boolean](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html) - true or false
  * [Short](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html) - whole numbers without decimal points with values between -32,768 and +32,767
  * [Integer](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html) - similar to Short, but the range is between -2.1 billions and + 2.1 billions
  * [Long](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html) - similar to Short and Integer but the limits are much larger (\~9 quintillions)
  * [Float ](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html)- numbers with decimal points, with values between 0.0 and 1.0 in Minecraft
  * [String](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) - the name Java uses for text, nothing special about this one
  * List<**Type**> - a list that expects elements of the said type, for example `lore: List<String>` expects a list of texts (Strings) that will be set as lore
* [MiniMessage](https://docs.adventure.kyori.net/minimessage)
* [RegEx](https://www.w3schools.com/java/java\_regex.asp) - regular expression
* Spigot (latest)
  * [Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html#field-summary)
  * [DyeColor](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html#enum-constant-summary)
  * [Enchantment](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html#field-summary)
  * [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html#enum-constant-summary)
  * [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html#enum-constant-summary)
  * [PatternType](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/block/banner/PatternType.html#enum-constant-summary) - different patterns a Banner can have

#### <mark style="color:green;">ColorString</mark>

Format: `<red>,<green>,<blue>` (e.g. `255,000,000`), `RRGGBB` (e.g. `FF0000` [HEX](https://htmlcolorcodes.com/color-picker/)) or the name of a [Color](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Color.html#field-summary) (e.g. `RED`)

Example:

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml"># A leather chestplate colored orange
item:
<strong>    material: LEATHER_CHESTPLATE
</strong>    # Spigot default color
    color: ORANGE
    # HEX format
    color: FFA500
    # R,G,B format
    color: 255,165,0
</code></pre>

#### <mark style="color:green;">**EnchantmentString**</mark>

Format: `Enchantment;<level>`

* **Enchantment**: String, the name of an [Enchantment](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/enchantments/Enchantment.html#field-summary) (e.g. `MENDING`), for 1.13+ could also use the `namespace:key` format (e.g. `minecraft:sharpness`)
* **\<level>**: Integer, the level of the enchantment

Example:

{% code overflow="wrap" fullWidth="false" %}
```yaml
# A diamond sword with mending and sharpness 3
item:
  material: DIAMOND_SWORD
  enchantments:
  - MENDING;1
  # The name spigot uses for sharpness
  - DAMAGE_ALL;3
  # Alternative for the previous option available for 1.13+ servers
  - minecraft:sharpness;3
```
{% endcode %}

#### <mark style="color:green;">LimitType</mark>

Values: GLOBAL, PERSONAL, NONE (default, if disabled)

#### <mark style="color:green;">Message</mark>

Format: `Type;<message>` or `<message>` and CHAT will be the default `Type`

* **Type**: ACTION\_BAR, CHAT, TITLE
* **\<message>**: String, the actual message that will be sent, use `[n]` for TITLE to separate the title from subtitle

Examples:

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml"><strong>settings:
</strong>  messages:
    # Simple chat message
    redeem: You have received a voucher
    redeem: CHAT;You have received a voucher
    # Action bar message
    redeem: ACTION_BAR;You have received a voucher
    # Title message
    # 'You have received' will be the title and 'a voucher' the subtitle
    redeem: TITLE;You have received[n]a voucher
</code></pre>

#### <mark style="color:green;">Option</mark>

Format: `regex:<expression>` for [RegEx ](https://www.w3schools.com/java/java\_regex.asp)or just a normal String

Examples: Allow the voucher to be used at `spawn` or on a "player world", same thing applies for regions.

{% code overflow="wrap" %}
```yaml
# Allow the voucher to be used at spawn or on a "player world"
# same format and logic applies for regions.
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
{% endcode %}

#### <mark style="color:green;">BannerPatternString</mark>

Format: `PatternType;DyeColor`

* **PatternType**: String, the name of a [PatternType](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/block/banner/PatternType.html#enum-constant-summary) (e.g. `CREEPER`)
* **DyeColor**: String, the name of a [DyeColor](vouchers.yml.md#format) (e.g. `RED`)

Example

```yaml
# A banner with a black gradient and red border
item: WHITE_BANNER
banner:
  patterns:
    - GRADIENT;BLACK
    - BORDER;RED
```

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### SoundObject

```yaml
<section-name>:
  sound: (1) # Required
  source: (2) # Optional | default: MASTER
  volume: (3) # Optional | default: 1
  pitch: (4) # Optional | default: 1
```

1. **sound**: String, the name of a sound ('[namespace:path](https://minecraft.fandom.com/wiki/Resource\_location)' or just 'path' for vanilla sounds from the 'minecraft' namespace), example: `minecraft:block.note_block.pling` or simply `block.note_block.pling`
2. **source**: String, the name of a sound [Source](https://jd.adventure.kyori.net/api/4.11.0/net/kyori/adventure/sound/Sound.Source.html#enum.constant.summary), example: `MASTER`
3. **volume**: Float, the volume of the sound, example: `0.25`
4. **pitch**: Float, the pitch of the sound, example: `1.50`

#### TextureString

Format: `Type;<value>` or `<value>` and BASE64 will be the default `Type`

* **Type**: BASE64, HDB, PLAYER
* **\<value>**:
  * BASE64: String, texture value (e.g. `BASE64;eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZGNlYjE3MDhkNTQwNGVmMzI2MTAzZTdiNjA1NTljOTE3OGYzZGNlNzI5MDA3YWM5YTBiNDk4YmRlYmU0NjEwNyJ9fX0=`)
  * HDB: Integer, the id of a head from [HeadDatabase](https://www.spigotmc.org/resources/head-database.14280/) (e.g. `HDB;21899`)
  * PLAYER: String, the name of a player (e.g. `PLAYER;MHF_Chest`)

[^1]: Which is about 9 quintillion
