# Changelog

## `v0.0.31`

- Updated the `t-o()` function to support an optional type (`$t`) parameter to return the type string of `$v`.
- Fixed typo in `~/test/_basics.test.scss`.

## Goals for `v0.1.0`
  - To-dos: **15**
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