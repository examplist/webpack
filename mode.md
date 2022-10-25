## Reference

homepage > DOCUMENTATION > Configuration > Mode

## Use

We have to choose the way of the bundling.

These are the ways: 'none' | 'development' | 'production'.

If it isn't set, an error will pop up.

In 'production' mode, codes are not formatted because the developers won't see it.

In 'development' mode, codes are formatted because the developers will see it.

You can set this using the CLI or a configuration file.

## Example

|the configuration file|

```js
const path = require('path');

module.exports = {
  // mode
  mode: 'development',
  entry: './source/index.js',
  output: {
    path: path.resolve(__dirname, 'public'),
    filename: 'bundle.js',
  },
};
```
