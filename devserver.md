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

## Example

### Settings

Please install 'html-webpack-plugin' as a dev dependency. This is needed because actual bundling does not occur. So, to check whether it works, we need make an instant HTML file using a template HTML file. And the instant HTML file will be on the server.

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

|source/template.html|

```html
<body>
  <div>template</div>
  <div id="root"></div>
</body>
```

|source/index.js|

```js
const $root = document.querySelector('#root');

$root.textContent = 'dev server';
```

### Running Command

'serve' should be added.

```sh
$ npx webpack serve
```

If you run the code, the server address will be shown. Please go to the address.
