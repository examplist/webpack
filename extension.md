## Concept

By default, we can leave file extensions out.

However, if we use [resolve > extensions], we can designate which file extensions can be left out. In this case, file extensions which are not written can't be left out.

## Example of No Extension Being Designated

### Settings

|source/export.js|

```js
export default 'in export';
```

|source/index.js|

```js
// 'js' is omitted.
import str from './export';

const $root = document.querySelector('#root');

$root.textContent = str;
```

### Results

|public/bundle.js|

```js
document.querySelector('#root').textContent = 'in export';
```

## Example of Extension Being Designated

|source/export.js| and |source/index.js| are same as above.

|the configuration file|

```js
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './source/index.js',
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js',
  },
  // This is the part.
  resolve: {
    extensions: ['.ts'],
  },
};
```

An error will occur.
