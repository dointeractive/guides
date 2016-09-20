#Javascript style guide

1. [Naming convention](#naming_convention)
2. [ES6](#ES6)
3. [Semicolons](#semicolons)
4. [Objects](#objects)
5. [Strings](#strings)
6. [Variables](#variables)
7. [Whitespaces](#whitespaces)
8. [Blocks](#blocks)
9. [Selectors](#selectors)

## <a name="naming_convention">Naming convention</a>
- Use complete readable speakable names, try not to use abbreviations and shortened names
- Single letter variables names are only allowed in cycles and primitive anonymous functions
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

- Prefix jQuery objects with $ sign
```javascript
// do
var $body = $('body')

// don't
var body = $('body')
```

## <a name='es6'>ES6</a>
- Where it's possible prefer `const` over `let`, and `let` over `var`

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

## <a name='objects'>Objects</a>

- Insert line breaks, after leading and before trailing curly braces, declaring long objects

```javascript
var obj = {
  key1: 'value',
  key2: 'value'
}

// don't
var obj = { key1: 'value',
            key2: 'value' }
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
function·get()·{
  // some code
}

// don't
function·get(){
  // some code
}

// do
function·()·{
  // some code
}

// don't
function·(){
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
var items = [·'one', 'two', 'three'·]
```

- In hash declaration put spaces before and after trailing and leading curly braces correspondingly
```javascript
var obj = {·key: value·}

// don't
var obj = {key: value}
```

- Don't put leading space before colon in hash declaration

```javascript
var obj = { key: value }

// don't
var obj = { key·: value }
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
  .reduce(function (m, i) { return m + i })

// don't
var purr = function () { /* some code */ }
```

## <a name='selectors'>Selectors</a>

- Prefer to use `data-` attributes as a selectors
- Avoid use of class selectors
