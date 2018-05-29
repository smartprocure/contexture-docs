[↩  Parent: Table of Contents](../README.md)  
[↩  Previous: Glossary of Terms](glossary-of-terms.md)

# Map of Repos

The Contexture framework comes to life through a list of repositories
that individually specialize in some needed layer for our
architecture. Let's explore the repos we have so far:

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
- In our [under the hood docs (Contexture Core section)](../under-the-hood/contexture-core.md).

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
- In our [under the hood docs (Contexture Providers section)](../under-the-hood/contexture-providers/README.md).

[↪ Next: Brief History](brief-history.md)
