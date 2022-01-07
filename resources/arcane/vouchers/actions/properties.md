# Properties

## General properties

These properties are available for all actions.

### Chance

The chance out of 100 for this action to be executed (supports decimals)\
Format: `chance=<chance>` (e.g. `chance=25` for 25%)

### Delay

Delay an action by n ticks\
Format: `delay=<delay>` (e.g. `delay=20` for 1s)

### Permission

Execute the action depending on player's permission.\
Format: `permission=<PermissionMode>:<permission>`

* **PermissionMode:**
  * ADD: The action will be executed only if the player doesn't have this permission and will be added after the first execution
  * ADD\_TEMP: The permission is added, the the action is executed and then the permission is removed
  * NO\_PERMISSION: The action will be executed only if the player doesn't have this permission
  * REQUIRE: The action will be executed only if the player has this permission
  * REMOVE: Same as REQUIRE but the permission is removed after the first execution
* **\<permission>**: String, a permission node

## Specific properties

These properties are available only for certain actions.

### Broadcast

Broadcast the action to certain players.\
Actions: \[bossbar], \[message], \[sound]\
**Format:** `broadcast=<condition>:(value),<condition>:(value)...` or `broadcast=*` to broadcast to all players with no exceptions

* `permission:<permission>`: Broadcast to players with a certain permission
* `radius:<radius>`: Broadcast to players within a radius (supports decimals)
* `world`: Broadcast to players from player's world world

Example:

* `broadcast=permission:example.permission,world`&#x20;
* `broadcast=permission:some.permission,radius:50`
