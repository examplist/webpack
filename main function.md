## Main Function

It bundles files linked by module system.

## Which Modules Are Possible?

According to this link(https://webpack.js.org/concepts/modules/), these are possible.

Some are natively supported and some are not.

- An ES2015 import statement

- A CommonJS require() statement

- An AMD define and require statement

- An @import statement inside of a css/sass/less file.

- An image url in a stylesheet url(...) or HTML &lt;img src=...&gt; file.

## Example

### Settings

|source/export.js|

```js
export default 'in export';
```

|source/index.js|

```js
import str from './export.js';

const $root = document.querySelector('#root');

$root.textContent = str;
```

### Results

|public/bundle.js|

```js
document.querySelector('#root').textContent = 'in export';
```
