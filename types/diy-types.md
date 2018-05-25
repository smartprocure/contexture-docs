# DIY Types

The Contexture ecosystem provides a defined list of types that can be
used to perform a wide variety of different searches. Our types are
focused on the different search interfaces that we provide, but our
API is designed to allow you to build any type you might need for any
other possible use case you might encounter.  We believe in making a
generic framework so you can be creative on your search solutions.
Because of that, we will start this chapter by explaining how to build
your own types.

## How to Wite a Type

Writing a type is as simple as writing a plain JavaScript Object with
one or more of the following properties:

| Property | Type | Params (Type) | Return Value Type | What it does |
| --- | --- | --- | --- | --- |
| `hasValue` | Function | Node (Object) | Boolean | Allows Contexture to know wether or not to process this search. |
| `filter` | Function | Node (Object) | Object | Returns a query with the applied input values, which will be sent later to the database provider. |
| `result` | Function | Node (Object), Search (Function) | Promise | Allows you to run a direct search for this type before Comtexture sends the full seaech with the whole tree. |

## Some examples

_Coming Soon..._
