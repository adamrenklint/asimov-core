asimov-core
================

[![NPM version](https://badge.fury.io/js/asimov-core.png)](http://badge.fury.io/js/asimov-core) [![Code Climate](https://codeclimate.com/github/adamrenklint/asimov-core.png)](https://codeclimate.com/github/adamrenklint/asimov-core) [![Dependency Status](https://david-dm.org/adamrenklint/asimov-core.png?theme=shields.io)](https://david-dm.org/adamrenklint/asimov-core)

**Base classes and toolkit for [asimov.js](http://asimovjs.org)**

## How to use

### Install from NPM

    $ npm install asimov-core

### Klass, an EventEmitter class

Klass is a base class, which all other classes build on, and it is itself mostly a wrapper for the **EventEmitter** in [wunderbits.core](https://github.com/wunderlist/wunderbits.core/).

```
var Klass = require('asimov-core').Klass;

var MyClass = module.exports = Klass.extend({
  
  'myMethod': function () {
    console.log('Hello world')!
  }
});
```

#### Events

If you've worked with Backbone or wunderbits.core before, the API for binding to and triggering events should feel very familiar.

```
var theThing = new MyClass();

theThing.on('event', function () {
  console.log('stuff done!');
});

theThing.trigger('event');
```

#### Assert type and existance

Klass and all of its child classes comes with a convenient method for typechecking.

```
var MyClass = module.exports = Klass.extend({
  
  'saveValue': function (value) {
    this.assert('number', value, 'Value must be a number!');
  }
});
```

---

Made by [Adam Renklint](http://adamrenklint.com), Berlin 2014. [MIT licensed](https://github.com/adamrenklint/asimov-test/blob/master/LICENSE).