#### This is our code style guide. Its here to help us write better code!

# Strict Mode

The `'use strict'` directive helps catch mistakes and protects us from JavaScript's "bad parts." There's no reason (that I know of) not to use it. In CoffeeScript it should be placed at the top of the file. In JavaScript, it should be placed at the top of the IIFE in order to prevent strict mode from "leaking" into other scripts that were perhaps not written for strict mode.

__CoffeeScript__

```CoffeeScript
'use strict'
# awesome code starts here
```

__JavaScript__

```
!(function () {
  'use strict';
  // awesome code starts here
})()
```



# Long Lists

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



# Naming Things

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

