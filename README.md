# Helpers to use jasmine with require

## requireDependencies(deps, cb)

Loads modules for testing

    describe('my tests', function() {
        requireDependencies(['someMod','anotherMod'], function(someMod, anotherMod) {
            // use someMod here or set a variable for use later
        });
    });

## requireStubs(stubs)

Creates stubs that will be returned from require that is in code that is being tested

Code to be tested

    function(cb) {
        require(['someMod'}, function(someMod) {
            // do something
            cb();
        });
    }


The following code will return your stub when require is called.

    describe('my tests', function() {
        stubs = {
            someMod: function(){
                return {// my module to return}
            }
        }

        beforeEach(function() {
            requireStubs(stubs);
        });
    });

NOTES:
* I use these with jasmine running as a rake/CI task.  I have not tested it with jasmine running standalone.
* The code uses Array.isArray() from ECMAScript 5.  Include a ES5 compatability library if you are testing using a browser that does not support ES5.



