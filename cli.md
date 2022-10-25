## Reference

homepage > DOCUMENTATION > API > Introduction > CLI > Learn more about the CLI!

## Base

```sh
$ npx webpack
```

## --entry, --output-path(-o)

after '--entry': the file which will be bundled

after '--output-path' or '-o': the directory where the bundled file will be saved

```sh
$ npx webpack --entry ./source/index.js -o ./public
```

The name of the bundled file will be 'main.js'.

## --watch(-w)

If there are changes in the file, it automatically bundles again.

```sh
$ npx webpack --entry ./source/index.js -o ./public -w
```

## --help

You can get the information about the CLI.

```
$ npx webpack --help
```
