#### This is our code style guide. Its here to help us write better code!

JavaScript & CoffeeScript
=========================

## Strict Mode

The `'use strict'` directive helps catch mistakes and protects us from JavaScript's "bad parts." There's no reason (that I know of) not to use it. In CoffeeScript it should be placed at the top of the file. In JavaScript, it should be placed at the top of the IIFE in order to prevent strict mode from "leaking" into other scripts that were perhaps not written for strict mode.

__CoffeeScript__

```CoffeeScript
'use strict'
## awesome code starts here
```

__JavaScript__

```
!(function () {
  'use strict';
  // awesome code starts here
})()
```



## Long Lists

Anywhere you have a list with more than three items, consider putting each item on its own line. This makes it easier to read and easier to deal with when manually resolving Git merge conflicts. Types of lists include function arguments, function parameters, arrays etc.

__Good__

```CoffeeScript
angular.factory("omgDeps", (
  thingy,
  notherThingy,
  oneMore,
  omgOneMore,
  gobPleaseOneMore
) ->
  ...
```

__Bad__
  
```CoffeeScript
angular.factory("omgDeps", (thingy, notherThingy, oneMore, omgOneMore, gobPleaseOneMore) ->
  ...
```



## Naming Things

Capitalized names should refer classes and all classes should be referred to with capitalized names. 

__Good__

```CoffeeScript
yipYip = new Dog();
```

__Bad (and just looks funny)__

```CoffeeScript
yipYip = new dog();
```

__Also bad__

```CoffeeScript
FavoriteNumber = 12
```

Prefix property names with an underscore to signify that they're "private" and not intended for use by other "modules"

__Good__

```JavaScript
!(function () {
  function MyClass () {};

  MyClass.prototype._weirdPrivateMethodThatMakesNoSenseToUseOutsideThisFile = function () { ... };

  MyClass.prototype.callMe = function () { ... };
})();
```

__Bad__

```JavaScript
!(function () {
  function MyClass () {};

  MyClass.prototype.callMe = function () { ... };

  MyClass.prototype.orMaybeMe = function () { ... };
})();
```

Prefix "module level" variables with an underscore to easily differentiate from function local variables

__Good__

```CoffeeScript
_flavor = "vanilla"

exports.setFlavor = (flavor) ->
  _flavor = flavor
```

__Bad (funny tho)__

```CoffeeScript
flavor = "vanilla"

exports.setFlavor = (flavorFlav) ->
  flavor = flavorFlav
```



CSS & SASS
==========

Circa May 2016 we started using a naming convention based on the _Block, Element, Modifier_ (BEM) pattern. Using this convention, CSS classes consist of up to three parts: 

The _Block_ corresponds to a visual element consisting of a few simpler visual elements. Blocks have their own dedicated CSS classes. For example, if we're styling an analog clock, the clock itself would be the Block and might have a CSS class called simply `analog-clock`.

The _Elements_ are the simpler visual elements that compose the Block. So continuing with our analog clock example, each of the numbers might be an Element, and so might the hands. So we would have class names like `analog-clock__number` and `analog-clock__hand`. When writing style rules for Elements, the convention is to include the Block class in the rule selector like so: `.analog-clock .analog-clock__hand`. 

The _Modifiers_ correspond to variants of either Blocks or Elements. For instance, we might want to have different "skins" for our analog clock. For the "kit cat" skin, there would be a class called "analog-clock--kit-cat". When writing style rules for Modifiers the convention is to include the class being modified, the _base class_, like so `.analog-clock.analog-clock--kit-cat`. That way the properties in the Modifier's rules always override the corresponding properties in the base class's without resorting to `! important`. You might want a Block Modifier to also modify the Block's Elements, which can be achieved with a style rule selector like `.analog-clock.analog-clock--kit-cat .analog-clock__hand`. An example of a Element Modifier would be special classes for the hour hand and minute hand like `analog-clock__hand--hour` and `analog-clock__hand--minute` and would be selected with rules like `.analog-clock .analog-clock__hand.analog-clock__hand--hour` and `analog-clock .analog-clock__hand.analog-clock__hand--minute` respectively.

Sometimes we need rules that are shared across many Blocks. For that we have _Atomic_ classes. A rule for adding a certain amount of left margin is a perfect example because its usually not a good idea to include margin on a Block that may appear in several different contexts, some where a left margin is desirable and some where it isn't. Such a rule might simple be:

```CSS
.m-left10px { 
  margin-left: 10px;
}
```
