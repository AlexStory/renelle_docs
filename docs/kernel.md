# Kernel

## Summary

The kernel module descrobes all of the built in functions in the default namespace. These are all implemented in the host language, and used to build other features.

## Functions

### fst

#### fst(tuple)

Returns the first item in a tuple.

#### example

```
let tuple = (1 2)
fst(tuple) # returns 1
```

### head

#### head(array)

Returns the first argument of an array, returns `:nil` for an empty array.

#### example

```
let array = [1 2 3 4]
head(array) # returns 1

head([]) # returns :nil
```

### last

#### last(array)

Returns the last element in an array, returns `:nil` for an empty array.

```
let array = [1 2 3 4]
last(array) # returns 4

last([]) # returns :nil
```

### len

#### len(argument)

Takes returns the length of the argument it is passed. It currently supports arrays, tuples, and maps.

#### example
```
let array = [1 2 3 4]
len(array) # returns 4
```

### os_args

!> This will most likely be moved to the os module once that is finished

Returns a list of strings of the arguments passed into the interpreter.

for example if the following was called with `rnl ./file.rnl "cat" "dog"`

```
let args = os_args()
args # returns ["cat" "dog"]
```

### push

#### push(array, item)

Returns a new array with `item` added to the end of `array`. Does not change the original array.

#### example
```
let array = [1 2 3]
let new_array = push(array 4)

array # [1 2 3]
new_array # [1 2 3 4]
```

### print

#### print(arg)

Prints the string representation of an argument to standard out.

#### example

```
print("hello") # "hello" printed to console
print(1) # 1 printed to console
```

### snd

#### snd(tuple)

Returns the second item in a tuple.

#### example

```
let tuple = (1 2)
snd(tuple) # returns 2
```

### tail

#### tail(array)

Returns a list of all but the first item in an array, returns `:nil` for an empty list.

#### example

```
let array = [1 2 3]
tail(array) # return [2 3]

tail([]) # returns :nil
```

### type

#### type(item)

Returns the builtin type of the item as a string.

#### example

```
type("hello") # returns "STRING"
type(1) # returns "INTEGER"
```