---
description: From here you can add custom NBT tags to vouchers
---

# vouchers-nbt.txt

## Format

{% code title="vouchers-nbt.txt" %}
```
voucher-id {SNBT here}
```
{% endcode %}

[SNBT](https://minecraft.fandom.com/wiki/NBT\_format#SNBT\_format) or stringified NBT is the format used by Minecraft for stuff like `/give` commands for NBT. It is very easy to use, you can copy the SNBT from a `/give` command and paste it in the file.

## Examples

A colored leather item\
`/give NAME minecraft:leather_chestplate{display:{color:14574937}} 1`&#x20;

```
voucher-id {display:{color:14574937}}
```

## Resources

* [/give command generator](https://www.gamergeeks.net/apps/minecraft/give-command-generator)
