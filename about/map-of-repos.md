[↩  Parent: Table of Contents](../README.md)
[↩  Previous: Glossary of Terms](glossary-of-terms.md)

# Map of Repos

The Contexture framework comes to life through a list of repositories
that individually specialize in some needed layer for our
architecture. Let's explore the repos we have so far:

## Contexture core

[github.com/smartprocure/contexture](https://github.com/smartprocure/contexture)
is where our main DSL processor lives. It is a very small layer that
ties everything together. This one receives the information about the
different search representations, about the databases involved, and
the DSL, then outputs the search results respective to each one of the
queries described in a copy of the received DSL.

You can read more about the core here:
- [In the repository](https://github.com/smartprocure/contexture).
- In our [querying docs](../querying/contexture-core.md).
- In our [under the hood docs](../under-the-hood/contexture-core.md).

[↪ Next: Brief History](brief-history.md)
