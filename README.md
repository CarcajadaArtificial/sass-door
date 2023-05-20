# Sass Door 🚪
``Hello ( ´ ω ` )ノﾞ`` thanks a lot for being interested in this library. Here's the story, even though I really like SCSS, I find it far away from the things I deeply love. I feel uneasy that the general direction of Sass as a programming tool points becomes more and more unaligned with my own path as a developer. I think there are so many more robust and complex things that can be done using it if only it had a few upgrades.

 - **Type Safety** - Having Scss behave a little more like TypeScript or Rust would be fantastic. Having data types for different units and keywords would be helpful for writing functions and mixins.
 - **Error Handling** - There are only three at-rules `@error`, `@warn`, and `@debug` that help somewhat in handling errors. Simply having a `throw()` function and mixin would make a huge difference.
 - **Basic Utilities** - Some staples are missing in the official modules, type conversions, transformations, and others.

These are the scope of things I can add myself. These three upgrades can mostly be done using Sass itself and rather slimly. If I could vent for a second, what I believe this language desperately needs that can only be correctly done by modifying the Dart source code are: hard typing, callback functions, complete modularity, and unit tests (I know about Sass True and appreciate it but I think that it is limited due to having a Sass implementation).

## Setup
The simplest way to setup Sass Door is to install it in a node project:
```bash
npm i sass-door -D
```
But in the case you're not using Node in your project you can import it as a git submodule or simply by copying `~/index.scss` to your project.

## Usage
To use this library, one must simply import it using the `@use` sass keyword and target the index of the project.
```scss
@use 'path/to/sass-door' as *;
```

[Read the reference](https://carcajadaartificial.github.io/sass-door/)

---
## Type Safety
*Coming soon*

### Basic argument type
With a few functions, a big map, and a little imagination we can simulate type safety right here in SCSS. _If only Scss would become rusty..._ So let's see the first example, say a simple function like one that squares a number. Given a scope for only number types (there won't be squaring strings, booleans, colors, etc) and a missing `@return` expression on the flow where the type does not match.
```scss
@use 'path/to/sass-door' as *;

@function sq($n) {
  @if not check($n, 'number') {
    @return -1;
  }
  
  @return $n * $n;
}
```

### Union types
*Coming soon*
```scss
@use 'path/to/sass-door' as *;
```

### Interface types
*Coming soon*
```scss
@use 'path/to/sass-door' as *;
```

### Types in unit testing
Whenever unit tests come to mind in SCSS code, the only option is [True by Oddbird](github.com/oddbird/true). It is a fantastic library that, alone, makes unit testing available in Sass. Also, this is a modified version of the example function `sq()`, now the flow where the type does not match is accounted for and must be tested.
```scss
@use 'path/to/sass-door' as *;
@use 'true' as *;

@function sq($n) {
  @if not check($n, 'number') {
    @return -1;
  }
  @return $n * $n;
}

@include test-module('Number functions') {
  @include describe('@function sq($num)') {
    @include it('Correctly squares a number') {
      @include assert-equal(sq(12), 144);
    }
    @include it('Returns -1 with types other than a number') {
      @include assert-equal(sq('12'), -1);
    }
  }
}
```
When running the testing command, this is what the terminal would show:
```bash
Number functions
  @function sq($num)
    ✔ Correctly squares a number
    ✔ Returns -1 with types other than number
```

### Type safety and mixins
*Coming soon*
```scss
@use 'path/to/sass-door' as *;
```

---
## Error Handling
*Coming soon*

### Error handling in functions
Once imported, the error-handling functions become available for usage. For example, this is how it would look like this:
```scss
@use 'path/to/lib/sass-door.scss' as *;

@function example-function($ok) {
  @if not $ok {
    @return throw('Incorrect input');
  }
  @return null;
}
```
And once the `throw()` happens, it would look like this in the terminal:
```bash
Error: "Incorrect input"
  ╷
5 │     @return throw('Incorrect input');
  │             ^^^^^^^^^^^^^^^^^^^^^^^^
  ╵
  path/to/index.scss 5:13 example-function()
```
As an additional feature, the error message string is also returned in the `throw()` function. This is useful for unit testing.
```scss
@debug example-function(false); // Debug: Incorrect input
```

### Error handling in mixins
There's also the `throw()` mixin, whose name is exactly the same as the `throw()` function, but the mixin must be called using the `@include` keyword.
```scss
@use 'path/to/lib/sass-door.scss' as *;

@mixin example-mixin($ok) {
  @if not $ok {
    @include throw('Incorrect input');
  }
}
```
And once the `throw()` happens, it would look like this in the terminal:
```bash
Error: "Incorrect input"
   ╷
5  │   --scss-error: '#{throw($message, $catch)}';
   │                    ^^^^^^^^^^^^^^^^^^^^^^^
   ╵
   path/to/index.scss 5:5 example-mixin()
```
As an additional feature, the error messa ge string is also applied as a custom CSS property called `--scss-error`. This is also useful for unit testing mixins.
```scss
.example {
  @include example-mixin(false);
}
// .example {
//   --scss-error: "Incorrect input";
// }
```

---
## Sass Basics
Sass is a niche problem as a language with limited features. My opinion is that it can be much more. These are a set of functions and mixins (abbreviated as `@f` and `@m`) that do things that aren't available in the official SCSS modules. I just think they're neat.

- `@f` [`capitalize()`](carcajadaartificial.github.io/sass-door/#function-capitalize) - Turns the first letter of a string into uppercase.
- `@f` [`to-string()`](carcajadaartificial.github.io/sass-door/#function-to-string) - This function converts a value of any type into a string.
- `@f` [`map-next-key()`](carcajadaartificial.github.io/sass-door/#function-map-next-key) - Returns the next key in a map given the current key. 
- `@m` [`quick-mq()`]() - This mixin optionally applies a media query.
- `@m` [`quick-pseudo()`]() - This mixin optionally applies a pseudoclass.

---
## Configuration
I would recommend in your file structure have a `/lib/` directory where you can import Sass Door's index scss. This snippet contains all configurable variables with their default value. [Read more](https://carcajadaartificial.github.io/sass-door/#config-variable)
```scss
// ~/lib/sass-door.scss
@forward 'path/to/sass-door' with (
  $catching-enabled: true,
  $mixin-style-name: '--scss-error',
);
```
