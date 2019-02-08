# MarkLang Specification {#main}

MarkLang is a very strict language, thus it is very important to know the rules.

## Files

The standard and only MarkLang file extension is  `.mkl`  
The standard structure of a MarkLang file is:

```
[module declaration]

[using declarations]

[main declaration (only in main modules)]

[def declarations]
```

## Modularity

MarkLang is a modular programming language.  
Each _module_ resides in a corresponding file, which, by convention should have the same name, but it is not mandatory.  
_Modules_ are compact and independent units of code and can interact with each other.  
_Modules_ cannot be nested and their names must be unique in a compilation unit.  
There are two kinds of _modules_:

* Main module
* Library module

### Main module

The _main module_ contains the _main_ declaration \(actually it must contain it\) and is the starting point of the compilation.  
In a compilation unit there should be just one _main module_, but it is not mandatory. As it may be useful to have many and switch between them according to needs.  
However just one _main module_ will be taken into consideration, the others will be ignored. In fact in the compilation configuration file it is mandatory to specify the _main module_ name, to avoid ambiguities.  
A _main module_ does not expose its _def_ declarations, as it must not be used by other _modules_.

### Library module

_Library modules_ do not have a _main_ declaration \(mandatorily\). They expose their _def_ declarations, which can be used in other _modules_. There can be unlimited _library modules_.

### Module syntax

The _module_ declaration must be the first declaration in a `mkl` file.  
The syntax for the _main module_ is:

```
module [name];
```

The syntax for a _library module_ is:

```
library module [name];
```

By convention _module_ names should be lowercase or, if necessary, camelCase \(lower\).

## Inclusion

_Modules_ are closed scopes for _def_ declarations, therefore it is not possible to use implicitly a _def_ from other _library modules_ \(from now on _libraries_ for brevity\).  
To do this it is necessary to introduce _using_ declarations.  
A _using_ declaration allows using a _def_ defined in another module.

The syntax for a _using_ declaration is the following:

```
using [module].[def];
```

To avoid conflicts when using _defs_ with the same name but defined in different _modules_, it is mandatory to use _aliases_ with the following syntax:

```
using [module].[def] as [alias];
```

_Aliases_ should always follow _def_ naming conventions.

All _using_ declarations must mandatorily appear after the _module_ declaration and before the _main_ and _def_ declarations.

## Main

The _main_ declaration is the starting point of the application.  
It must be in a _main module_ \(i.e. not in a _library module_\) and must be unique.  
In a _main module_ there must be one and only one _main_ declaration.  
The syntax for a _main_ declaration is the following:

```
main {
    [statements]
}
```

A _main_ can only contain these kinds of _statements_:

* Components
* Links

## Def

_Def_ is the basic block of a MarkDCS program.  
It has a name that uniquely identifies it in its _module_. By convention, it should be in CamelCase \(upper\).  
It is similar to a class in an object oriented language: it can be extended from other _defs_ and it can be instantiated into a _component_.

