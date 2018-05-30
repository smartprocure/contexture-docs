[↩  Parent: Table of Contents](../README.md)  
[↩  Previous: Connecting to Elasticsearch & MongoDB](connecting.md)

## Connecting to Other Databases

Contexture depends on it's providers to be able to know how to
translate from the Contexture DSL to the specific DSL that each
database needs. Because of this, to other databases you will need to
create a new Provider.

Writing a new provider consists of writing a function (, or class or
anything other approach you might like,) that returns the following
properties:

| Property Name  | Type       | Example Value  | Description |
| ---            | ---        | ---            | ---         |
| `types`        | Object | See the example-types in [contexture-elasticsearch](https://github.com/smartprocure/contexture-elasticsearch) and [contexture-mongo](https://github.com/smartprocure/contexture-mongo) | This will contain the [Contexture Types](../types/diy-types.md) for your custom Provider |

[↪ Next: Simple Search Box](simple-search-box.md)
