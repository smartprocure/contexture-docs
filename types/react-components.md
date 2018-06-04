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
![Date Type Screenshot 3](https://i.imgur.com/acvIuIS.png)

(Purpose)

Here's how you write a node of type `date` in your _searchTree_:
```javascript
{
  type: 'date',
  field: 'fieldName',
  from: '2016-04-25',
  to: '2017-05-26'
}
```

Here is the list of properties that it expects to have on the node:

| Property Name | Type | Description |
| --- | --- | --- |

Here's how you write your component:
```javascript
let DateComponent = require('contexture-react/dist/exampleTypes').Date

// Then, on your render function, or where you put your components:
<DateComponent path={['date']} tree={searchTree}/>
```

- [Source code of the date type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/src/example-types/date.js).
- [Unit tests of the date type](https://github.com/smartprocure/contexture-elasticsearch/blob/master/test/example-types/date.js).
- [Source code of the Date component](https://github.com/smartprocure/contexture-react/blob/master/src/exampleTypes/Date.js).

## DateHistogram
## Facet
## Number
## Query
## ResultCount
## ResultPager
## ResultTable
## TermsStats

[↪ Next: Other Components](../other-components/README.md)
