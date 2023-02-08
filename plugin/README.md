## Reference

homepage > DOCUMENTATION > Plugins

## Concept

Literally, they are plug-ins.

Many of them create not only JS files, but also HTML files or CSS files.

## Kinds

Let me introduce each plug-in using other files in this folder.

## How to Use

1. install the plug-in

2. write related things in the configuration file as below

```js
// template: 'source/pre-plugin.html'
// result: 'public/re-plugin.html'

const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  mode: 'production',
  entry: './source/index.js',
  output: {
    path: __dirname + '/public',
    filename: 'bundle.js',
  },
  plugins: [
    new HtmlWebpackPlugin({
      // In filename, the working directory is the ouput's path.
      filename: './re-plugin.html',
      template: './source/pre-plugin.html',
    }),
  ],
};
```
