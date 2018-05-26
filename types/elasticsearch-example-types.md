[↩  Parent: README.md](../README.md)
[↩  Previous: DIY Types](diy-types.md)

# ElasticSearch Example Types

Contexture is designed to target any database you might need. However,
so far we have only inplemented database providers for the only
databases that we use: ElasticSearch and Mongo.

Most of our types have relevant components already written to
facilitate building search interfaces. As we progress over each one of
these types, we will show small examples of simple components written
to search with these types. We hope to provide enough information to
allow you to take as little as you need, or as much as you want, and
fulfill you expectations.

Our ElasticSearch types are the following ones:

## [bool](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/bool.js)

The bool type is intended to work as an ElasticSearch terms
aggregation with only one value for a single property. This is useful
for user interfaces with a checkbox to include or exclude a specific
field from a search (or a specific field-value pair).

Here's the definition of this type:

| Property Name | Type | Description |
| --- | --- | --- |
| field | String | Name of the field that we will include or exclude from the search. |

[Next  ⃕: Mongo Example Types](mongo-example-types.md)
