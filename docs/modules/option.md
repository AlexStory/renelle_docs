# Option

## Summary

The `Option` module has all of the standard library functions for working with options. Almost all of them will take in an option as the first parameter. As a note. Option is not its own type in renelle, it's only a convention of a value being in either the tuple `(:some, value)` or `:none`.

## Functions

### default

#### default(option, value)

Returns the `option`'s value for the some path, or the provide `value` for the none path.

#### example

```
Option.default((:some 2), 6) # 2
Option.default(:none, 6) # 6
```

---

### is_option?

#### is_option(optional)

Returns true if the value provided is an option, otherwise returns false.

#### example

```
Option.is_option?(3) # false
Option.is_option?((:some, 3)) # true
```

---

### map

#### map(option, f)

Applies the given function `f` to the `option` if it is a some value, otherwise returns `:none`

#### example

```
let o = (:some 3)
Option.map(o \x => x * 2) # 4
Option.map(:none \x => x * 2) # none
```

---

### some

#### some(value)

Wraps a `value` in a some option.

#### example

```
Option.some(2) # (:some 2)
```

---

### some?

#### some?(option)

Returns true if an `option` is some, otherwise returns fales.

#### example

```
Option.some?(:none) # false
Option.some?((:some 2)) # true
```

---