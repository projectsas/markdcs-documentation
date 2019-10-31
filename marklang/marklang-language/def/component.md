# Component

Component is one of the statements allowed inside a non-_basic_ _def_. It represents an instantiation of another _def_ called its _type._ At least one __Component is required.  
It has a name that uniquely identifies it in its _def_ and _super-def_ \(if any\). By convention, it should be in lowerCamelCase.

The most simple syntax for a Component declaration is the following:

```text
[name] [type];
```

where _type_ is a _def_ name, which must refer to a different _def_ that must not contain any Component referring, even indirectly, to the current _def_.

The full syntax for a Component declaration is the following:

```text
[name] [type]([arguments]);
```

_arguments_ are a comma-separated list of expressions, each yielding a value of type compatible with the corresponding parameter in the _def_ referred to by _type_.

