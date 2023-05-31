# Changelog

## `v0.0.35`

- Added the `check()` mixin.
- Added the use for the `$catch` parameter on the `throw()` mixin.
- Added documentation for the `check()` function and mixin.

## Goals for `v0.1.0`
  - To-dos: **6**
  - [ ] Document usage
    - [ ] Type validation usage
      - [ ] Single types
      - [ ] Union types
      - [ ] Interface types
      - [ ] Recurring types in maps and lists.
    - [ ] Mixin type validation
    - [x] Sass basics
  - [x] Sass basics
    - [x] to-string(any)
    - [x] capitalize(string)
    - [x] map-next-key()

### Ideas for `v0.2.0`
  - [ ] Type validation
    - [ ] Add check for a dictionary with the same type.
    - [ ] Add a arglist option for spread args.
    - [ ] Add type shorthands (e.g. "numbers", "non-numbers", "dimensional")
    - [ ] Map functions that aid in extracting types like:
      - [ ] except($type)
      - [ ] extendable type map.