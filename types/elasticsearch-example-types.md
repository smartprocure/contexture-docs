[↩  Parent: Table of Contents](../README.md)  
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

## Bool Type

The bool type is intended to work as an ElasticSearch terms
aggregation with only one value for a single property. This is useful
for user interfaces with a checkbox to include or exclude a specific
field from a search (or a specific field-value pair).

Here is the list of all properties this type uses:

| Property Name | Type | Description |
| --- | --- | --- |
| field | String | Name of the field that we will be using to filter the search search. |
| value | String | Value of the field that will be used to filter the search. |

Example input:

```javascript
{
  type: 'bool',
  field: 'fieldName',
  value: true
}
```

Example output:

```javascript
{
  term: {
    fieldName: true
  }
}
```

You can read more about it in:

- [Source code of the type: bool](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/bool.js).
- [Unit tests of the type: bool](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/bool.js).
- Elastic Search [Term Query](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-term-query.html).

## Cardinality Type

The Cardinality type serves to calculate an approximate count of the
distinct available values. This type only uses one property, `field`.

Example input:
```javascript
{
  key: 'fieldName',
  type: 'cardinality',
  field: 'Organization.Name.untouched'
}
```

Example output:
```javascript
{
  aggs: {
    cardinality: {
      cardinality: {
        field: 'Organization.Name.untouched'
      }
    }
  }
}
```

- [Source code of the type: cardinality](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/cardinality.js).
- [Unit tests of the type: cardinality](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/cardinality.js).
- Elastic Search [Cardinality Aggregation](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-metrics-cardinality-aggregation.html).

## Date Type

The Date type is used to specify a range of dates that will be used to
filter the available results. This range of dates can be specified by
a string formatted date (`YYYY-MM-DD`) or by a small set of possible
humanly readable date ranges. Details follow:

| Property Name | Type | Description |
| --- | --- | --- |
| `from` | String | Either a date formatted as `YYYY-MM-DD`, or an ES date (formatted properly for ElasticSearch), or one of the following values: `thisQuarter` (for the current quarter of the year), `lastQuarter` (for the previously completed quarter of the year), `nextQuarter` (for the upcoming quarter). |
| `to` | String | Optional. Defaults to the current date. Only concidered if there's a `from` value, should be a date formatted as `YYYY-MM-DD` or an ES date (formatted properly for ElasticSearch). |
| `useDateMath` | Boolean | Defines if we should parse `from` as one of the `*Quarter` dates. |
| `isDateTime` | Boolean | Ignores any processing or formatting and accpets the `form` and `to` values as they come. |

Example input 1:
```javascript
{
  type: 'date',
  field: 'fieldName',
  from: '2016-04-25'
}
```

Example output 1:
```javascript
{
  range: {
    fieldName: {
      gte: '2016-04-25',
      format: 'dateOptionalTime'
    }
  }
}
```

Example input 2:
```javascript
{
  type: 'date',
  field: 'test',
  from: 'thisQuarter',
  useDateMath: true,
}
```

Example output 2:
```javascript
{
  range: {
    test: {
      gte: moment().quarter(moment().quarter()).startOf('quarter').format('YYYY-MM-DD'),
      lte: moment.utc(datemath.parse(`${moment().quarter(moment().quarter()).startOf('quarter').format('YYYY-MM-DD')}||+3M-1d/d`)).format('YYYY-MM-DD'),
      format: 'dateOptionalTime'
    }
  }
}
```

- [Source code of the type: date](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/date.js).
- [Unit tests of the type: date](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/date.js).
- Elastic Search [Range QUery](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-range-query.html).

## Date Histogram Type

The `dateHistogram` type

| Property Name | Type | Description |
| --- | --- | --- |
| `key_field` |  |  |
| `value_field` |  |  |
| `interval` |  |  |
| `boundsRange_min` |  |  |
| `boundsRange_max` |  |  |
| `boundsRange_useDateMath` |  |  |

Example input:
```javascript
{
  key: 'test',
  type: 'dateHistogram',
  key_field: 'PO.IssuedDate',
  value_field: 'LineItem.TotalPrice'
}
```

Example output:
```javascript
{
  aggs: {
    max_date: {
      max: {
        field: 'PO.IssuedDate',
      },
    },
    min_date: {
      min: {
        field: 'PO.IssuedDate',
      },
    },
    twoLevelAgg: {
      date_histogram: {
        field: 'PO.IssuedDate',
        interval: 'year',
        min_doc_count: 0,
      },
      aggs: {
        twoLevelAgg: {
          stats: {
            field: 'LineItem.TotalPrice',
          },
        },
      },
    },
  },
}
```

- [Source code of the type: dateHistogram](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/dateHistogram.js).
- [Unit tests of the type: dateHistogram](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/dateHistogram.js).
- [Two Level Aggregations in ElasticSearch](https://www.elastic.co/blog/intro-to-aggregations-pt-2-sub-aggregations).

## Exists Type

The `exists` type is used to check wether some property exsits or not.
It requires only two fields: `field` and `value`.

| Property Name | Type | Description |
| --- | --- | --- |
| `field` | String | The target field we want to check. |
| `value` | Boolean | the value we want to check. Normally true or false. |

Example input:
```javascript
{
  type: 'bool',
  field: 'test',
  value: true
}
```

Example output:
```javascript
{
  exists: {
    field: 'test'
  }
}
```

- [Source code of the type: exists](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/exists.js).
- [Unit tests of the type: exists](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/exists.js).
- Elastic Search [Exists Query](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-exists-query.html).


## Facet Type

| Property Name | Type | Description |
| --- | --- | --- |
| `values` |  |  |
| `field` |  |  |
| `fieldMode` |  |  |
| `mode` |  |  |
| `size` |  |  |
| `sort` |  |  |
| `includeZeroes` |  |  |
| `optionsFilter` |  |  |
| `caseSensitive` |  |  |
| `anyOrder` |  |  |
| `maxWords` |  |  |
| `cardinality` |  |  |

Example input 1:
```javascript
{
  key: 'test',
  type: 'facet',
  field: 'testField',
  values: ['abc', '123']
}
```

Example output 1:
```javascript
{
  terms: {
    'testField.untouched': ['abc', '123']
  }
}
```

Example input with exclude:
```javascript
{
  key: 'test',
  type: 'facet',
  field: 'testField',
  mode: 'exclude',
  values: ['abc', '123'],
}
```

Example output with exclude:
```javascript
{
  bool: {
    must_not: {
      terms: {
        'testField.untouched': ['abc', '123'],
      },
    },
  },
}
```

TODO:
- Explain missing values.
- Explain find filter box.

- [Source code of the type:
  facet](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/facet.js).
- [Unit tests of the type:
  facet](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/facet.js).
- Elastic Search [Terms Query](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-terms-query.html).

TODO:
- All the other types!

[↪ Next: Mongo Example Types](mongo-example-types.md)
