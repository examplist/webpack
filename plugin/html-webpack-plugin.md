## Use

If the template HTML file is given, it generates a HTML file which uses the bundled js file.

## Installation

Please install 'html-webpack-plugin' as a dev dependency.

## Example

### Settings

|the configuration file|

```js
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
      template: './source/pre-plugin.html',
      // In filename, the working directory is the ouput's path.
      filename: './re-plugin.html',
    }),
  ],
};
```

|source/pre-plugin.html|

It is the template HTML file.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>Pre-Plugin</h1>
    <div id="root"></div>
  </body>
</html>
```

There is no script tag to bring js files.

|source/export.js|

```js
export default 'in export';
```

|source/index.js|

```js
import str from './export';

const $root = document.querySelector('#root');

$root.textContent = str;
```

### Results

|public/bundle.js|

```js
document.querySelector('#root').textContent = 'in export';
```

|public/re-plugin.html|

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>Document</title>
    <script defer="defer" src="bundle.js"></script>
  </head>
  <body>
    <h1>Pre-Plugin</h1>
    <div id="root"></div>
  </body>
</html>
```

There is a script tag to bring |bundle.js|.
