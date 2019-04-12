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

