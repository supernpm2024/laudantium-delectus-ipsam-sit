# @supernpm2024/laudantium-delectus-ipsam-sit <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES 2021 spec-compliant shim for Promise.any. Invoke its "shim" method to shim `Promise.any` if it is unavailable or noncompliant. **Note**: a global `Promise` must already exist: the [es6-shim](https://github.com/es-shims/es6-shim) is recommended.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment that has `Promise` available globally, and complies with the [spec](https://tc39.es/ecma262/#sec-@supernpm2024/laudantium-delectus-ipsam-sit).

Most common usage:
```js
var assert = require('assert');
var any = require('@supernpm2024/laudantium-delectus-ipsam-sit');

var resolved = Promise.resolve(42);
var rejected = Promise.reject(-1);
var alsoRejected = Promise.reject(Infinity);

any([resolved, rejected, alsoRejected]).then(function (result) {
	assert.equal(result, 42);
});

any([rejected, alsoRejected]).catch(function (error) {
	assert.ok(error instanceof AggregateError);
	assert.deepEqual(error.errors, [-1, Infinity]);
});

any.shim(); // will be a no-op if not needed

Promise.any([resolved, rejected, alsoRejected]).then(function (result) {
	assert.equal(result, 42);
});

Promise.any([rejected, alsoRejected]).catch(function (error) {
	assert.ok(error instanceof AggregateError);
	assert.deepEqual(error.errors, [-1, Infinity]);
});
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

## Pre-1.0 versions

The `@supernpm2024/laudantium-delectus-ipsam-sit` package was released as now-deprecated v0.1.0 and v0.1.1, as a fork of https://github.com/m0ppers/promise-any.

Thanks to @sadorlovsky for donating the repo and the `@supernpm2024/laudantium-delectus-ipsam-sit` npm package!

[package-url]: https://npmjs.com/package/@supernpm2024/laudantium-delectus-ipsam-sit
[npm-version-svg]: https://versionbadg.es/supernpm2024/laudantium-delectus-ipsam-sit.svg
[deps-svg]: https://david-dm.org/supernpm2024/laudantium-delectus-ipsam-sit.svg
[deps-url]: https://david-dm.org/supernpm2024/laudantium-delectus-ipsam-sit
[dev-deps-svg]: https://david-dm.org/supernpm2024/laudantium-delectus-ipsam-sit/dev-status.svg
[dev-deps-url]: https://david-dm.org/supernpm2024/laudantium-delectus-ipsam-sit#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@supernpm2024/laudantium-delectus-ipsam-sit.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@supernpm2024/laudantium-delectus-ipsam-sit.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@supernpm2024/laudantium-delectus-ipsam-sit.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@supernpm2024/laudantium-delectus-ipsam-sit
[codecov-image]: https://codecov.io/gh/supernpm2024/laudantium-delectus-ipsam-sit/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/supernpm2024/laudantium-delectus-ipsam-sit/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/supernpm2024/laudantium-delectus-ipsam-sit
[actions-url]: https://github.com/supernpm2024/laudantium-delectus-ipsam-sit/actions
