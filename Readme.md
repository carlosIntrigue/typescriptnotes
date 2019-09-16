# Typescript tutorial notes

## What and why

- Typescript is an open source programming language form Microsoft.
- Typescript is a typed superset of javascript
- It compiles down to plain javascript

- It features a superset of javascript.
- optional static typing and type inference
- IDE support with intelissense
- Rapid growing community.

## Variables and scopes

- Files in ts are trated as scripts in a global scope.
- To make files scoped modules, we need to add exports keyword.
- To compile a js file to ts we can use the `tsc filename.ts` or `tsc filename.ts --watch` to compile a file to plain js.
- For variable declarations typescript allows us to use the `let and const` keywords
- The difference between let and const is that let can be reassigned and do not need to have an initial value, whereas const has to have an initial value and is immutable thereafter.
- Typescript supports block level variable declaration unlike js and disallows re-declarations in the same scope.

## Types

- To add types to a variable the following syntax has to be followed `vardeclaration varname : vartype = assignmentifconst`
- `let loggedIn: boolean = true`
- `let total: number = 0`
- `let name: string = 'Hello'`
- The use of types is static type checking.
- Assignments will be stopped if types do not match.
- Unlike plain typescript, the compiler will stop static type errors.
- Accurate intelisense is an addition thanks to type declararions.
- The basic types are boolean, number, null, undefined.
- In Typescript null and undefined are subtypes of all types.
- `let loggedIn: boolean = null`
- `let total: number = undefined`

## Declaring arrays

- two ways:
- `let list1:number[] = [1,2,3]`
- `let list2:Array<number> = [1,2,3]`

## Declaring tuples

- Tuples are useful to declare a fixed number of values with various types.
- `let person: [string, number]= ['Chris', 11]`

## Declaring enums

- Enumns are types that give friendly names to numeric values.
- `enum Color {red, green, blue}`
- `let c: Color = Color.green`
- red is 0, green is 1, blue is 2
- `enum Color {red=5, green, blue}`
- `let c: Color = Color.green`
- red is 5, green is 6, blue is 7
- Enums are good ways to handle magic number code smell

## any Type

- The any type allows you to reassign different types of values.
- This is usefull for user input or 3rd party libraries.
- Useful for migratign from js to ts.
- `let randvar : any = 10`
- `randvar = true`
- `randvar = [true]`
- `randvar.toUppercase() // no error is raised`

## unknown Type

- Dynamic type that enables synamic assignment but disables any method calls
- `let randvar : unknown = 10`
- `randvar.toUppercase() // does not compile`

## Type assertion

- same as java. Allows you to coherce the compiler into accepting a type for a variable. This can be use d with unknown.
- `let randvar : unknown = 10`
- `(randvar as string).toUppercase() // compiles`
- intelissense also supports custom type guards. by declaring a typecheking functions for unknown types.

## Type inference

- `let a;// no inference`
- `a=20`
- `a=true`

- `let b=10;// inference`
- `b=true // error`

## Multi-type

- `let multitypevalue: number|boolean;`
- `multitypevalue = 20`
- `multitypevalue = true`
- We use multitype instead of any type because we restrict the possible types that can be assigned.
- Better intelissense support thatn any type.

## Functions

- types can be declared for parameters. `fnName(param1: type1, param2: type2, ...): returntype {}`
- The compiler has static type checking for parameters.
- Intelissense support.
- params can be optional.
- types can be declared for parameters. `fnName(param1: type1?, param2: type2?, ...): returntype {}`
- This will make all params optional
- params can be default.
- types can be declared for parameters. `fnName(param1: type1?, param2: number = 10, ...): returntype {}`
- param2 will be 10 when a value is not provided

## Interfaces

- Are a feature that enable to specify a type of data defined by its shape.
- an object shape as a type.
- Example with no interface
- `fnName(param1: {a:number, b:number}): returntype {}`
- param 1 is an object of that shape specified in the params scope
- We can extract this into an interface.
- `interface A{a:number, b:number}`
- `fnName(param1: A): returntype {}`
- Easier to maintain.
- properties can be optional.
