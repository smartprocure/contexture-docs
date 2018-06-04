[↩  Parent: Table of Contents](../README.md)  
[↩  Previous: Mongo Example Types](mongo-example-types.md)

# Available React Components for Types

A huge part of working with advanced search interfaces is identifying
how to portray a specific search filter that you might want to use.
We've talked about very simple components that react to changes on the
tree state, but now we'll see how to make it easier for more complex
nodes to gather the inputs necessary, and also to show the results
correctly. Here we'll see components specifically crafted for some of
our providers' example types.

## Date

![Date Type Screenshot 1](https://i.imgur.com/XwuGi2c.png)
![Date Type Screenshot 2](https://i.imgur.com/joTECy0.png)

_(Same goes with the right, not adding another screenshot to avoid
consuming more space.)_

(TODO: Purpose)

Here's how you write a node of type `date` in your _searchTree_:
```javascript
{
  type: 'date',
  field: 'fieldName',
  from: '2016-04-25',
  to: '2017-05-26'
}
```

Here is the list of properties that this component expects to have on the node:

| Property Name | Type | Description |
| --- | --- | --- |
| `from` | Date or String (`YYYY-MM-DD` format) | The initial date of our timeframe. |
| `to` | Date or String (`YYYY-MM-DD` format) | The final date of our timeframe. |

**Note:** The properties present in the search tree that aren't used by the node
might be needed for the provider's type. See the Provider type's
documentation in our [previous pages](README.md).

Here's how you write your component:
```javascript
let DateComponent = require('contexture-react/dist/exampleTypes').Date
// ...
// Then, on your render function, or where you put your components:
<DateComponent path={['date']} tree={searchTree}/>
```

- [Source code of the date type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/date.js).
- [Unit tests of the date type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/date.js).
- [Source code of the Date component](https://github.com/smartprocure/contexture-react/blob/master/src/exampleTypes/Date.js).

## DateHistogram

![Date Histogram Screenshot](https://i.imgur.com/XwuGi2c.png)

(TODO: Purpose)

Here's how you write a node of type `date` in your _searchTree_:
```javascript
{
  key: 'releases',
  type: 'dateHistogram',
  key_field: 'released',
  value_field: 'imdbVotes',
  interval: '3650d',
  context: {
    entries: [
      {
        key: 0,
        doc_count: 1,
        count: 1,
        min: 625633,
        max: 625633,
        avg: 625633,
        sum: 625633,
      },
      {
        key: 315360000000,
        doc_count: 3,
        count: 3,
        min: 74450,
        max: 557731,
        avg: 355868.3333333333,
        sum: 1067605,
      },
      {
        key: 630720000000,
        doc_count: 2,
        count: 2,
        min: 82360,
        max: 376362,
        avg: 229361,
        sum: 458722,
      },
      {
        key: 946080000000,
        doc_count: 4,
        count: 4,
        min: 28087,
        max: 395463,
        avg: 275019.25,
        sum: 1100077,
      },
      {
        key: 1261440000000,
        doc_count: 1,
        count: 1,
        min: 264551,
        max: 264551,
        avg: 264551,
        sum: 264551,
      },
    ],
    maxDate: null,
    minDate: null,
  },
}
```

Since this component doesn't need any property from the node itself,
but only from the results, here's how you write your component:
```javascript
let DateHistogram = require('contexture-react/dist/exampleTypes').DateHistogram
let formatYear = x => new Date(x).getFullYear() + 1
// ...
// Then, on your render function, or where you put your components:
<DateHistogram path={['dateHistogram']} format={formatYear} tree={searchTree}/>
```

- [Source code of the dateHistogram type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/dateHistogram.js).
- [Unit tests of the dateHistogram type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/dateHistogram.js).
- [Source code of the DateHistogram component](https://github.com/smartprocure/contexture-react/blob/master/src/exampleTypes/DateHistogram.js).

## Facet
## Number
## Query
## ResultCount
## ResultPager
## ResultTable
## TermsStats

[↪ Next: Other Components](../other-components/README.md)
