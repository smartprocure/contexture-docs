[↩  Parent: Table of Contents](../README.md)  
[↩  Previous: Glossary of Terms](glossary-of-terms.md)

# Map of Repos

The Contexture framework comes to life through a list of repositories
that individually specialize in some needed layer for our
architecture. We will be using most (if not all) of these projects in
our upcoming pages. Let's explore the repos we have so far:

## Contexture Core

[github.com/smartprocure/contexture](https://github.com/smartprocure/contexture)
is where our main DSL processor lives. It is a very small layer that
ties everything together. This one receives the information about the
different search representations, about the databases involved, and
the DSL, then outputs the search results respective to each one of the
queries described in a copy of the received DSL.

You can read more about the core here:
- [In the repository](https://github.com/smartprocure/contexture).
- In our [docs about querying (Contexture Core section)](../querying/contexture-core.md).
- Or with greater detail in our [under the hood docs (Contexture Core section)](../under-the-hood/contexture-core.md).

## Contexture Providers

The Contexture Providers are the interfacing layer that ties the
Contexture DSL to the targeted databases. So far, we have only two
open source providers:

- [contexture-elasticsearch](https://github.com/smartprocure/contexture-elasticsearch),
  and
- [contexture-mongo](https://github.com/smartprocure/contexture-mongo).

If you are planning to use either ElasticSearch or MongoDB for your
project, the best way to get started is to use those repositories.
However, if you need to use Contexture with another database, you will
need to implement the provider yourself. We're looking for code
contributors, so please don't feel limited to the current available
tools. Help us grow together!

You can read more about Contexture Providers here:
- In our [docs about querying (Available Providers section)](../querying/available-providers.md).
- In with greater detail in our [under the hood docs (Contexture Providers section)](../under-the-hood/contexture-providers/README.md).

## Contexture Client

The Contexture Client is responsible for triggering behaviors on the
search interfaces by knowing what causes changes in one or more
elements of the search tree. It is the key piece of technology that
allows our search interfaces to work in real time.

You can read more about the Contexture Client here:
- [In the repository](https://github.com/smartprocure/contexture-client).
- [In the repository] - In our [docs about querying (Contexture Client section)](../interactive-queries/contexture-client.md).
- Or with greater detail in our [under the hood docs (Contexture Client section)](../under-the-hood/contexture-client.md).

## Contexture React

The Contexture React repository holds a list of components that
facilitate building search interfaces. They are mainly graphical
representations of the types that exist on our Contexture Providers.

You can read more about the Contexture React:
- [In the repository](https://github.com/smartprocure/contexture-client).
- In our guide for the [Available React Components for Types](./types/react-components.md).
- Or in greater detail in our [under the hood docs (Contexture React section)](under-the-hood/contexture-react.md).

[↪ Next: Brief History](brief-history.md)
