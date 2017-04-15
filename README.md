# api documentation for  [gulp-preprocess (v2.0.0)](http://github.com/jas/gulp-preprocess)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-preprocess.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-preprocess) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-preprocess.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-preprocess)
#### Gulp plugin to preprocess HTML, JavaScript, and other files based on custom context or environment configuration

[![NPM](https://nodei.co/npm/gulp-preprocess.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/gulp-preprocess)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-preprocess/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-preprocess/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-preprocess/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-preprocess/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jason Sandmeyer"
    },
    "bugs": {
        "url": "https://github.com/jas/gulp-preprocess/issues"
    },
    "dependencies": {
        "lodash": "3.10.x",
        "map-stream": "0.1.x",
        "preprocess": "^3.0.0"
    },
    "description": "Gulp plugin to preprocess HTML, JavaScript, and other files based on custom context or environment configuration",
    "devDependencies": {
        "gulp-util": "3.0.x",
        "mocha": "*",
        "should": "*"
    },
    "directories": {
        "test": "test"
    },
    "dist": {
        "shasum": "067bf6a4e1b703d7b45ed2047ce7e87d5974d241",
        "tarball": "https://registry.npmjs.org/gulp-preprocess/-/gulp-preprocess-2.0.0.tgz"
    },
    "engines": {
        "node": ">= 0.9.0"
    },
    "gitHead": "45bdd31567e6cdf873074f195deadde1ffac90b6",
    "homepage": "http://github.com/jas/gulp-preprocess",
    "keywords": [
        "gulpplugin",
        "gulp-plugin",
        "preprocessor",
        "html",
        "javascript",
        "coffeescript",
        "debug",
        "environment",
        "ENV",
        "conditional",
        "include",
        "exclude",
        "ifdef",
        "ifndef",
        "echo"
    ],
    "license": "MIT",
    "main": "./index.js",
    "maintainers": [
        {
            "name": "ioloie"
        },
        {
            "name": "jas"
        }
    ],
    "name": "gulp-preprocess",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/jas/gulp-preprocess.git"
    },
    "scripts": {
        "test": "mocha --reporter spec"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-preprocess](#apidoc.module.gulp-preprocess)
1.  [function <span class="apidocSignatureSpan"></span>gulp-preprocess (options)](#apidoc.element.gulp-preprocess.gulp-preprocess)
1.  [function <span class="apidocSignatureSpan">gulp-preprocess.</span>toString ()](#apidoc.element.gulp-preprocess.toString)



# <a name="apidoc.module.gulp-preprocess"></a>[module gulp-preprocess](#apidoc.module.gulp-preprocess)

#### <a name="apidoc.element.gulp-preprocess.gulp-preprocess"></a>[function <span class="apidocSignatureSpan"></span>gulp-preprocess (options)](#apidoc.element.gulp-preprocess.gulp-preprocess)
- description and source-code
```javascript
gulp-preprocess = function (options) {
  var opts    = _.merge({}, options);
  var context = _.merge({}, process.env, opts.context);

  function ppStream(file, callback) {
    var contents, extension;

    // TODO: support streaming files
    if (file.isNull()) return callback(null, file); // pass along
    if (file.isStream()) return callback(new Error("gulp-preprocess: Streaming not supported"));

    context.src = file.path;
    context.srcDir = opts.includeBase || path.dirname(file.path);
    context.NODE_ENV = context.NODE_ENV || 'development';

    extension = _.isEmpty(opts.extension) ? getExtension(context.src) : opts.extension;

    contents = file.contents.toString('utf8');
    contents = pp.preprocess(contents, context, extension);
    file.contents = new Buffer(contents);

    callback(null, file);
  }

  return map(ppStream);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-preprocess.toString"></a>[function <span class="apidocSignatureSpan">gulp-preprocess.</span>toString ()](#apidoc.element.gulp-preprocess.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
...

  context.src = file.path;
  context.srcDir = opts.includeBase || path.dirname(file.path);
  context.NODE_ENV = context.NODE_ENV || 'development';

  extension = _.isEmpty(opts.extension) ? getExtension(context.src) : opts.extension;

  contents = file.contents.toString('utf8');
  contents = pp.preprocess(contents, context, extension);
  file.contents = new Buffer(contents);

  callback(null, file);
}

return map(ppStream);
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
