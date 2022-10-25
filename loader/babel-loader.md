## Installation

First, please install Babel tools you want.

Second, please install 'babel-loader' as a dev dependecy.

## Example

### Settings

In this file, I am going to use '@babel/preset-typescript'.

|the configuration file|

```js
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './source/index.ts',
  output: {
    path: path.resolve(process.cwd(), 'public'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.ts$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-typescript'],
          },
        },
      },
    ],
  },
  resolve: {
    // if
    // 1. there is a same name file with 'js' extension
    // 2. '.ts' is not written
    // then
    // 'js' file will be applied.
    extensions: ['.ts'],
  },
};
```

|source/export.ts|

```ts
export default 'in export';
```

|source/index.ts|

```ts
import str from './export';

const $root = document.querySelector('#root');

if ($root) {
  $root.innerHTML = str;
}
```

### Results

|public/bundle.js|

```js
const e = document.querySelector('#root');
e && (e.innerHTML = 'in export');
```
