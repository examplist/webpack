## If (1) NPM packages Are Used & (2) 'resolve - extensions' Are Used

|the configuration file|

```js
module.exports = {
  resolve: {
    extensions: ['.ts', '.js'],
  },
};
```

'.js' must be added. There are files in node_modules which use this. If '.js' is omitted, building works okay, but dev server does not work.

You can check the example through my 'React-without-toolchain' repository.
