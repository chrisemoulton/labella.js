Docs ▸
**Introduction** |
[Development](docs/Development.md) |
[Demo](http://twitter.github.io/labella.js/)
&nbsp;&nbsp;////&nbsp;&nbsp;
API Reference ▸
[Force](docs/Force.md) |
[Node](docs/Node.md) |
[Renderer](docs/Renderer.md)

# Labella.js

*"Labels should be beautiful."*

If you try to place labels for points on a timeline (or any 1D space), one common problem is the labels often overlap.
How about making the labels push each other. Use the force, jedi-style.

* Play with [interactive demo](http://twitter.github.io/labella.js/) to learn more
* See examples: [up](http://twitter.github.io/labella.js/basic_up.html) |
[down](http://twitter.github.io/labella.js/basic_down.html) |
[left](http://twitter.github.io/labella.js/basic_left.html) |
[right](http://twitter.github.io/labella.js/basic_right.html) |
[with text (v)](http://twitter.github.io/labella.js/with_text.html) |
[with text (h)](http://twitter.github.io/labella.js/with_text2.html)
* Read the instructions on this page or API reference.

Moreover, if you are looking for a ready-to-use timeline component with Labella's smart labeling instead of building your own timeline from scratch, check out [d3Kit-timeline](https://github.com/kristw/d3kit-timeline)

### Install

```
npm install labella --save
```

or

```
bower install labella --save
```

### Import to your project

##### Choice 1. Global

Adding this library via ```<script>``` tag is the simplest way. By doing this, ```labella``` is available in the global scope.

```html
<script src="labella.min.js"></script>
```

##### Choice 2: AMD

If you use requirejs, Labella.js support AMD out of the box.

```javascript
require(['path/to/labella'], function(labella) {
  // do something
});
```

##### Choice 3: node.js / browserify

Labella.js also supports usage in commonjs style.

```javascript
var labella = require('path/to/labella');
```

### Example

```javascript
// idealPos: The most preferred position for each label
// width:    The width of each label
var nodes = [
  new labella.Node(1, 50), // idealPos, width
  new labella.Node(2, 50),
  new labella.Node(3, 50),
  new labella.Node(3, 50),
  new labella.Node(3, 50),
];

var force = new labella.Force()
  .nodes(nodes)
  // Listen when the nodes' positions are updated.
  .on('end', function(){
    // The rendering is independent from this library.
    // User can use canvas, svg or any library to draw the labels.
    // There is also a built-in helper labella.Renderer for this purpose. See the examples
    draw(force.nodes());
  })
  // Run simulation at most 100 rounds. It may end earlier if equillibrium is reached.
  .start(100);
```

### Author

Krist Wongsuphasawat / [@kristw](https://twitter.com/kristw)

Copyright 2015 Twitter, Inc. Licensed under the [Apache License Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
