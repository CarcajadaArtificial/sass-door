# Sass Door 🚪
``Hello ( ´ ω ` )ノﾞ`` thanks a lot for being interested in this library. Something I've found when developing SCSS is that the language doesn't feature any help in error handling besides `@error`. The code that upgrades this is really short but I'd rather not copy and paste it in every project where I need some type of error handling.

[Read the docs](https://carcajadaartificial.github.io/sass-door/)

## Setup
The simplest way to setup Sass Door is to install it in a node project:
```bash
npm i sass-door -D
```
But in the case you're not using Node in your project you can import it as a git submodule or simply by copying the files to your project.

## Usage
To use this library, one must simply import it using the `@use` sass keyword and target the index of the project.
```scss
@use 'path/to/sass-door' as *;
```

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
53 │   --scss-error: '#{throw($message, $catch)}';
   │                    ^^^^^^^^^^^^^^^^^^^^^^^
   ╵
   path/to/index.scss 5:5 example-mixin()
```
As an additional feature, the error message string is also applied as a custom CSS property called `--scss-error`. This is also useful for unit testing mixins.
```scss
.example {
  @include example-mixin(false);
}
/*
.example {
  --scss-error: "Incorrect input";
}
*/
```

## Configuration
I would recommend in your file structure have a `/lib/` directory where you can import Sass Door's index scss. This snippet contains all configurable variables with their default value. [Read more](https://carcajadaartificial.github.io/sass-door/#config-variable)
```scss
// ~/lib/sass-door.scss
@forward 'path/to/sass-door' with (
  $catching-enabled: true,
  $mixin-style-name: '--scss-error',
);
```