# Dointeractive Javascript style guide

## <a name="naming convention">Naming convention</a>
- Use camelCase when naming objects, function and instances

```javascript
// do
var kitten = {}
function purrAndMew() {}
var lovelyPusheen = new Cat()

// don't
var Pusheen = {}
function purr_and_mew() {}
var lovely-pusheen = new Cat()
```

- Use PascalCase when naming constuctors

```javascript
function Cat(options) {
  this.mood = options.mood
}

var grumpyCat = new Cat({
  mood: 'Grumpy'
})
```

- Name variable `self` when saving reference to `this`

```javascript
  // do
  var self = this

  // don't
  var that = this
```

## <a name='semicolons'>Semicolons</a>
- Use semicolons only where it's needed. So __don't use semicolons__!

```javascript
// do 
for(; i < length; i++) {}

// don't
var name = 'nyan cat';
var sharpenClaws = function () {
  // some code
};
```

## <a name='strings'>Strings</a>

- Use single quotes `''` for strings

```javascript
// do
var name = 'pushen'

// don't
var name = "kitty"
```

## <a name='variables'>Variables</a>
- Use leading commas for variables declaration
- Use one `var` declaration for multiple variables and declare each variable on a new line

```javascript
// do
var mustache
  , pads
  , tail

// don't
var mustache
var pads
var tail
```

## <a name="whitespaces">Whitespaces</a>
- Use 2 space indentation

```javascript
// do
function () {
··var name
}

// don't
function () {
····var name
}
```

- Functions declaration indentation examples 

```javascript
// do 
function get() {
  // some code
}

// don't
function get(){
  // some code
}

// do
function () {
  // some code
}
  
// don't
function (){
  // some code
}
```
  
- Conditions indentation examples

```javascript
// do
if (condition) {
  // some code
}

// don't
if(condition){
  // some code
}
```

- Don't put spaces in array declaration

```javascript
var items = ['one', 'two', 'three']

// don't
var items = [ 'one', 'two', 'three' ]
```

## <a name='blocks'>Blocks</a>

- Use braces with all multi-line blocks.

```javascript
// do
if (condition) return false

// do
if (condition) {
  return false
}

// don't
if (test)
  return false
```

- Use single line function declaration only for simple function in chaining methods

```javascript
// do 
kittens
  .map(function (i) { return i.fur === 'fluffy' })
  .reduce(function(m, i) { return m + i })

// don't
var purr = function() { /* some code */ }
