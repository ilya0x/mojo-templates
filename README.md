# Mojo Notes

## import Python module

``` python
from PythonInterface import Python

# this is equivalent to Pyhon's 'import module_name as importedModule':

let importedModule = Python.import_module("module_name")

# now importedModule can be used like in Python.

```

## Snippets for Matrix Multiplication

## Snippets for Strong Type Checking

## Snippets of fn functions

- with various argument type specifications preset:
- all local variables declared:
- raising exceptions explicitly declared with 'raises' function effect (placed after the function argument list):

## Custom Constructors

## Custom Destructors

## Custom Copy and Move Constructors

## @value decorator

print contents fn example:

fn dump(self):
<br>
&nbsp;&nbsp;&nbsp;&nbsp;print_no_newline("{")
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for i in range(self.size):
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if i > 0:
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print_no_newline(", ")
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print_no_newline(self.data.load(i))
<br>
&nbsp;&nbsp;&nbsp;&nbsp;print("}")
