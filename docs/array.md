# Array

## Summary

The `Array` module has all of the standard library functions for working with arrays. They will pretty much all take an array as their first argumet, to facilitate pipelining.

## Functions

### length

#### length(array)

Returns the length of a given `array`.

#### example

```
let array = [1 2 3]
Array.length(array) # returns 3
```

### map

#### map(array, f)

Applies the function `f` to every item in the `array`, and returns a new array with the resulting values.

#### example

```
let array = [1 2 3]
Array.map(array, \x => x + 1) # returns [2 3 4]
```