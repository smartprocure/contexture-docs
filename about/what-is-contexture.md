[↩  Parent: Table of Contents](../README.md)  
[↩  Previous: About Contexture](README.md)

# What Is Contexture

People of the Internet, here we officialy introduce you to
`contexture`, our framework for building search interfaces.

This framework is carefully designed to be a generic solution for a
universe of unlimited possible search interfaces. We've started with a
minimal set of repositories that are representative of tools that
empower our business, but are intended to be merely examples. If
anything, our approaches are only use cases, for the potential of
this tool is ultimately yours to take.

A quick search over the Internet would reveal that the word
`contexture` means: `the fact or manner of being woven or linked
together to form a connected whole` or even `the putting together of
words and sentences in connected composition; the construction of a
text`.

With this word we are trying to expose not only our ultimate
intentions, but also more or less how the system is built. The way our
projects work is by a DSL that is used to gather different intended
search inputs, each one representing some useful abstraction of a
search filter (like a search input or a tags filter), then using the
values to process the DSL into one or more different database query
languages, running the underlying searches as optimized as possible,
then returning these values on the respective sections of the DSL, so
that each result can update each one of the components of the user
interface.

The canonical example of a Contexture Node is faceted search, where
you have a checkbox list that is both a filter (in the sense that it
restricts results based on the checked values) and an aggregation
(which shows the top n values that can be checked). Contexture allows
them to be nested in advanced searches with boolean joins like
`and`/`or`/`not`.

This thought process will become more clear as we progress through the
docs. Hopefully, some pages later it will become clear how we provide
a new perspective on building search interfaces, and perhaps even how
you can use it to power up your business just like we have been doing
for almost a decade.

[↪ Next: Glossary of Terms](glossary-of-terms.md)  
[↪ Or perhaps you want to jump to: Map of Repos](map-of-repos.md)
