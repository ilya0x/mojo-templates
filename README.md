# <img src="images/mojo-full-50.png" alt="Mojo">

Mojo is (designer to become) a superset language to Python that is specifically designed and optimized
for AI programming. It is fully interoperable with Python modules and libraries.

"Mojo gives Python superpowers." - Chris Lattner

-
-

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

<!--TODO: Table of Contents -->

<br>

### SDK

Currently there's only Ubuntu version of SDK (as of 9/18/2023)

<img src="images/sdk.png" width=800 alt="Mojo SDK"><br>
A view of the Mojo SDK

<br>

### Importing Python modules

Example:

``` python
from python import Python

def main():
    # This is equivalent to Python's `import numpy as np`
    let np = Python.import_module("numpy")

    # Now use numpy as if writing in Python
    array = np.array([1, 2, 3])
    print(array)

```

> Remember to import the Python module!<br>
> `$ sudo apt install python3-numpy`<br>
> Currently Mojo error messages do not notify user that the Python module you're
> trying to import is missing.

### Snippets for Matrix Multiplication

### Snippets for Strong Type Checking

### Snippets of fn functions

- with various argument type specifications preset:
- all local variables declared:
- raising exceptions explicitly declared with 'raises' function effect (placed
  after the function argument list):

### Custom Constructors

### Custom Destructors

### Custom Copy and Move Constructors

### @value decorator

print contents fn example:

```mojo
fn dump(self):
    print_no_newline("{")
        for i in range(self.size):
            if i > 0:
                print_no_newline(", ")
            print_no_newline(self.data.load(i))
    print("}")
```
