## Reference

homepage > DOCUMENTATION > Configuration

## Problems So Far

1. We have to write this long command.

```sh
$ npx webpack --entry ./source/index.js -o ./public
```

2. We cannot decide the name of the file.

## Solution

It is using a configuration file.

## Basic

|config.js|

```js
const path = require('path');

module.exports = {
  entry: './source/index.js',
  output: {
    path: path.resolve(__dirname, 'public'),
    // Unlike writing in cli, we can decide the name of the file.
    filename: 'bundle.js',
  },
};
```

```sh
$ npx webpack --config config.js
```

## webpack.config.js

If the name of the file is 'webpack.config.js', you can omit '--config ~' like this.

```sh
$ npx webpack
```

## ES-Module System.

The configuration file also accepts ES-Module system.

```js
import path from 'path';

export default {
  entry: './source/index.js',
  output: {
    path: path.resolve(process.cwd(), 'public'),
    filename: 'bundle.js',
  },
};
```

But be careful that '\_\_dirname' cannot be used in ES-Module system.

So, this is not possible.

```js
import path from 'path';

export default {
  entry: './source/index.js',
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js',
  },
};
```

If you want to use '\_\_dirname', then change the file extension as 'cjs' and use CommonJS system.
