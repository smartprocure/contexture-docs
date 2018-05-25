# Contexture Providers

The _Contexture Providers_ are an abstraction layer around the databases that can be targeted by any given search tree. Each Provider by itself is a function that is called for initialization, which expects the following parameters:

| Input Object Property | Meaning |
| ------- | ------- |
| `types` | [Contexture Types](#TODO) that apply for this specific provider |
| `getClient` | Function that will return the direct database API manager, such as the `mongodb` NPM package. |

This initialization retutns an object with:

| Return Object Property | Meaning |
| ------- | ------- |
| `types` | [Contexture Types](#TODO) that apply for this specific provider |
| `groupCombinator` | Function that will determine how to construct boolean operations on the search tree nodes, such as `and`, `or` and `not`. |
 
With that in mind, let's explore our currently available providers:

## contexture-mongo
## contexture-elasticsearch
