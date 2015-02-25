# Changelog

## 0.4.0

  - Update all dependencies to latest version

## 0.3.0

  - **Released Friday November 28th, 2014 @ 4.45pm**
  - Improved assert method for numbers, now returns false if the inspected object is ```NaN```

## 0.2.3

  - **Released Saturday May 10th, 2014 @ 6.35pm**
  - One shared logger, across the entire runtime

## 0.2.2

  - **Released Saturday May 10th, 2014 @ 5.15pm**
  - Logs with namespace ```error``` are always red

## 0.2.1

  - **Released Sunday May 4th, 2014 @ 5.30pm**
  - Fixed stupid issue from ```o.publicInterface()``` implementation

## 0.2.0

  - **Released Sunday May 4th, 2014 @ 5.15pm**
  - Add public interface by defining a ```publicMethods``` array on Klass
  - Access it with ```o.publicInterface()```

## 0.1.5

  - **Released Saturday May 3rd, 2014 @ 10pm**
  - Fix issue with the custom triggerEvent() method, now correctly calls calls the "all" event when any event is triggered

## 0.1.4

  - **Released Friday May 2nd, 2014 @ 8.05pm**
  - Added missing dependency: colors

## 0.1.3

  - **Released Friday May 2nd, 2014 @ 8pm**
  - Added missing dependency: watchdirectory

## 0.1.2

  - **Released Friday May 2nd, 2014 @ 3.50pmm**
  - Fixed performance issue when using ```filesystem.findFirstMatch``` on large folder structures, for real this time

## 0.1.1

  - **Released Friday May 2nd, 2014 @ 3pmm**
  - Fixed performance issue when using ```filesystem.findFirstMatch``` on large folder structures

## 0.1.0

  - **Released Friday May 2nd, 2014 @ 11am**
  - Initial release, ported from [asimov.js](https://github.com/adamrenklint/asimov.js)
