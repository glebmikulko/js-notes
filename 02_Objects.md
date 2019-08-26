# Objects
## Basic
- associative arrays
- properties: strings or symbols, values - any types
- assigned and copied by references
- copy object with `Object.assing(dest, source)` or lodash `_.cloneDeep()`

```javascript
let obj = {
	'a': 1,
	[Symbol("gleb")]: 2
};

delete obj['a'] // deleting
alert('a' in obj) // check existance
for(let key in obj) console.log(key) // iterating
```
## Garbage collection
- Objects are retained in memory while they are reachable. (object can be linked but not reachable when linked to a pack of unreachable objects)
- Automatic collection

## Symbols
- Primitive type for unique identifiers
- Symbols are always different values, even if they have the same name
```javascript
let s = Symbol('gleb')
Symbol('gleb') === Symbol('gleb') // false
Symbol.for('gleb') === Symbol.for('gleb') // true
```
- The two main purposes of the symbols are:
1) Inject our fields in 'stranger's' code
2) Have access to some built-in JS variables

## Object methods, "this"
- “this” is not bound
```javascript
let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
  alert( this.name );
}

// use the same function in two objects
user.f = sayHi;
admin.f = sayHi;
```
- Arrow functions don't have own `this` and use outside value

## Object to primitive
- objects are always `true`
- there are 3 hints (conversion types) for objects: number, string and default (usually the same rule as number)
- method for conversions are: `obj[Symbol.toPrimitive](hint)`, `toString/valueOf`

## Constructor
```javascript
function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");
```
