## Use

These will process CSS files.

## Installation

Please install 'style-loader' and 'css-loader' as dev dependencies

## Example

### Settings

|source/style.css|

```css
body {
  background-color: aliceblue;
  color: tomato;
}
```

|source/index.js|

```js
// this part
import './style.css';

const $root = document.querySelector('#root');

$root.textContent = 'index';
```

|the configuration file|

```js
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './source/index.js',
  output: {
    path: path.resolve(process.cwd(), 'public'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        // Be careful that the order of elements in 'use' array should not change.
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```

### Results

|public/bundle.js|

```js
// Because it is too long, please check it through the HTML file.
```
