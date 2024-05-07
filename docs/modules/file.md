# File

## Summary

The `File` module contains methods for reading, writing, and manipulating files.

## Functions

### open

#### open(path)

Reads the file at the given `path` and returns a tuple, with `(:ok value)` on success, and `(:error reason)` on failure. value, and reason are both strings.

#### example

```
let (res, text) = File.open("cat.txt")
if res == :ok {
    print(text) # prints "meow"
}
```

---

### open!

#### open!(path)

Reads the file at the given `path` and returns the value as a string. This function will throw an error if it encounters any problem reading the file.

#### example

```
let txt = File.open!("cat.txt")
print(txt)
# "meow"
```

---

### write

#### write(content, path)

Writes the given string content to the path. Returns `(:ok, :nil)` on a success, and `(:error, reason)` on a failure, with reason being a string.

#### example
```
let content = "meow"
let (success, message) = File.write(content, "cat.txt")
```

---

### write!

#### write!(content, path)

Writes the given text `content` to the `path` given. This function will throw an error if it encounters any problem reading the file.

#### example(content, path)

```
let text = "meow"
File.write!(text, "cat.txt") # writes "meow" to disk at cat.txt
```