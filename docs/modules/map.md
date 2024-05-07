# Map

## Summary

The `map` module has all of the standard library functions for working with maps. These will most all take a map as the first argument to facilitate pipelining.

## Functions

### length

#### length(map)

Returns the number of items in of `map`

#### example

```
let cat = {
    name: "Hayley"
    age: 8
}
Map.length(cat) # returns 2
```

---

### put

#### put(map, key, value)

Adds the `key` to the `map` with the provided `value`. This function returns a new value and does not mutate the previous value

#### example

```
let cat = { name: "Hayley" }
Map.put(cat :age 8) # { name: "Hayley", age: 8}
```