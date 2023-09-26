# <img src="images/mojo-full-50.png" alt="Mojo">

Mojo is (designed to become) a superset language to Python that is specifically designed and optimized
for AI programming. It is fully interoperable with Python modules and libraries.

"Mojo gives Python superpowers." - Chris Lattner

<br>

## <img src="./images/template-20.png" alt="template"> Templates

<br>

## <img src="./images/vscode-20.png" alt="Flask"> Visual Studio Code Extensions

[Mojo <img src="images/mojo-15.png" alt="Mojo">](
    https://marketplace.visualstudio.com/items?itemName=modular-mojotools.vscode-mojo)
    - extension from the Modular team adds support for the [Mojo programming
    language](https://www.modular.com/mojo).

[Mojo-lang](https://marketplace.visualstudio.com/items?itemName=CristianAdamo.mojo) - A basic
syntax highlighter for Mojo Language.

<br>

## 📝Notes

> These notes are updated on regular basis

<!--
TODO: Table of Contents

TODO: Snippets for Matrix Multiplication

TODO: Snippets for Strong Type Checking

TODO: Snippets of fn functions
- with various argument type specifications preset:
- all local variables declared:
- raising exceptions explicitly declared with 'raises' function effect (placed
  after the function argument list):

TODO: Custom Constructors

TODO: Custom Destructors

TODO: Custom Copy and Move Constructors
-->
<br>

### SDK

Currently there's only Ubuntu version of SDK (as of 9/18/2023)

<img src="images/sdk.png" width=800 alt="Mojo SDK"><br>
A view of the Mojo SDK

<br>

### Variables

available variable declarations:

`let` - declares a variable a constant, immutable (can not be changed)

`var` - declares a variable that can be changed

`alias` - immutable, stores the variable at compile time (usually used to store libraries)

<br>

### `main()` function

Mojo (currently) requires a `main()` function to run your code (expressions are
not yet supported on file scope level):

``` mojo
fn main():
    print("Hello World")
```

- Mojo will run `main` function by default.

<br>

### Use of `fn` vs `def`

#### `fn`

- Explicit, strict: requires type annotations for every function argument and variable
- Speeds up the process when the types are declared
- The functions can be in any order

``` mojo
fn addNumbers(a: Int, b: Int) -> Int: # Int defaults to Int64 when bits are not declared
    let c: Int = a + b
    return c

fn main():
    let x: Int = addNumbers(2, 5)
    print (x) # prints 7
```

#### `def`

- Implicit, so will take more time for system to figure out the types

``` mojo
def addNumbers(a, b):
    c = a + b
    return c
```

<br>

### Data Types

Available data types:

`string` - a string of characters - words, numbers, special characters, emoji

`int` - integers, whole numbers.

```mojo
fn main():
    let x: Int8 = 42
  
    # the 8 after Int means it occupies 8 bits of memory
    # 2^8 = 256 : can store 256 different numbers, 0 through 255
    # there is Int8, Int16, Int32 and Int64
```

`uint` - unsigned integers - cannot have a sign so means just positive whole numbers.

``` mojo
fn main():
    let x: UInt8 = 42
  
    # requires memory allocation
    # there is Int8, Int16, Int32 and Int64
```

`Float` - any decimal number

``` mojo

fn main():
    let x: Float16 = 3.14
  
    # requires memory allocation
    # there is Float16, Float32 and Float64
```

`Bool` - Boolean value: can only be `True` or `False`

<br>

### `if` `elif` `else` statements

If a condition is met then you execute some code and if it is not met then you default to other code:

- can have multiple `elif` but only one `if` and `else`

``` mojo
fn main():
    let x: Int16 = 100
    # changing the value of x from 100 to 1 will trigger the elif
    # and changing it to anything else will default to "else"

    if x == 100:
        print("x is 100")
  
    elif x == 1:
        print("x is 1")

    else:
        print("x is not 100")
```

<br>

### Loops

`for` - will execute a set number of iterations until an end goal is met

``` mojo
fn main():
    for i in range(10): # i is number of iterations
        print (i) # prints 0 to 9 
```

`white` - will go on forever until a goal is met

``` mojo
fn main():
    var x Int8 = 0 # declares x as an integer variable
    while x < 10:
        x += 1 # adds 1 to x and assigns result to x
        print (x) # prints 1 to 10
```

or

``` mojo
fn main():
    var x Int8 = 0 # declares x as an integer variable
    while True:
        x += 1 # adds 1 to x and assigns result to x
        print (x) # prints 1 to 10
        if x >= 10:
            break # stops the loop
```

<br>

### Importing Python modules

Example:

``` mojo
from python import Python # imports Python

fn main() raises: # raises means the function itself can raise errors
    let np = Python.import_module("numpy") # This is equivalent to Python's `import numpy as np`

    # Now use numpy as if writing in Python
    array = np.array([1, 2, 3])
    print(array)

```

> Remember to import the Python module!<br>
> `$ sudo apt install python3-numpy`<br>
> Currently Mojo error messages do not notify user that the Python module you're
> trying to import is missing.

<br>

### More about `raises`

- error handling is done with:

`raises` - any function that can raise an error has to be explicitly labeled with this label

`try` - attempts to run some code

`except` - catches the error and announces it

`finally` - the function will still follow through with the code within `finally`

``` mojo
fn main() raises:
    try:
        # attempt to run some code here, like open a file
        print("opening file")
    except:
        # we get an error, like "bad encoding"
        raise Error("bad encoding")
    finally:
        # ensure the file is closed to prevent resource leaks
        print("file closed")
    # if we try to close the file outside of the finally block,
    # error will terminate the program before this is run and get you'll get a leak
    print("try to close the file...')
```

<br>

### Getting User Input

This is not implemented natively in Mojo yet, so we have to import the
"builtins" Python module to use Python's `input()` function:

``` mojo
from python import Python

fn main() raises:
    let py = Python.import_module("builtins") # allows the use of Python's "builtins" module

    let user_input = py.input("What is your name?") # using Python's input function to get user input

    print("Hello, ", user_input, "!")
```

<br>

### Arrays

Arrays are not natively supported in Mojo, so Python has to be used:

To print to one element in the array:

``` mojo
from python import PythonObject

fn main() raises:
    let x: PythonObject = [2, 4, 6, 8, 10]

    print(x[3]) # will print 8 (array element ids start with 0)
```

To print all elements in the array:

``` mojo
from python import PythonObject

fn main() raises:
    let x: PythonObject = [2, 4, 6, 8, 10]

    for i in range(x.__len__()):
        print(x[i]) # will print all the elements of the array, one per line
```

<br>

### Function Arguments

`Inout` - marks the argument as mutable/changeable. Changes made INside the
function are visible OUTside the function.

`borrowed` - marks the argument explicitly immutable.

`owned` - marks the variables as belonging to the function, even if they were
declared with a `let` in another function

`with` - 

<br>

### Variable Scope

- Global scope variables are accessible inside all functions
- Local scope variables are only accessible within the function they are declared.

``` mojo
let x = 6 # global / file scope

fn main():
    let y = 8 # local scope
    # has access to x
    # does NOT have access to z
fn Function():
    let z = 9 # local scope
    # has access to x
    # does NOT have access to y
```

<br>

### Objects

- use `struct` to create an object in Mojo (equivalent to `class` in Python)

``` mojo
struct Banana:

    # Define your variables, including their data types:
    var Ripe: Bool
    var Length: Float32
    var Color: String

    # Initializing Method:
    # set arguments and their data types:
    fn __init__(inout self, Ripe: Bool, Length: Float32, Color: String): 
        # Initializing variables with passed arguments
        self.Ripe = Ripe # declare 
        self.Length = Length
        self.Color = Color
    
    # pass in the object and declare the output type:
    fn ripe(self, rhs: Banana) -> Bool: # rhs stands for "right hand side" (can be any name)
        return self.Ripe

    fn length(self, rhs: Banana) -> Float32:
        return self.Length
    
    fn color(self, rhs: Banana) -> String:
        return self.Color

fn main():
    var my_banana = Banana(False, 4.7, "yellow")
    print(my_banana.ripe(my_banana))
```

<br>

### "Arguments" vs "Parameters"

In Python "arguments" and "parameters" are fairly interchangeable for "things
that are passed into functions." In Mojo they are different:

- "Parameters"
  - use square braces: `[...]`
  - are only compile-time values or types
- "Arguments" and "expressions"
  - use parentheses, like in Python: `(...)`
  - are runtime or compile-time values

Examples:

<br>

### @value decorator

You can think of `@value` as an extension of Python’s `@dataclass` that also handles
Mojo’s `__moveinit__` and `__copyinit__` methods.

Example:

<br>

### Mojo CLI



<br>

## Bringing in Python into Mojo

There are several things that need to be changed in Python code to be able to
run it as Mojo code:
