## ! Caution

You need to know 'css-loader' first.

## Use

This makes css codes imported by 'css-loader' be applied to DOM.

! These will not make a new CSS file. The contents will be in the JS file.

## Installation

Please install 'style-loader' as a dev dependency.

! 'css-loader' should be installed as well.

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
        // Because css-loader should be used first,
        // the order should be like this.
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
};
```

### Results

|public/bundle.js|

```js
// Because it is so long, let me skip this part.
```

Unlike when only 'css-loader' exists, the style will be applied to the DOM.
