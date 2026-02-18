# @hashtagchris/typescript-lib

A registry package with a TypeScript entry point and erasable TypeScript syntax. A JavaScript distribution is NOT included with this package.

## Doesn't work with the Node.js runtime

While Node has [some support for running TypeScript code](https://nodejs.org/en/learn/typescript/run-natively), you can't use this package, at least not with Node 25. Dependents will hit `ERR_UNSUPPORTED_NODE_MODULES_TYPE_STRIPPING`. See https://github.com/nodejs/node/issues/57215#issuecomment-2689347639 for why this is by design.

### Usage Test

```javascript
const { add } = require('@hashtagchris/typescript-lib');

console.log(add(2, 3));
```

### Error

```
% npm install @hashtagchris/typescript-lib

% node test-typescript-lib.js
node:internal/modules/typescript:183
    throw new ERR_UNSUPPORTED_NODE_MODULES_TYPE_STRIPPING(filename);
    ^

Error [ERR_UNSUPPORTED_NODE_MODULES_TYPE_STRIPPING]: Stripping types is currently unsupported for files under node_modules, for "/tmp/tests/node_modules/@hashtagchris/typescript-lib/index.ts"
    at stripTypeScriptModuleTypes (node:internal/modules/typescript:183:11)
    at Module._compile (node:internal/modules/cjs/loader:1712:15)
    at Module._extensions..js (node:internal/modules/cjs/loader:1892:10)
    at Module.load (node:internal/modules/cjs/loader:1480:32)
    at Module._load (node:internal/modules/cjs/loader:1299:12)
    at TracingChannel.traceSync (node:diagnostics_channel:328:14)
    at wrapModuleLoad (node:internal/modules/cjs/loader:245:24)
    at Module.require (node:internal/modules/cjs/loader:1503:12)
    at require (node:internal/modules/helpers:152:16)
    at Object.<anonymous> (/tmp/tests/test-typescript-lib.js:1:17) {
  code: 'ERR_UNSUPPORTED_NODE_MODULES_TYPE_STRIPPING'
}

Node.js v25.2.1
```