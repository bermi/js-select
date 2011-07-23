# js-select

js-select is a little mashup of [js-traverse](https://github.com/substack/js-traverse) and a subset of [JSONSelect](http://jsonselect.org/).

It lets you traverse and modify JavaScript object nodes that match JSONSelect selectors:

```javascript
var select = require("js-select");

var people = {
   george: {
       age : 35,
       movie: "Repo Man"
   },
   mary: {
       age: 15,
       movie: "Twilight"
   }
}

select(people, ".age").forEach(function(age) {
     // make everyone look younger!
    this.update(age - 5);
})

select(people, ".age").nodes();  // [30, 10]
```

See [js-traverse](https://github.com/substack/js-traverse) for all the things you can do to modify the node. The `forEach()` callback will get the same context (`this`) as the `forEach()` callback in [js-traverse](https://github.com/substack/js-traverse), plus a `this.matches()` which will test if the node matches a selector:

```javascript
select(obj).forEach(function(node) {
    if(this.matches(".movie")) {
        this.update(node.toLowerCase());
    }
}
```

# selectors

js-select supports the following [JSONSelect](http://jsonselect.org/) selectors so far:

```
"*"
".key"
".ancestor .key"
".parent > .key"
```

# install

Download the code, then with [npm](http://npmjs.org):

```bash
npm install js-select
```

Get a browser file after npm-installing using [browserify](https://github.com/substack/node-browserify)
