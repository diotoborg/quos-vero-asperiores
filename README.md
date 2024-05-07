# @diotoborg/quos-vero-asperiores <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Is this value a JS SharedArrayBuffer? This module works cross-realm/iframe, does not depend on `instanceof` or mutable properties, and despite ES6 Symbol.toStringTag.

## Example

```js
var assert = require('assert');
var isSharedArrayBuffer = require('@diotoborg/quos-vero-asperiores');

assert(!isSharedArrayBuffer(function () {}));
assert(!isSharedArrayBuffer(null));
assert(!isSharedArrayBuffer(function* () { yield 42; return Infinity; });
assert(!isSharedArrayBuffer(Symbol('foo')));
assert(!isSharedArrayBuffer(1n));
assert(!isSharedArrayBuffer(Object(1n)));

assert(!isSharedArrayBuffer(new Set()));
assert(!isSharedArrayBuffer(new WeakSet()));
assert(!isSharedArrayBuffer(new Map()));
assert(!isSharedArrayBuffer(new WeakMap()));
assert(!isSharedArrayBuffer(new WeakRef({})));
assert(!isSharedArrayBuffer(new FinalizationRegistry(() => {})));
assert(!isSharedArrayBuffer(new ArrayBuffer()));

assert(isSharedArrayBuffer(new SharedArrayBuffer()));

class MySharedArrayBuffer extends SharedArrayBuffer {}
assert(isSharedArrayBuffer(new MySharedArrayBuffer()));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/quos-vero-asperiores
[npm-version-svg]: https://versionbadg.es/inspect-js/@diotoborg/quos-vero-asperiores.svg
[deps-svg]: https://david-dm.org/inspect-js/@diotoborg/quos-vero-asperiores.svg
[deps-url]: https://david-dm.org/inspect-js/@diotoborg/quos-vero-asperiores
[dev-deps-svg]: https://david-dm.org/inspect-js/@diotoborg/quos-vero-asperiores/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@diotoborg/quos-vero-asperiores#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/quos-vero-asperiores.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/quos-vero-asperiores.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/quos-vero-asperiores.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/quos-vero-asperiores
[codecov-image]: https://codecov.io/gh/inspect-js/@diotoborg/quos-vero-asperiores/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@diotoborg/quos-vero-asperiores/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@diotoborg/quos-vero-asperiores
[actions-url]: https://github.com/diotoborg/quos-vero-asperiores/actions
