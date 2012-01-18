# Helpers to use jasmine with require

## requireDependencies(deps, cb)

Loads modules for testing

    describe('my tests', function() {
        requireDependencies(['someMod','anotherMod'], function(someMod, anotherMod) {
            // use someMod here or set a variable for use later
        });
    });

## requireStubs(stubs)

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



