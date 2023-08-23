# Module Federation OS Output Different

The `@module-federation/node` package is producing a different output for `macos` and `windows`.

To reproduce this error, follow the steps below on both `macos` and `windows`.

1. Clone this repo
2. Install the dependencies `npm i`
3. Build the `remote1` app for server - `nx run remote1:server`
4. Compare the output of the `main.js` file in `dist/apps/remote1/server/main.js`

On `macos` the output is:
```js
/***/ 7271:
/*!********************************!*\
  !*** ./apps/remote1/server.ts ***!
  \********************************/
/***/ (function(__unused_webpack_module, __unused_webpack_exports, __webpack_require__) {



__webpack_require__.e(/*! import() */ 751).then(__webpack_require__.bind(__webpack_require__, /*! ./src/main.server */ 6751));

/***/ }),
```

On `windows` the output is:
```js
/***/ 3372:
/*!********************************!*\
  !*** ./apps/remote1/server.ts ***!
  \********************************/
/***/ (function(__unused_webpack_module, __webpack_exports__, __webpack_require__) {

__webpack_require__.r(__webpack_exports__);
/* harmony export */ __webpack_require__.d(__webpack_exports__, {
/* harmony export */   renderApplication: function() { return /* reexport safe */ _angular_platform_server__WEBPACK_IMPORTED_MODULE_0__.renderApplication; },
/* harmony export */   renderModule: function() { return /* reexport safe */ _angular_platform_server__WEBPACK_IMPORTED_MODULE_0__.renderModule; },
/* harmony export */   "ɵSERVER_CONTEXT": function() { return /* reexport safe */ _angular_platform_server__WEBPACK_IMPORTED_MODULE_0__["ɵSERVER_CONTEXT"]; }
/* harmony export */ });
/* harmony import */ var _angular_platform_server__WEBPACK_IMPORTED_MODULE_0__ = __webpack_require__(/*! @angular/platform-server */ 9019);
/* harmony import */ var _angular_platform_server__WEBPACK_IMPORTED_MODULE_0___default = /*#__PURE__*/__webpack_require__.n(_angular_platform_server__WEBPACK_IMPORTED_MODULE_0__);


__webpack_require__.e(/*! import() */ 425).then(__webpack_require__.bind(__webpack_require__, /*! ./src/main.server */ 3425));

  // EXPORTS added by @angular-devkit/build-angular
  
  

/***/ }),
```

## Sanity Check
As a sanity check, you can see that if you build the `myssrapp` with `nx run myssrapp:server` and compare the `main.js` file in `dist/apps/myssrapp/server/main.js` they are identical across both OS platforms.
