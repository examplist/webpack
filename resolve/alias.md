## Reference

homepage > DOCUMENTATION > Configuration > Resolve > resolve > resolve.alias

## Use

If you don't want to write a long path to get modules, you can use this.

## Example

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
  resolve: {
    // the part
    alias: {
      '@utils': path.resolve(__dirname, 'source', 'utils'),
    },
  },
};
```

|source/utils/util1.js|

```js
export default function () {
  return 'util1';
}
```

|source/index.js|

```js
// The path has changed.
import util1 from '@utils/util1';
// not this one
// import util1 from './utils/util1';

console.log(util1());
```

|public/bundle.js|

```js
(() => {
  'use strict';
  console.log('util1');
})();
```
