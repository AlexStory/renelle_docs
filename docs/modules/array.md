# Array

## Summary

The `Array` module has all of the standard library functions for working with arrays. They will pretty much all take an array as their first argumet, to facilitate pipelining.

## Functions

### all?

#### all?(array, predicate)

Returns true if all member of the `array` return true for the `predicate`.

#### example

```
let a = [2 4 6]
Array.all?(a, \x => x % 2 == 0) # true
```

---

### any?

#### any?(array, predicate)

Returns true if any element of the `array` returns true for the `predicate`, otherwise returns false.

#### example

```
let a = [1 2 3]
Array.any?(a, \x => x % 2 == 0) # true
```
---

### average

#### average(array)

Returns the average of all items in the `array`

#### example

```
let a = [1 2]
Array.average(a) # 1.5
```

---

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

### contains?

#### contains?(array, element)

Returns true if the given `element` is present in the `array`, otherwise returns false.

#### example

```
let a = [1 2 3]
Array.contains(a, 2) # true
```

---

### empty?

#### empty?(array)

Returns whether the given array is empty.

#### example

```
let nums = [1 2 3]
Array.empty?(nums) # false
Array.empty?([]) # true
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

### find

#### find(array, predicate)

Returns the first element in the given `array` for which `predicate` returns true, otherwise returns`:nil`. If using an array which you suspect could have `:nil` as a value, use `try_find` instead.


#### example

```
let a = [1 2 3]
Array.find(a \x => x % 2 == 0) # returns 2
```

---

### find_index

#### find_index(array, predicate)

Returns the index of the first element in the given `array` for which the `predicate` returns true, otherwise returns `:nil`.


#### example 
```
let a = [1 2 3]
Array.find_index(a, \x => x % 2 == 0) # returns 1
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

### iter

#### iter(array, f)

Runs the function `f` for each element in the `array`

#### example

```
let a = [1 2 3]
Array.iter(a, print) # prints each item to the std out
```
---

### join

#### join(array, separator)

Joins all strings in an array, with separator between items.

#### example

```
let array = ["a" "b" "c"]
Array.join(array ", ")
# returns "a, b, c"
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

### max

#### max(array)

Returns the largest item in the `array`.

#### example

```
let a = [1 3 2]
Array.max(a) # 3
```

---

### max_by

#### max_by(array, f)

Returns the largest item in the `array` when applying the function `f`.

#### example

```
let a = ["apple" "pear" "banana"]
Array.max_by(a, len) # "banana"
```

---

### min

#### min(array)

Returns the smallest item in the array.

#### example

```
let a = [3 1 2]
Array.min(a) # 1
```

---

### min_by

#### min_by(array, f)

Returns the smallest item in the `array` when applying the function `f`.

#### example

```
let a = ["apple" "pear" "banana"]
Array.min_by(a, len) # "pear"
```

---

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

### range

#### range(start, stop)

Returns an array of all numbers from `start` to `stop`. If only one argument is passed in it returns an array from 0 to `stop`.

#### example

```
Array.range(5) # [0 1 2 3 4]
```

---

### reduce

#### reduce(array, acc, f)

Reduces over an array, applying the function `f` to the accumulator and the next item in the array. Reduce is a special function, and can also be called with only 2 arguments, the array and the function, in which case it will use the first element of the array as the initial accumulator.

#### example

```
let add = \x y => x + y
let numbers = [1 2 3]
let sum = Array.reduce(numbers, 0, add)
# returns 6
```

---

### reduce_while

#### reduce_while(array, acc, f) 

Reduces over an array, applying the functon `f` to the accumulator and the next item in the array. Expects each iteration of `f` to return either `(:cont, acc)` or `(:halt, acc)` with `acc` being the new accumulator. If it hits `(:halt, acc)` it will return the value, otherwise it continues to the end of the array. `reduce_while` is a special function and can be called with either 2 or 3 arguments, and if called with only 2, the first item of the array will be supplied as the initial accumulator.

#### example

```
fn is_even(_, x) {
    if x % 2 == 0 {
        (:halt true)
    } else {
        (:cont false)
    }
}

fn any_even(array) {
    Array.reduce_while(array, false, is_even)
}
```

---

### replace_at

#### replace_at(array, index, elem)

Replaces the item at the given `index` in the `array` with the new  `elem`

#### example

```
let a = [1 2 3]
Array.replace_at(a, 1, 0) # returns [1 0 3]
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

### sum

#### sum(array)

Sums all items in an array

#### example

```
let array = [1 2 3]
Array.sum(array)
# returns 6
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

### try_find


#### try_find(array, predicate)

Returns `(:some, result)` if an element is found in the `array` that matches `predicate` otherwise returns `:none`

#### example

```
let a = [1 2 3]
Array.try_find(a \x => x % 2 == 0) # (:some 2)
Array.try_find(a \x => x > 4) # :none
```

---

### with_index

#### with_index(array)

Returns a new array as the pairing of each item with its index.

#### example

```
let a = ["a" "b" "c"]
Array.with_index(a) # returns [(0 "a") (1 "b") (2 "c")]
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