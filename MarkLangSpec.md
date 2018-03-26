# MarkLang Specification

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
Each *module* resides in a corresponding file, which, by convention should have the same name, but it is not mandatory.  
*Modules* are compact and independent units of code and can interact with each other.  
*Modules* cannot be nested and their names must be unique in a compilation unit.  
There are two kinds of *modules*:

* Main module
* Library module

### Main module

The *main module* contains the *main* declaration (actually it must contain it) and is the starting point of the compilation.  
In a compilation unit there should be just one *main module*, but it is not mandatory. As it may be useful to have many and switch between them according to needs.  
However just one *main module* will be taken into consideration, the others will be ignored. In fact in the compilation configuration file it is mandatory to specify the *main module* name, to avoid ambiguities.  
A *main module* does not expose its *def* declarations, as it must not be used by other *modules*.

### Library module

*Library modules* do not have a *main* declaration (mandatorily). They expose their *def* declarations, which can be used in other *modules*. There can be unlimited *library modules*.

### Module syntax

The *module* declaration must be the first declaration in a `mkl` file.  
The syntax for the *main module* is:

```
module [name];
```

The syntax for a *library module* is:

```
library module [name];
```

By convention *module* names should be lowercase or, if necessary, camelCase (lower).

## Inclusion

*Modules* are closed scopes for *def* declarations, therefore it is not possible to use implicitly a *def* from other *library modules* (from now on *libraries* for brevity).  
To do this it is necessary to introduce *using* declarations.  
A *using* declaration allows using a *def* defined in another module.  
  
The syntax for a *using* declaration is the following:

```
using [module].[def];
```

To avoid conflicts when using *defs* with the same name but defined in different *modules*, it is mandatory to use *aliases* with the following syntax:

```
using [module].[def] as [alias];
```

*Aliases* should always follow *def* naming conventions.  
  
To use all the *defs* defined in a specific *module*, it is possible to adopt the `*` shorthand:

```
using [module].*;
```

All *using* declarations must mandatorily appear after the *module* declaration and before the *main* and *def* declarations.

## Main

The *main* declaration is the starting point of the application.  
It must be in a *main module* (i.e. not in a *library module*) and must be unique.  
In a *main module* there must be one and only one *main* declaration.  
The syntax for a *main* declaration is the following:

```
main {
    [statements]
}
```

A *main* can only contain these kinds of *statements*:

- Components
- Links

## Def

*Def* is the basic block of a MarkDCS program.  
It has a name that uniquely identifies it in its *module*. By convention, it should be in CamelCase (upper).  
It is similar to a class in an object oriented language: it can be extended from other *defs* and it can be instantiated into a *component*.