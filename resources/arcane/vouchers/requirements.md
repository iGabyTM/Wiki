# Requirements

## Types

* [Number operations](requirements.md#number-operations)

## Number operations

Compare two numbers using math operations

### Format <a href="#types-number_operations-format" id="types-number_operations-format"></a>

```yaml
type: operation # See below
left: number    # placeholder that returns a number
right: number   # placeholder that returns a number
```

### Equal (==) <a href="#number_operations-equal" id="number_operations-equal"></a>

Check if the numbers are equal

```yaml
type: '=='
left: 10
right: 15
# Result: false, 10 and 15 are not equal
```

### Greater (>) <a href="#number_operations-greater" id="number_operations-greater"></a>

Check if `left` is greater than `right`

```yaml
type: '>'
left: 10
right: 15
# Result: false, 10 is not greater than 15
```

### Greater or equal (>=) <a href="#number_operations-great_or_equal" id="number_operations-great_or_equal"></a>

Check if `left` is greater or equal to `right`

```yaml
type: '>='
left: 20
right: 15
# Result: true, 20 is greater or equal to 15
```

### Smaller (<) <a href="#number_operations-smaller" id="number_operations-smaller"></a>

Check if `left` is smaller than `right`

```yaml
type: '<'
left: 10
right: 15
# Result: true, 10 is smaller than 15
```

### Smaller or equal (<=) <a href="#number_operations-smaller_or_equal" id="number_operations-smaller_or_equal"></a>

Check if `left` is smaller or equal to `right`

```yaml
type: '<='
left: 20
right: 15
# Result: false, 20 is not greater or equal to 15
```
