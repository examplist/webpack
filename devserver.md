## Reference

homepage > DOCUMENTATION > Configuration > DevServer

## Use

It is annoying to bundle(npx webpack) every time we edit the files.

Of course, we can use '--watch(-w)' in the CLI.

But the problem is bundling requires a lot of resources.

Because everything should be bundled again.

So, it is needed to reflect only edited parts.

That is why we use devserver.

What we have to be careful is actual bundling does not occur.

It just shows the final result in the screen.

## Installation

Please install 'webpack-dev-server' as a dev dependency.

Also, please install 'html-webpack-plugin' as a dev dependency. This is needed because actual bundling does not occur. So, to check with HTML files, we need make instant HTML file that will be on the dev server.

If you are not familiar with plugins, please check plugin folder.

## Example

### Settings

|the configuration file|

```js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  // If 'mode' is not set, warning will be on the browser.
  mode: 'production',
  entry: './source/index.js',
  plugins: [
    new HtmlWebpackPlugin({
      template: './source/template.html',
    }),
  ],
  devServer: {
    // If this is true, the browser opens automatically as we run the server.
    open: true,
    // If this is true, it uses Hot Module Replacement.
    hot: true,
    port: 3000,
  },
};
```

### Running Command

'serve' should be added.

```sh
$ npx webpack serve
```
