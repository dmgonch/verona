# Parser Notes

* allow `using` inside a function
* put precedence paren forcing back in
* special type: Self
* inheritance
* try/catch
* update sugar
  should we instead have Ref[T] or Ref[T, U]?
* distinguishing value parameters from type parameters
* constant expressions
* yield transformation
  https://csharpindepth.com/Articles/IteratorBlockImplementation
* trim indented strings

## Open Questions

* lambdas and object literals: are they ever block expressions?
* transform an object literal into an anonymous class and a create call
  needs free variable analysis
  could do the same thing for lambdas
  might not want to do either as they have type checking implications
* `where` might need to have non-type constraints
* do we need default capabilities for types
* short-circuiting
  lazy type, or lambdas

## Public/Private

* Public access only if the imported module path is not a prefix of the current module path (private access from submodules).
* Perhaps also allow private access if the current module path is a prefix of the imported module path (private access to submodules).
* do we want to be able to have private functions with symbol names?

## Anonymous Types

* anonymous interface types
* allow class/interface definition where a type is expected
  and also where an expr is expected?
* `'type' tuple` where a type is expected
  meaning the type of the expression
* `'interface' tupletype` where a type is expected
  meaning extract an interface from the type

## Autogenerate Create

create(): Self & iso
{
  // This will only type-check if all fields have default values
  // But how do default values work with other calls to new?
  new ()
}

## Overload Resolution

https://en.cppreference.com/w/cpp/language/overload_resolution
https://en.cppreference.com/w/cpp/language/constraints

find all candidate functions
  functions in scope
  functions on the receiver
  must have the same name
  must have a compatible arity, accounting for default parameter values

## Standard Library

env doesn't need stdin, stdout, stderr
  can use a capability to get access to them
use a capability to set the global exit code
use a capability to fetch args
use a capability to read and write envvars
main() gets ambient authority and nothing else

> instead of ref and tuple having oftype, put it on expr
