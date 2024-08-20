# String

## Summary

Contains several operations for working on or with strings.

## Functions

### concat

#### concat(str1, str2)

Concatenates two strings together.

#### example

```
let s1 = "hello"
let s2 = "world"
String.concat(s1, s2) # "helloworld"
```

---

### contains?

#### contains?(str, substr)

Returns true if the given string `str` contains the substring `substr`

#### example

```
string = "I like dogs"
String.contains?(string, "og") # true
```

---

### ends_with?

#### ends_with?(string, substr)

Returns true if the given `string` ends with the substring `substr`

#### example

```
let website = "www.example.com"
String.ends_with?(website, ".com") # true
```

---

### index_of

#### index_of(string, substr)

Returns the index of the firs instance of the substring `substr` in the given `string`, returns -1 if it isn't found.

#### example

```
let string = "I like dogs"
String.index_of(string, "dog") # 7
String.index_of(string, "cat") # -1
```

---

### length

#### length(string)

Returns the length of the given `string`

```
String.length("hello") # 5
```

---

### lower

#### lower(string)

Returns the given `string` in lowercase

#### example

```
String.lower("Hello") # "hello"
```

---

### match? 

#### match?(string, regex)

Returns wether the given `regex` matches for the given `string`

### example

```
let og_word = "[b|c|d]og"
String.match?("dog", og_word) # true
```

---

### pad_left

#### pad_left(string, length, character)

Ensures that the given `string` meets the minimum `length` by padding it to the left with the `character` given, or " " if none is supplied.

#### example

```
String.pad_left("dog", 5, "x") # "xxdog"
String.pad_left("cat", 5) # "  cat"
```

---
### pad_right

#### pad_right(string, length, character)

Ensures that the given `string` meets the minimum `length` by padding it to the right with the `character` given, or " " if none is supplied.

#### example

```
String.pad_right("dog", 5, "x") # "dogxx"
String.pad_right("cat", 5) # "cat  "
```

---

### replace

#### replace(string, old, new)

Replaces the first instance of the substring `old` with `new` in the given `string`

#### example

```
let string = "I love dogs"
String.replace(string, "dogs", "cats") # "I love cats"
```

---

### replace_all

#### replace_all(string, old, new)

Replaces all instance of the substring `old` with `new` in the given `string`

#### example

```
let string = "I like go because go is fun"
String.replace_all(string, "go", "rnl") # "I like rnl because rnl is fun"
```

---

### split

#### split(string, substr)

Splits a given `string` into an array by the given substring `substr`. If a substring isn't suppliend it seperates each character.

#### example

```
String.split("hello") # ["h" "e" "l" "l" "o"]
String.split("csv,json,xml", ",") # ["csv" "json" "xml"]
```

---

### starts_with?

#### starts_with?(string, substr)

Returns true if the `string` starts with the substring `substr`

#### example

```
let string = "hello world"
String.starts_with?(string, "hello") # true
```

---

### trim

#### trim(string)

Trims all whitespace characters from the start and end of the given `string`.

#### example

```
let string = "   hello\r\n"
String.trim(string) # "hello"
```

---

### trim_end

#### trim_end(string)

Trims all whitespace characters from the end of the given `string`.

#### example

```
let string = "   hello\r\n"
String.trim_end(string) # "   hello"
```

---

### trim_start

#### trim_start(string)

Trims all whitespace characters from the start of the given `string`.

#### example

```
let string = "   hello\r\n"
String.trim_start(string) # "hello\r\n"
```

---

### upper

#### upper(string)

Returns the given `string` in uppercase.

#### example

```
String.upper("Hello") # "HELLO"
```