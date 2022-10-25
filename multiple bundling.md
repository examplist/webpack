## Concept

It can do multiple bundlings.

## Example

### Settings

|source/index1.js|

```js
import str from './export';

const $root = document.querySelector('#root');

$root.textContent = str + '1';
```

|source/index2.js|

```js
import str from './export';

const $root = document.querySelector('#root');

$root.textContent = str + '2';
```

|the configuration file|

```js
const path = require('path');

module.exports = {
  mode: 'production',
  entry: {
    // The keys go into ouput's '[name]' part.
    1: './source/index1.js',
    2: './source/index2.js',
  },
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle[name].js',
  },
};
```

### Results

|public/bundle1.js|

```js
document.querySelector('#root').textContent = 'in export1';
```

|public/bundle2.js|

```js
document.querySelector('#root').textContent = 'in export2';
```
