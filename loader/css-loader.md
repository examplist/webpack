## Use

These will import CSS codes to the output file.

! Although there are the codes in the file, they will not be applied to the DOM. You have to use other tools (such as style-loader) to apply them.

## Installation

Please install 'css-loader' as a dev dependency.

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
        use: ['css-loader'],
      },
    ],
  },
};
```

### Results

|public/bundle.js|

```js
// You can find 'aliceblue' and 'tomato'.
// ! Be careful the colors will not be applied.
```
