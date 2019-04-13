# Modules

MarkLang is a modular programming language.  
Each _module_ resides in a corresponding file, which, by convention should have the same name, but it is not mandatory.  
_Modules_ are compact and independent units of code and can interact with each other.  
_Modules_ cannot be nested and their names must be unique in a compilation unit.  
There are two kinds of _modules_:

* Main module
* Library module

## Main module

The _main module_ contains the _main_ declaration \(actually it must contain it\) and is the starting point of the compilation.  
In a compilation unit there may be just one _main module_, but it is not mandatory. However just one _main module_ will be taken into consideration, the others will be ignored. In fact in the compilation configuration file it is mandatory to specify the _main module_ name, to avoid ambiguities.  
A _main module_ does not expose its _def_ declarations, as it must not be used by other _modules_.

## Library module

_Library modules_ do not have a _main_ declaration \(mandatorily\). They expose their _def_ declarations, which can be used in other _modules_. There can be unlimited _library modules_.

## Module syntax

The _module_ declaration must be the first declaration in a `mkl` file.  
The syntax for the _main module_ is:

```text
module [name];
```

The syntax for a _library module_ is:

```text
library module [name];
```

By convention _module_ names should be lowercase or, if necessary, lowerCamelCase.

## Inclusion

_Modules_ are closed scopes for _def_ declarations, therefore it is not possible to use implicitly a _def_ from other _library modules_ \(from now on _libraries_ for brevity\).  
To do this it is necessary to introduce _using_ declarations.  
A _using_ declaration allows using a _def_ defined in another module.

The syntax for a _using_ declaration is the following:

```text
using [module].[def];
```

To avoid conflicts when using _defs_ with the same name but defined in different _modules_, it is mandatory to use _aliases_ with the following syntax:

```text
using [module].[def] as [alias];
```

_Aliases_ should always follow _def_ naming conventions.

All _using_ declarations must mandatorily appear after the _module_ declaration and before the _main_ and _def_ declarations.

