# DIY Types

The Contexture ecosystem provides a defined list of types that can be
used to perform a wide variety of different searches. Each type we
offer also has a respective component in our contexture-react repo, so
you can quickstart your search interfaces. However, even if our types are
focused on the different search interfaces that we provide, our
API is designed to allow you to build any type you might need for any
other possible use case you might encounter.  We believe in making a
generic framework so you can be creative on your search solutions.
Because of that, we will start this chapter by explaining how to build
your own types.

## How to Wite a Type

Writing a type is as simple as exposing any valid string property name
on the types object of a specific provider, then assigning a plain
JavaScript Object value with one or more of the following properties:

| Property | Type | Params (Type) | Return Value Type | What it does |
| --- | --- | --- | --- | --- |
| `hasValue` | Function | NodeSome Examples Object) | Boolean | Allows Contexture to know wether or not to process this search. |
| `filter` | Function | Node (Object) | Object | Returns a query with the applied input values, which will be sent later to the database provider. |
| `result` | Function | Node (Object), Search (Function) | Promise | Allows you to run a direct search for this type before Comtexture sends the full seaech with the whole tree. |

Once you have your type written, you can use it by sending it to an
existing [Contexture Provider](#TODO). It should look more or less
like:

```javascript
let myType = {
  hasValue: node => node.requiredProperty,
  filter: node => ({
    providerQueryObject: {
      value: node.requiredProperty
    }
  })
}

let provider = MyProvider({
  types: {
    myType
  }
})
```

## How to Write a UI Component for a Type

Writing a ussr interface for any type can be as simple as writing an
HTML or JSX Element that will render or write into any property of the
type, for example, using our custom type `myType`, we could write an
input field that, onChange, will write the field's value into the
`requiredProperty`. For example:

```javascript
let Component = node => (
  <input
    type="text"
    onChange={e => {
      node.requiredProperty = e.target.value
    }}
  />
)
```

- Managing State

## Shared Types

**Type names are not exclusive across providers**. You can define one
type called `myAwesomeType` in more than one provider and you'll be
able to keep the same required node properties, thus the same
`hasValue`. This allows us to provide the same API for several types,
and re-use code even if we switch the target database of the search.

## The Example Types

With the intention of providing practical examples of how to write
types, we decided to share some of the types we use in our production
applications. These types belong to two different database processors:
`contexture-elasticsearch` and `contexture-mongo`.

**Example Types aren't the rule**. These types are only provided to
serve as a guide to build any other type you might need for your
application. You can also **extend our example types**, simply by
assigning new types as properties on the objects exposed by
`contexture-elasticsearch` and `contexture-mongo`.
