## Concept

webpack can bundle modules in node_modules.

## Example

### Settings

Please install lodash first.

|source/index.js|

```js
import _ from 'lodash';

const $root = document.querySelector('#root');

const str = _.toString([1, 2, 3]);

$root.textContent = str;
```

### Results

|public/bundle.js|

```js
// Because there are so many codes, please check the codes using HTML file.
```
