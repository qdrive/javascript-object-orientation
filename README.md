# Javascript Object Orientation

A simple example of creating and initializing a reusable Javascript class.

``` js
var classExample = function (options) {

    // Variables
    var vars = {
        var1: 'Hello',
        var2: 'World'
    };

    // Class constructor
    this.construct = function (options) {

        // Initialize the extend function.
        var ex = extend();

        // Extend the options.
        ex(vars, options);
    };

    // The public method which can be instantiated outside of this class.
    this.publicMethodExample = function () {

        // Do work here.
        console.log(vars.var1);
        console.log(vars.var2);

        // Call the internal method.
        privateMethodExample();
    };

    // Internal method that can only be acccessed by this class.
    var privateMethodExample = function () {

        // Do work here.
        console.log('Just a message from the internal private method!');

    };

    // Extend function added for completeness but can be included anywhere.
    function extend() {
        return function (out) {
            out = out || {};
            for (var i = 1; i < arguments.length; i++) {
                if (!arguments[i])
                    continue;
                for (var key in arguments[i]) {
                    if (arguments[i].hasOwnProperty(key))
                        out[key] = arguments[i][key];
                }
            }
            return out;
        };
    }

    // Make the options publically available when initializing this class.
    this.construct(options);

};
```

Example using the Default Variables

``` js
var ce = new classExample();
ce.publicMethodExample();
```

Example Overriding the Default Variables

``` js
var ce = new classExample({ 
    var1: 'Aye up',
    var2: 'Yorkshire' 
});
ce.publicMethodExample();
```