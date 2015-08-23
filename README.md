# Javascript Client App Template
This project is meant to be a template for setting up a project that will auto bundle multiple javascript source files into a single deployable javascript output file.

## Basic Usage
Assuming this template has been forked.
1. clone locally
2. cd to project folder
3. `npm install`
4. `gulp bundle` (or use `gulp bundle --type ship` to output minified files)
5. Output files will be in `dist` folder

## Advance Usage
This project template uses gulp to automate common tasks. The following tasks are supported.
### `gulp bundle`
Using browserify bundles everything `src\index.js` and `spec/tests.js` source files require into single output files. Also as part of this process transforms the input files using babel to convert es6 syntax to es5.
### `gulp autoBundle`
Wraps the browserify call in bundle with watchify to re-bundle whenever a source file changes. Watchify caches the input files so re-bundling is faster. Task runs until cancel (`ctrl-c`).
### `gulp jasmine`
Starts a server at localhost:8888 which hosts the jasmine unit tests. Points at the bundled output `dist/tests.js`. If the file changes a refresh of the browser will load the latest version. Task runs until cancel (`ctrl-c`).
### `gulp autoLint`
Looks at all js source files in the src and spec folders and lints them using eslint. If a source file changes then will re-lint that file. Task runs until cancel (`ctrl-c`).
### `gulp watch`
Runs the `autoBundle`, `jasmine`, and `autoLint`.
### Options
If the command line argument `--type ship` is passed into any task, the output js files will be minify (appending the suffix `.min`). If tests are run as part of that task it will be on the minified files.
