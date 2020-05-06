# Inputs and Outputs

Input and Output statements are allowed inside any _def_. They represent the connection points of instantiations of this _def_ as components of another _def._ Each of them has a name that uniquely identifies it in its _def_ and _super-def_ \(if any\). By convention, it should be in lowerCamelCase.

Inputs and Outputs are declared as follows:

```text
[modifiers] input [name];
[modifiers] output [name];
```

_input_ modifiers may be one of the following:

* _variadic_: the _input_ defined actually represents an array of inputs. Each input is referred to in links with a non-negative integer subscript between square brackets.
* _unordered variadic_: same as _variadic_ when the index in the input array does not matter and is automatically assigned. Each input is referred to in links with empty square brackets.

The only _output_ modifier allowed is _variadic_, with the same meaning as above.

