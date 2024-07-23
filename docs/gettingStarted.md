# Getting Started

## Basic Types

Renelle supports the basic data types.

```
1 # integers
3.14 # floats
"hello" # strings
```

## Comments

As you can tell from the previous snippet, `#` is used for comments, and continues until the end of the line.

```
# this is a comment
```

## Arithmatic Operators

Renelle has many operators for working with the built in types.

```
1 + 1 # 2
1 * 3 # 3
5 - 3 # 2
5 / 2 # 2 integer division
5 / 2.0 # 2.5
5 ** 2 # 25
5 % 2 # 1
```

## Booleans

Renelle has booleans, and some operations for them. The conditional operations for renelle are short circuiting, and won't evaluate branches it know's don't matter.

```
true
false

1 == 1 # true
1 != 1 # false

true or false # never evaluates the right branch
false and true # never evaluates the right branch
```

## Atoms

Renelle has a data type known as atoms, where they represent their own value. So the value for the atom `:ok` is `:ok`. `:nil` is an atom that is used by functions that need to represent nothing.

```
:ok
:success
:nil
```

## Arrays and Tuples

Renelle has two basic collection types, arrays and tuples. They are both immutable, and used to represent groups of data. Arrays use [], and tuples use (). This is also a good time to bring up that commas are optional in renelle, and just treated as whitespace.

```
[1 2 3 4 5] # a five element array
(:ok "successful result") # a two item tuple to represent a result
```

Tuples will commonly be used in that format to represent success and failure. And both tuples and arrays have several builtin functions to make working with them easier.

```
head([1 2 3]) # 1
tail([1 2 3]) # [2 3]

fst((1, 2)) # 1
snd((1, 2)) # 2

len([1 2 3]) # 3
len((1, 2)) # 2
```

The operator for getting an item at an index from a tuple, or array is `@`, and it will return `:nil` if you try to get an item that doesn't exist.

```
[1 2 3] @ 1 # 2
(1 2) @ 0 # 1

[1 2 3] @ 5 # :nil
```
## Maps

Maps are the implementation of "objects" in renelle. They can be used as both, plain objects, like in javascript, and as dictionaries like in python. In this first example all the keys are actually atoms, but when they are you can use . notation to get the properties.

```
let cat = {
    name: "Hayley"
    age: 8
}

cat.name # returns "Hayley"
```

When using them like dictionaries, you can store any valid expression in the key, including, arrays, lambdas, and other maps. To get the non-atom values, you would use the `@` operator

```
let add = \x y => x + y
let sub = \x y => x - y

let ops = {
    add = "+"
    sub = "-"
}

ops@add # returns "+"
```

Maps can be updated using the `with` keyword, like so.

```
let cat = {
    name: "Hayley"
    age: 8
}

let cat2 = { cat with :name = "Toothless" }
```


## Assignment

Values are assigned with `let` and `equals`, and there is not a way to change a value. Although you can reassign to the same name.

```
let x = 5
let array = [1 2 3]
x = x + 1 # throws an error
let x = x + 1 # new binding to the name x
```

## Destructuring

You can also pattern match and destructure the left side by the right side to get to values. This works with any data type, and supports any nesting. You can also use `_` for spots you don't want a value to match.

```
let array = [1 2 3]
let [x y z] = array

let tuple = (1 2)
let (a _) = tuple
```

## Pipelines

Renelle has a pipeline operator `|>` which you can use to pass data and avoid function nesting. It always passes the expression on the left to the first argument of the function on the right.

```
[1 2 3]
|> push(4) # [1 2 3 4]
|> tail() # [2 3 4]
```

## Conditionals

If else are currently used for conditionals, and they are expressions, and do return a value.

```
let x = if true {
    "true value"
} else {
    "false value"
}
```

Cond allows you to test multiple conditions, and take the appropriate statement
```
cond {
    x < 10 => # branch
    x < 5  => # branch
    true   => # default case
}
```

Case allows you to pattern match against the shape of an argument.
```
let mock_response = (:ok, "success")

case mock_response {
    (:ok, result) => print(result)
    (:err, msg)   => print("Error: " + msg)
    _             => print("how did we get here?")
}
```

## Functions

Functions are declared with the `fn` keyword, and just like arrays and tuples, commas on the arguments are optional. Functions in renelle have an implicit return on their last value, but the `return` keyword is there for early returns.

```
fn add(x y) {
    x + y
}
```

Renelle also supports lambdas which are anonymous functions that can be assigned to values, passed around, and are easier to use in higher order functions. lambdas start with an `\`, then the arguments followed by a `=>` 

```
map(my_list, \ x => x + 1)
let complex_lambda = \ => {
    let x = 1
    let y = 2
    x + y
} 
```

!> `fn` is for declaring top level functions in a script or module, and should not be nested. If you need another call use a helper function, or if you absolutely need a local function, use a lambda.

## Scripting

To run a script you can simply run `rnl ./my_file.rnl` and renelle will evaluate the file, and will use a function called `main` as the entry point. If you simply call `rnl` with no commands you will enter the REPL, an interactive prompt, where you can type renelle code into the command line. use Ctrl+c to quit.

*my_file.rnl*
```
fn main() {
    print("hello world!")
}
```

## Modules

To run more than a single file you can use the cli tool to init a project, and call `rnl run` in the project to run it. Renelle expects all of your source code to be in the `src` directory, and that `src/main.rnl` is the entry point of your code. Specifically its `main` function.

You can create a new project with `rnl new project_name`

Module naming should follow the filesystem. with the exception, that the main file will just be named after your app.

*src/main.rnl*
```
module MyApp

fn main() {
    MyApp.Utils.Web.helper()
}
```

*src/utils/web.rnl*
```
module MyApp.Utils.Web

fn helper() {
    print("hello")
}
```

## Aliasing

!> WIP

If you want to avoid using the full name resolution for a module you are calling often, you can create an alias. The default alias will be the last part of the module.

```
alias MyApp.Utils.Web
alias MyApp.Utils.Web as Web # both of these lines are the same
```
