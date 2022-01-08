---
description: Configuration for v2.0.0
---

# config.yml

{% code title="config.yml" %}
```yaml
settings:
  disable:
    #
    # If 'true', people won't be able to craft items using vouchers
    #
    crafting: true
  command: arcanevouchers
  alias:
    - av
  #
  # Any cooldown lower than the threshold won't be saved to database
  # Set it to 0 to save all cooldowns. The value supports formatting with letters:
  # h - hours
  # m - minutes
  # s - seconds
  #
  cooldownSaveThreshold: 1m

confirmationGui:
  size: 3 # The number of rows, min 1 and max 6
  title: 'Confirmation GUI' # The title
  #
  # All items listed below accept the same configuration
  # options as the vouchers (see vouchers.yml)
  #
  items:
    #
    # The buttons must be here, otherwise the GUI won't work
    #
    buttons:
      confirmation:
        material: EMERALD_BLOCK
        slot: 12
        name: '<green><b>YES</b></green>'
      cancel:
        material: REDSTONE_BLOCK
        slot: 14
        display_name: '<red><b>NO</b><red>'
    #
    # Items listed here are only used for design
    #
    other: {}
```
{% endcode %}
