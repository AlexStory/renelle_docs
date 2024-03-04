# Array

## Summary

The `Array` module has all of the standard library functions for working with arrays. They will pretty much all take an array as their first argumet, to facilitate pipelining.

## Functions

### concat

#### concat(array1, array2)

Combines two arrays into a single array.

#### example

```
let a1 = [1 2]
let a2 = [3 4]
Array.concat(a1 a2) # returns [1 2 3 4]
```
---

### filter

#### filter(array, predicate)

Returns all the elements in the `array` where the `predicate` function returns true

#### example

```
let array = [1 2 3 4 5]
Array.filter(array, \x => x % 2 == 0) # returns [2 4]
```
 ---

### head

#### head(array)

Returns the first item in the `array`

#### example

```
let array = [1 2 3]
Array.head(array) # returns 1
```
---

### length

#### length(array)

Returns the length of a given `array`.

#### example

```
let array = [1 2 3]
Array.length(array) # returns 3
```
---

### map

#### map(array, f)

Applies the function `f` to every item in the `array`, and returns a new array with the resulting values.

#### example

```
let array = [1 2 3]
Array.map(array, \x => x + 1) # returns [2 3 4]
```
---

### quicksort

#### quicksort(array)

Recursively sorts the `array` using the quicksort algorithm.

#### examples

```
let array = [2 1 5 4 3]
Array.quicksort(array) # returns [1 2 3 4 5]
```
---

### quicksort_by

#### quicksort_by(array, f)

Recursively sorts the array, by the value of applying the function `f` to each argument

#### example

```
let cats = [{age: 4} {age: 7} {age: 2}]
Array.quicksort_by(cats, \x => x.age) # returns [{age: 2} {age: 4} {age: 7}]
```
---

### tail

#### tail(array)

Returns all items in the `array` except for the first one.

#### example

```
let array = [1 2 3]
tail(array) [2 3]
```