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

### reduce

#### reduce(array, acc, f)

Reduces over an array, applying the function `f` to the accumulator and the next item in the array.

#### example

```
let add = \x y => x + y
let numbers = [1 2 3]
let sum = Array.reduce(numbers, 0, add)
# returns 6
```

---

### reverse

#### reverse(array)

Returns a new array that is a reversed version of the original array

#### example

```
let array = [1 2 3]
let reversed = Array.reverse(array)
array # [1 2 3]
reversed # [3 2 1]
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
---

### zip

#### zip(array1, array2)

Returns a new array with the elements from `array1` and `array2` joined together in a tuple

#### example

```
let array_1 = [1 2 3]
let array_2 = ["a" "b" "c"]
Array.zip(array_1 array_2) # returns [(1 "a") (2 "b") (3 "c")]
```

---

### zip_with

#### zip_with(array1, array2, f)

Returns a new array with the function `f` applied to each set of arguments in an array. Returns early if either array runs out of elements.

#### example

```
let a = [1 2 3 4 5]
let b = [1 2 3]
let add = \x y => x + y
Array.zip_with(a b add) # returns [2 4 6]
```