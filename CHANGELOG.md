# Changelog

## `v0.0.25`

- Added a bunch of `@todos`
- Removed the `@throw` sassdoc tag.
- Renamed the `$interface` and `$i-value` variables to something related to "type".
- Created the `check-map-type` function for refactoring nested code.
- Created the `check-recurrent-type` function for the feature of recurrent types.

## Goals for `v0.1.0`
  - To-dos: **7**
  - [ ] Document usage
    - [x] Type validation usage
    - [ ] Mixin type validation
    - [x] Sass basics
  - [x] Sass basics
    - [x] to-string(any)
    - [x] capitalize(string)
    - [x] map-next-key()
  - [ ] Type validation
    - [ ] Add check for a dictionary with the same type.
    - [ ] Add a arglist option for spread args.
    - [ ] Add type shorthands (e.g. "numbers", "non-numbers", "dimensional")
    - [ ] Map functions that aid in extracting types like:
      - [ ] except($type)
      - [ ] extendable type map.