# Def

_Def_ is the basic block of a MarkDCS program.  
It has a name that uniquely identifies it in its _module_. By convention, it should be in UpperCamelCase.  
It is similar to a class in an object oriented language: it can be extended from other _defs_ and it can be instantiated into a _component_.

The most simple syntax for a _def_ declaration is the following:

```text
def [name];
```

The full syntax for a _def_ declaration is the following:

```text
[modifiers] def [name]([parameters]) : [super-def]([arguments]) {
    [statements]
}
```

A _def_ may have the following modifiers:

* _final_ : makes the _def_ not extensible, i.e. it cannot be used as _super-def_ for another _def_
* _base_ : makes the _def_ refer to an _element_ implemented in native code, either in the MarkDCS runtime or in a custom extension library. A _base def_ is also intrinsically _final_, thus the _final_ modifier is not needed.

The parameters of a _def_ are a comma-separated list of type-ID couples, with optional default value separated by "=", for example:

```text
def Logger(string format, string path = "stdout") 
```

A _def_ can extend another, inheriting its Inputs, Outputs, Components and Links. Arguments must be passed to the _super-def_ parameters, as a comma-separated list of expressions, in a similar way as for Components. For example:

```text
def ErrorLogger(string format) : Logger(format, "stderr")
```

Here `ErrorLogger` extends `Logger` \(defined above\) passing to it the value of the `format` parameter and the constant string `"stderr"`

A _base def_ may contain the following statements:

* Attributes
* Inputs
* Outputs

Example:

```text
base def Formatter(string format) {
	string format = format;
	variadic input in;
	output out;
}
```

A non-_base def_ may contain the following statements:

* Inputs
* Outputs
* Components
* Links

Example:

```text
def Logger(string format, string path = "stdout") {
	Formatter formatter(format);
	FileWriter fw(path, false);
	variadic input in;
	in -> formatter.in;
	formatter.out -> fw.in;
}
```

