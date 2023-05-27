# Changelog

## `v0.0.32`

- Added the `separator-character()` function.
- Fixed the function `to-string()` to print correctly the last element of a list and map.
- Fixed the function `to-string()` to support correct separators in lists.
- Refactored the funciton `capitalize()`.
- Updated the unit tests for the functions `to-string()` and `capitalize()`. `~/test/_basics.test.scss`.

## Goals for `v0.1.0`
  - To-dos: **11**
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