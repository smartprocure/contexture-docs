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

**Note:** Keep in mind that the styles of these components is purely
optional. Later on we'll see how to [style our
components](../theming/README.md).

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

| Property Name | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | Date or String (`YYYY-MM-DD` format) | Yes | The initial date of our timeframe. |
| `to` | Date or String (`YYYY-MM-DD` format) | No | The final date of our timeframe. |

**Note:** The properties present in the search tree that aren't used by the node
might be needed for the Provider's type. See the Provider type's
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

## Date Histogram

![Date Histogram Screenshot](https://i.imgur.com/XwuGi2c.png)

(TODO: Purpose)

Here's how you write a node of type `dateHistogram` in your _searchTree_:
```javascript
{
  key: 'releases',
  type: 'dateHistogram',
  key_field: 'released',
  value_field: 'imdbVotes',
  interval: '3650d',
}
```

**Note:** The properties present in the search tree that aren't used by the node
might be needed for the Provider's type. See the Provider type's
documentation in our [previous pages](README.md).

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

![Facet Type Screenshot](https://i.imgur.com/1X3mrfq.png)

(TODO: Purpose)

Here's how you write a node of type `facet` in your _searchTree_:
```javascript
{
  key: 'facet',
  type: 'facet',
  values: ['a'],
}
```

Here is the list of properties that this component expects to have on the node:

| Property Name | Type | Required | Description |
| --- | --- | --- | --- |
| `values` | Array | Yes | Array of selected values. To have a value selected by default, you will need to know in advance which value to put here, otherwise you can leave this with an empty array and let users select the values themselves. |
| `size` | Number | No | Max number of options to display. The default is 10. |

**Note:** The properties present in the search tree that aren't used by the node
might be needed for the Provider's type. See the Provider type's
documentation in our [previous pages](README.md).

Here's how you write your component:
```javascript
let Facet = require('contexture-react/dist/exampleTypes').Facet
// ...
// Then, on your render function, or where you put your components:
<Facet path={['facet']} tree={searchTree}/>
```

- [Source code of the facet type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/facet.js).
- [Unit tests of the facet type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/facet.js).
- [Source code of the Facet component](https://github.com/smartprocure/contexture-react/blob/master/src/exampleTypes/Facet.js).

## Number
## Query
## ResultCount
## ResultPager
## ResultTable
## TermsStats

[↪ Next: Other Components](../other-components/README.md)
