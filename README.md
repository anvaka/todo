# todo

I have lots of ideas, not so much time. Just dump my ideas here, without any particular order. Feel free to implement them.

# Browserify plugin to generate `guard` statements.

When browserifying a file, produce a guard statements where required. E.g.

``` javascript
module.exports = user;

function greet(user) {
 return "Hello " + user.getName();
}
```

This code uses method `getName` of user, without even checking three assumptions:

1. `user` is defined
2. `getName` is defined
3. `getName` is a function

We could do:

``` javascript
module.exports = user;
var guard = require('... guard module ... ');

function greet(user) {
  guard(greet); // protect ourselves!
  return "Hello " + user.getName();
}
```

When this code is browserified we could run a transform which will inject all guarding logic:

``` javascript
module.exports = user;
var guard = require('... guard module ... ');

function greet(user) {
 guard(user).has('getName()');

 return "Hello " + user.getName();
}
```

# Generate web-friendly builds for commonjs packages

When you have a browser-friendly commonjs package, it's often desirable to just play with it
on jsbin/jsfiddle. It would be nice to have a script which automatically browserifies and
publishes package to `gh-pages`, so, that users can just copy-paste link to browserified
version.

One can use `http://requirebin.com/` or [browserify as a service](https://github.com/jesusabdullah/browserify-cdn) too.
These are awesome tool. I just find requirebin less user friendly who needs html/css too. 
Whereas `browserify-cdn` is potentially not as reliable as gh-pages.

# ZSH <=> JS transpiler
Could be fun to write this transpiler...
