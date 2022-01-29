# Commands

To access any admin command, you need [this ](permissions.md#admin-commands)permission.

### Give

Syntax: **/av give \[player/\*] \[voucher] (amount) (arguments...)**\
To give vouchers to all online players, use `*` instead of a player name.\
\
Anything that's after `amount` can be accessed using `%args%` / `%args[INDEX]%` from messages or voucher item / name. By default, arguments are separated by space, but if you need multiple words for one argument, surround them with quotes (`"`).\
\
Example:\
Input: `FirstArgument "Second Argument" ThirdArgument` \
Output: `%args[1]%` - `FirstArgument`, `%args[2]%` - `Second Argument`, `%args[3]%` - `ThirdArgument`\


### Help

Syntax: **/av help**

### List

Syntax: **/av list**

### Reload

Syntax: **/av reload**

### Usages

Syntax: **/av usages \[voucher] \[action] (arguments...)**

#### **Actions**

* **check** - See how many times a voucher was used, requires a player name if the limit type of that voucher is PERSONAL
* **modify** -&#x20;
