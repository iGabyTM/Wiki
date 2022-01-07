# Actions

## Format

Starting with v2.0.0 the format for actions was changed to the following `{`[`properties`](./#properties)`} [`[`id`](./#undefined)`] args`.

### Properties

A set of `key=value` options separated by space. Read more about properties on their own page. 👇

{% content-ref url="properties.md" %}
[properties.md](properties.md)
{% endcontent-ref %}

### ID

Each action has its own unique identifier. The id is also case-insensitive, meaning that `[CONSOLE]` is the same as `[console]`.

#### Default actions

* Commands
  * [\[console\] \<command>](./#console)
  * [\[player\] \<command>](./#player-execute-a-command-as-the-player-that-is-using-the-voucher)
* Economy
  * [\[addexp\] \<amount>(L)](./#addexp)
  * [\[item\] \<material>(:damage) \<amount> (args...)](./#item)
* Message
  * [\[bossbar\] \<message>](./#bossbar)
  * [\[chat\] \<message>](./#chat)
  * [\[message\] \<message>](./#message)
* Other
  * [\[sound\] \<sound>](./#sound)

#### Actions with dependencies

* Crates
  * [\[givecratereloadedkey\] \<crate> (amount)](./#givecratereloadedkey)
* [Vault](https://www.spigotmc.org/resources/vault.34315/)
  * [\[addmoney\] \<amount>](./#addmoney)
  * [\[permission\] \<ADD/REMOVE> \<permission.node> (world)](./#permission)

## Available actions

### Default actions

{% hint style="info" %}
Command
{% endhint %}

#### \[console] - execute a command from [console](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/command/ConsoleCommandSender.html) <a href="#console" id="console"></a>

{% tabs %}
{% tab title="Arguments" %}
**\<command>**: String, the command to execute
{% endtab %}

{% tab title="Untitled" %}
`[console] kill %player_name`   - make the console run `/kill <name>`
{% endtab %}
{% endtabs %}

#### \[player] - execute a command as the player that is using the voucher <a href="#player" id="player"></a>

{% tabs %}
{% tab title="Arguments" %}
**\<command>**: String, the command to execute (the slash is not required, unless the command has two or more)
{% endtab %}

{% tab title="Examples" %}
`[player] kit Daily` - make the player run `/kit Daily`
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Economy
{% endhint %}

#### \[addexp] - give to the player an amount of EXP <a href="#addexp" id="addexp"></a>

{% tabs %}
{% tab title="Arguments" %}
**\<amount>(L):** Integer, amount of exp to add. By appending an `L` after, levels of exp will be given instead of points
{% endtab %}

{% tab title="Untitled" %}
`[addexp] 100` - give 100 EXP points to the player

`[addexp] 100L` - give 100 levels of EXP to the player
{% endtab %}
{% endtabs %}

#### \[item] - give to the player a custom item <a href="#item" id="item"></a>

A format similar to EssentialsX's is used.

{% tabs %}
{% tab title="Arguments" %}
**Required**

* **material(:damage)**: String, name of a [Material](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html#enum-constant-summary). To specify its damage, add `:damage` after (`INK_SACK:4` for lapiz lazuli on < 1.13)
* **amount**: Integer, the amount of the item

\
**Optional**

* **name:** String, the name of the item, use `_` for space
* **lore**: String, the lore of the item, use `_` for space and `|` for a new line
* **flags:** List, a comma separated list of [ItemFlag](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html#enum-constant-summary) names
* **unbreakable:** make the item unbreakable, this argument doesn't require a value
* **model**: Integer, the custom model data of this item (1.14.4+)
* **nbt:** String, a JSON string representing item's NBT, some escaping should be done, mostly for quotes. This argument must be the last one since it takes everything that's after `nbt:` as value

For enchantments simply use `Enchantment:level`\
For `name` and `lore` , if you want to use `_` and `|` you will have to escape them by adding a `\` before.
{% endtab %}

{% tab title="Examples" %}
`[item] LEATHER_CHESTPLATE 1 lore:<red>What's</red>_<blue>up?</blue>` - a leather chestplate with a lore saying <mark style="color:red;">What's</mark> <mark style="color:blue;">up?</mark>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Message
{% endhint %}

#### \[bossbar] - display a boss bar on player's screen <a href="#bossbar" id="bossbar"></a>

{% tabs %}
{% tab title="Arguments" %}
**message**: String, the message that will be displayed
{% endtab %}

{% tab title="Properties" %}
**color**: String, the name of a [Color](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/bossbar/BossBar.Color.html#enum.constant.summary) (default: [WHITE](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/bossbar/BossBar.Color.html#WHITE))

**duration**: Ticks, how long the bar will be displayed (default: 200 or 10 seconds)

**flags**: List, comma separated list of [Flag](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/bossbar/BossBar.Flag.html#enum.constant.summary) names (default: empty)

**overlay**: String, the name of an [Overlay ](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/bossbar/BossBar.Overlay.html#enum.constant.summary)(default: [PROGRESS](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/bossbar/BossBar.Overlay.html#PROGRESS))

**progress**: Float, the progress of the bar (default: [MAX\_PROGRESS](https://jd.adventure.kyori.net/api/4.9.3/constant-values.html#net.kyori.adventure.bossbar.BossBar.MAX\_PROGRESS))
{% endtab %}

{% tab title="Examples" %}
`{color=BLUE progress=0.5 display=200} [bossbar] <green>Hey</green>` - a blue bar that will stay on the screen for 10 seconds, with 50% progress and a green text saying <mark style="color:green;">Hey</mark>&#x20;
{% endtab %}
{% endtabs %}

#### \[chat] - make the player send a message in chat <a href="#chat" id="chat"></a>

{% tabs %}
{% tab title="Arguments" %}
**message**: String, the message that will be sent
{% endtab %}

{% tab title="Examples" %}
`[chat] <yellow>Hello everyone, my name is %player_name%!<yellow>` - a yellow message saying <mark style="color:yellow;">Hello everyone, my name is \<name>!</mark>
{% endtab %}
{% endtabs %}

#### \[message] - send a message to the player <a href="#message" id="message"></a>

{% tabs %}
{% tab title="Arguments" %}
**message**: String, the message that will be sent.
{% endtab %}

{% tab title="Properties" %}
**broadcast:** see [Properties/Broadcast](properties.md#broadcast) (default: none)

**type**: String, the type of the message (ACTION\_BAR, CHAT, TITLE) (default: `CHAT`).\
\
**Properties for** `TITLE`:

* **fadeIn:** Ticks, the time the title will fade-in (default: 10 or 0.5 seconds)
* **fadeOut:** Ticks, the time the title will fade-out (default: 20 or 1 second)
* **stay**: Ticks, the time the title will stay (default: 70 or 3.5 seconds)

For `TITLE`, use `[n]` to separate the title from subtitle (`This is the title[n]And this is the subtitle`)
{% endtab %}

{% tab title="Examples" %}
`{type=TITLE stay=100] [message] <blue>You have won</blue>[n]<dark_green>$</dark_green><green>50,000</green>`- a title that will stay on the screen for 5 seconds saying `You have won` `$50,000`

`[message] <red>Hey %player_name%, how are you?<red>` - a red chat message saying <mark style="color:red;">Hey \<name>, how are you?</mark>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Other
{% endhint %}

#### \[sound] - play a sound to the player <a href="#sound" id="sound"></a>

{% tabs %}
{% tab title="Arguments" %}
**sound**: NamespacedKey, the key of the sound
{% endtab %}

{% tab title="Properties" %}
**broadcast**: see [Properties/Broadcast](properties.md#broadcast) (default: none)

**pitch**: Float, the pitch of the sound (default: `0`)

**source**: String, the name of a [Source](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/sound/Sound.Source.html#enum.constant.summary) (default: [MASTER](https://jd.adventure.kyori.net/api/4.9.3/net/kyori/adventure/sound/Sound.Source.html#MASTER))

**volume**: Float, the volume of the sound (default: `0`)
{% endtab %}

{% tab title="examples" %}
`{source=AMBIENT} [sound] minecraft:ambient.cave` - play the sound from `AMBIENT` source

`[sound] custom:sound_name` - play a custom sound
{% endtab %}
{% endtabs %}

### Actions with dependencies

{% hint style="info" %}
Vault
{% endhint %}

#### \[addmoney] - add money to player's balance <a href="#addmoney" id="addmoney"></a>

<mark style="color:green;">An economy plugin is required to use this action.</mark>

{% tabs %}
{% tab title="Arguments" %}
**amount**: Double, the amount of money to give
{% endtab %}

{% tab title="Examples" %}
`[addmoney] 125.50`
{% endtab %}
{% endtabs %}

#### \[permission] add or remove a permission to the player <a href="#permission" id="permission"></a>

<mark style="color:green;">A permissions plugin is required to use this action.</mark>

{% tabs %}
{% tab title="Arguments" %}
**Required**:

* **action:** String, the name of the action to perform, `ADD` or `REMOVE`
* **permission**: String, the permission node

**Optional**:

* &#x20;**world**: String, the name of the world where the permission will be added / removed (default: player's world)
{% endtab %}

{% tab title="Examples" %}
`[permission] ADD some.permission world_nether` - add the permission only on world\_nether

`[permission] REMOVE some.permission` - remove the permission global
{% endtab %}
{% endtabs %}

