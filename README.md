asimov-core
================

[![NPM version](https://badge.fury.io/js/asimov-core.png)](http://badge.fury.io/js/asimov-core) [![Code Climate](https://codeclimate.com/github/adamrenklint/asimov-core.png)](https://codeclimate.com/github/adamrenklint/asimov-core) [![Dependency Status](https://david-dm.org/adamrenklint/asimov-core.png?theme=shields.io)](https://david-dm.org/adamrenklint/asimov-core)

**Base classes and toolkit for [asimov.js](http://asimovjs.org)**

## How to use

### Install from NPM

    $ npm install asimov-core

### Klass, an EventEmitter class

Klass is a base class, which all other classes build on, and it is itself mostly a wrapper for the **EventEmitter** in [wunderbits.core](https://github.com/wunderlist/wunderbits.core/).

```javascript
var Klass = require('asimov-core').Klass;

var MyClass = module.exports = Klass.extend({

  'myMethod': function () {
    console.log('Hello world')!
  }
});
```

#### Events

If you've worked with Backbone or wunderbits.core before, the API for binding to and triggering events should feel very familiar.

```javascript
var theThing = new MyClass();

theThing.on('event', function () {
  console.log('stuff done!');
});

theThing.trigger('event');
```

#### Assert type and existance

Klass and all of its child classes comes with a convenient method for typechecking.

```javascript
var MyClass = module.exports = Klass.extend({

  'saveValue': function (anything, value) {
    this.assert('defined', anything, 'Anything must be defined!');
    this.assert('number', value, 'Value must be a number!');
  }
});
```

#### Privacy with public interface

A class can implement a public interface by defining an array of method names. Useful for singleton, top-level modules.

```javascript
var MyClass = Klass.extend({

  'publicMethods': [
    'aMethodName'
  ]
});
var instance = new MyClass();
module.exports = instance.publicInterface();
```

### Logger

The logger class wraps console log to provide namespacing, task durations and more than one log level.

#### Simple logging

```javascript
var Logger = require('asimov-core').Logger;
var logger = new Logger();

logger.log('my-app', 'My awesome log message');
```

#### Log a pending task

```javascript
logger.pending('my-app', 'Doing things right now');
```

#### Log task duration

```javascript
var started = new Date();

setTimeout(function () {
  logger.since('my-app', 'And we are done', started);
}, 1000);
```

#### Log level low

These logs will only appear if ```process.env.VERBOSE``` is ```true```.

```javascript
logger.low('my-app', 'My debug message');
logger.lowSince('my-app', 'Some task is done', started);
```

### Filesystem

All synchronous filesystem abstraction, providing shortcuts for common use cases.

```
var Filesystem = require('asimov-core').Filesystem;
var fs = new Filesystem();
```

- ```fs.exists (string path)``` Check if path exists, returns true or false.
- ```fs.cleanDirectory (string path)``` Recursively delete everything in path.
- ```fs.copyDirectoryIfExists (string srcPath, string destPath)``` If source path exists, copy it to destination and return true. If source path doesn't exist, returns false.
- ```fs.findFirstMatch (string grep, array paths)``` Returns the path of the first file found matching the string grep, or false if no file was found.
- ```fs.forceExists (string path)``` Force a folder path to exist.
- ```fs.getStats (string path)``` Return the stat object for path.
- ```fs.isDirectory (string path)``` Returns true if path is a directory, otherwise false.
- ```fs.hasFileExtension (string filename, string extension)``` Check if filename has the expected extension, returns true or false.
- ```fs.readDirectory (string path, function iterator)``` If path exists, execute iterator with path of each file and return true. If path doesn't exist, returns false.
- ```fs.readFile (string path)``` Read and return file.
- ```fs.rebuildDirectory (string path)``` Delete a folder and recreate it as empty.
- ```fs.recursiveDelete (string path)``` Walks a tree, deletes all files and folders.
- ```fs.recursiveForFolders (string path, function iterator)``` Execute iterator for all folders in path, top down.
- ```fs.watchTree (string path, function handler)``` Watch path for added, removed and modified files using [watchdirectory](https://www.npmjs.org/package/watchdirectory). Returns a function that can be called to stop watching the path.
- ```fs.writeFile (string path, value)``` Write value to file at path.

### ChildProcess

A small wrapper for child_process. Documentation coming soon!

---

Made by [Adam Renklint](http://adamrenklint.com), Berlin 2014. [MIT licensed](https://github.com/adamrenklint/asimov-test/blob/master/LICENSE).
