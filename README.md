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

### Logger

The logger class wraps console log to provide namespacing, task durations and more than one log level.

#### Simple logging

```
var Logger = require('asimov-core').Logger;
var logger = new Logger();

logger.log('my-app', 'My awesome log message');
```

#### Log a pending task

```
logger.pending('my-app', 'Doing things right now');
```

#### Log task duration

```
var started = new Date();

setTimeout(function () {
  logger.since('my-app', 'And we are done', started);
}, 1000);
```

#### Log level low

These logs will only appear if ```process.env.VERBOSE``` is ```true```.

```
logger.low('my-app', 'My debug message');
logger.lowSince('my-app', 'Some task is done', started);
```

### Filesystem

All synchronous filesystem abstraction, providing shortcuts for common use cases.

```
var Filesystem = require('asimov-core').Filesystem;
var fs = new Filesystem();
```

- ```fs.exists (string path)``` check if path exists, returns true or false
- ```fs.readDirectory (string path, function iterator)``` if path exists, execute iterator with path of each file and return true. if path doesn't exist, returns false.

### ChildProcess

A small wrapper for child_process. Documentation coming soon!

---

Made by [Adam Renklint](http://adamrenklint.com), Berlin 2014. [MIT licensed](https://github.com/adamrenklint/asimov-test/blob/master/LICENSE).