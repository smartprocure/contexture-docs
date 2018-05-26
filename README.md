﻿# Contexture Documentation

This repo is designed to host the documentation of Contexture as a
whole. Everythin we currently have here is **WORK IN PROGRESS**.

## Table of Contents

- [About Contexture](about/index.md)
  - [What is Contexture](about/what-is-contexture.md)
  - [Map of Repos](about/map-of-repos.md)
  - [Brief History](about/brief-history.md)
  - [Alternatives & Benchmarks](about/alternatives-benchmarks.md)
- [Getting Started](getting-started/index.md)
  - [Project Setup & Use](getting-started/setup.md)
  - [Connecting to Elasticsearch](getting-started/connecting.md)
  - [Connecting to Other Databases](getting-started/connecting-other-databases.md)
  - [Simple Search Box](getting-started/simple-search-box.md)
  - [Your First Filter](getting-started/your-first-filter.md)
  - [Discovering the Database](getting-started/discovering-the-database.md)
  - [IMDB Index](getting-started/IMDB-example.md)
- [Querying](querying/index.md)
  - [Contexture Core](querying/contexture-core.md)
  - [Contexture DSL](querying/contexture-dsl.md)
  - [Available Providers](querying/available-providers.md)
- [Interactive Queries](interactive-queries/index.md)
  - [Contexture Client](interactive-queries/contexture-client.md)
  - [Introduction to Reactors](interactive-queries/reactors.md)
- [Types and Type Components](types/index.md)
  - [DIY Types](types/diy-types.md)
    - [How to Write a Type](types/diy-types.md#how-to-wite-a-type)
    - [How to Write a UI Component for a Type](types/diy-types.md#how-to-write-a-ui-component-for-a-type)
    - [The Example Types](types/diy-types.md#the-example-types)
  - [ElasticSearch Example Types](types/elasticsearch-example-types.md)
  - [Mongo Example Types](types/mongo-example-types.md)
  - [Available React Components for Types](types/example-types-react-components.md)
- [Other Components](other-components/index.md)
- [Managing State](managing-state/index.md)
  - [MobX](managing-state/mobx.md)
  - [Redux (Coming Soon)](managing-state/redux.md)
- [Theming](theming/index.md)
- [Recommendations](recommendations/index.md)
  - [Architecture](recommendations/architecture.md)
    - [Client vs Server](recommendations/architecture.md#client-vs-server)
    - [Type definitions](recommendations/architecture.md#type-definitions)
    - [Scaling](recommendations/architecture.md#scaling)
  - [Server Side Searches](recommendations/server-side-searches.md)
    - [Searching On an Endpoint](recommendations/server-side-searches.md#searching-on-an-endpoint)
    - [Caching](recommendations/server-side-searches.md#caching)
  - [Client Side Searches](recommendations/client-side-searches.md)
    - [Click to Search](recommendations/client-side-searches.md#click-to-search)
    - [Real Time Searches](recommendations/client-side-searches.md#real-time-searches)
    - [Cascading](recommendations/client-side-searches.md#cascading)
- [Under the Hood](under-the-hood/index.md)
  - [Design Principles](under-the-hood/design-principles.md)
  - [Contexture Core](under-the-hood/contexture-core.md)
    - [Default Export](under-the-hood/contexture-core.md#default-export)
    - [The Algorithm](under-the-hood/contexture-core.md#the-algorithm)
    - [Utility Functions](under-the-hood/contexture-core.md#utility-functions)
  - [Contexture Providers](under-the-hood/contexture-providers/index.md)
    - [Contexture ElasticSearch](under-the-hood/contexture-providers/)
    - [Contexture Mongo](under-the-hood/contexture-providers/)
  - [Contexture Client](under-the-hood/contexture-client.md)
    - [Reactors in detail](under-the-hood/contexture-client.md#reactors-in-detail)
  - [Contexture React](under-the-hood/contexture-react.md)
- [Examples](examples/index.md)
- [Contributing Guide](contributing-guide/index.md)
- [License](LICENSE)
