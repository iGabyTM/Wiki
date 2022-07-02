---
description: >-
  Built-in placeholders for generating random elements or evaluate math
  equations
---

# Tags

### Chance

Get an element from a list using a chance system (0 to 100, supporting decimals).\
Format: `chance:{(chance)=(item),(chance)=(item),default=(default item)}`\
\
Placeholders can be used for `chance` and using the `default` keyword instead of a chance, you can specify a default value for when the player is unlucky. If no default value is specified, nothing \
will be returned.\
\
Examples:

* `chance:{85=STONE 65,10=COAL 64,5=DIAMOND 4,default=DIRT 1}` - 85% for `STONE 64`, 10% for `COAL 64`, 5% for `DIAMOND 4` and the default value `DIRT 1`

### Math

Powered by [EvalEx](https://github.com/uklimaschewski/EvalEx), the math tag allows to evaluate math equations to get the result.\
Format: `math:{(scale),<equation>}` or `math:{<equation>}`\
Examples:

* `math:{3,10 / 3}` = 3.000
* `math:{10 / 3}` = 3

### Random Double

Generate a random [Double ](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html)between a min (inclusive) and max (inclusive) value.\
Format: `random:{(precision),<min>,<max>}` or `math:{<min>,<max>`\
Examples:

* `random:{0,100}` = 5.215616126 (without `precision` all decimals are returned)
* `random:{3,0-100}` = 5.231

### Random Element

Pick a random element from a comma separated list\
Format: `randomE:{E1,E2,E3...,En}`\
Examples:

* `randomE:{Epic,Rare,Common}` - pick a random String
* `randomE:{112,1948,9684,132}` - pick a random number
* `randomE:{Text,14918,AnotherText,1515}` - the elements can be anything

### Random Long

Generate a random Long between a min (inclusive) and max (inclusive) value.\
Format: randomL:{\<min>,\<max>}\
Examples:

* `randomL:{0,12345678901234567}`
