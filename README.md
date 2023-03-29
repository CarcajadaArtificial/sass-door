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
```scss
@use 'path/to/sass-door' as *;
```
