## Build

Before pushing and tagging follow these steps:

1. Install `vercel/ncc` by running this command in your terminal. `npm i -g @vercel/ncc`

2. Compile your `index.js` file. `ncc build index.js --license licenses.txt`

More more information, go [here](https://docs.github.com/en/actions/creating-actions/creating-a-javascript-action#commit-tag-and-push-your-action-to-github)

3. ncc emits plain `require(...)` calls in the ES-module bundle. Insert this as line 2 of `dist/index.js` after building (otherwise: "require is not defined in ES module scope"):

    `const require = __WEBPACK_EXTERNAL_createRequire(import.meta.url);`
