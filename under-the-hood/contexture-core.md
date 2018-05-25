# Contexture Core

The core of Contexture is a package of its own. Located at [github.com/smartprocure/contexture](https://github.com/smartprocure/contexture), it offers the very underlying function that is designed to process every one of the search queries. It begins with a simple curried function which, once the providers and the schemas are received, proceeds to process the [Contexture DSL](#TODO) by walking down the given search tree, cleaning up every node of possible inconsistencies, then mutating the tree with the directions given by the provider types and schemas, up until a valid search query is obtained. This query is delivered to the provider `runSearch` method, and the result is finally added back to the tree.

With this in mind, let's get some specifications.

## contexture's default export

Contexture's default export is a curried function with an initial arity of 1, which returns a function with an arity of 2. This separates the initialization from the search execution.

The first call of Contexture, with an arity 1, expects to receive a plain JavaScript Object with two expected keys:

- `providers`: It's expected to be an object where each key will have a [Contexture Provider](#TODO).
- `schemas`: It's expected to be an object where each key will have a [Contexture Schema](#TODO).

Example Declaration:

```javascript
Contexture({
  schemas: {
    ...mongoSchemas,
    ...elasticSearchSchemas,
  },
  providers: {
    mongo: require('contexture-mongo')({ /* provider configuration */ }),
    elasticsearch: require('contexture-elasticsearch')({ /* provider configuration */}),
  },
})
```

With that object sent, Contexture is officially initialized 🎉.The
resulting function will be able to be called multiple times to run
searches. This function expects the search tree ([Contexture DSL](#TODO)), and optionally an object that can have the following properties:

| Option | Description |
| ------ | ----------- |
| `debug`| Sends `_meta` as part of the response, which includes per node request records, relevant filters, and other debug info |
| `onResult` | A callback which is called whenever a node finishes producing it's results, which can be used to send partial results over websockets for example |

This second function will return a copy of the given search tree, filled with both properties needed to run the search, but also with the search results, which are assigned in the tree based on each one of the types that each specific search might be using. For more about how this happens, check out the [Contexture Types](#TODO)
