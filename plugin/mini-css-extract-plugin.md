## ! Caution

You need to know 'css-loader' first.

## Use

It makes a css file by css codes made by 'css-loader' which are in the output file.

## Installation

Please install 'mini-css-extract-plugin'.

! Of course, 'css-loader' should be installed.

## Example

### settings

|configuration file|

```js
const path = require('path');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

module.exports = {
  mode: 'development',
  entry: './source/index.js',
  output: {
    path: path.resolve(process.cwd(), 'public'),
    filename: 'bundle.js',
  },
  plugins: [new MiniCssExtractPlugin()],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: [MiniCssExtractPlugin.loader, 'css-loader'],
      },
    ],
  },
};
```

|source/index.js|

```js
import './style.css';

const $root = document.querySelector('#root');

$root.textContent = 'index';
```

|source/style.css|

```css
body {
  background-color: aliceblue;
  color: tomato;
}
```

### results

|public/bundle.js|

```js
// Because it is too long, let me skip it.
// ! There are "not" 'aliceblue' and 'tomato'.
```

|public/main.css|

```css
body {
  background-color: aliceblue;
  color: tomato;
}
```
