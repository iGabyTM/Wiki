---
description: Various examples to help new users get started with Arcane Vouchers
---

# Example vouchers

### Tag voucher

Unlock access to chat tags with a voucher. The example uses DeluxeTags permissions but it is very easy to modify the voucher to work with another plugin.

```yaml
heart-tag-voucher:
  item:
    material: NAME_TAG
    name: '<red>♥ chat tag'
    lore:
    - '<white>Click to unlock the chat tag!'
  actions:
  - '[permission] ADD deluxetags.tag.heart'
  - '[message] <green>You have unlocked the heart tag! Use /tags to equip it'
  settings:
    permissions:
      blacklist:
        list: [deluxetags.tag.heart]
        message: '<red>Looks lik you already have access to this tag!'
  
```
