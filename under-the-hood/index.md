# Under The Hood

## Design Principles

- Intentionally stateless.
- Detached from state management tools.
- Can work well with state management tools.
- Modern ES6+
- Non-strict functional programming.
- Configuration based architecture.
- Focus on a very extensible small core.
- Small DSL.
  - Database agnostic.
  - Isomorphic Tree State.
  - Optimized for database discovery.
  - Optimized for advanced search interfaces.
  - Aiming to be effective for arbitrarily complex database indexes.
  - Simplicity over performance.
- Reaction management.
  - Tree walking.
  - State flags.
  - What updates.
  - Pauses.

## Contexture Core

- Initializer.
  - Arguments and return values.
  - What it does.
    - Initial values in the tree.
    - Flat lenses.
    - State flags.
    - Add filters.
    - DFS initialization.
  - Example usages.
- Core Utils.

## Contexture ElasticSearch
