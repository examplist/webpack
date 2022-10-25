## Use

We can import files in other languages like CSS, TypeScript, or JSX.

## Kinds

Let me introduce each loader using other files in this folder.

## How to Use

1. install the related modules

2. write related things in the configuration file as below

```js
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './source/index.js',
  output: {
    path: path.resolve(process.cwd(), 'public'),
    filename: 'bundle.js',
  },
  // this part
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```

## Execution Order

reference: https://webpack.js.org/concepts/loaders/#configuration

The latter one in 'use' array is executed earlier.

In the above example, 'css-loader' is executed earlier than 'style-loader'.
