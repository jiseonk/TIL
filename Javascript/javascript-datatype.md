# Javascript data type

## let : mutuable data type

```
let name = "abcd";
console.log(name);
```
In es6 update, declare using let.

### Alert : Do not use Var !!  
 The Reasons : 
 1. **var hoisting** : pull variable declarations to the top regardless of where they are located.
 2. Var has no block scope.
 
### What is Block scope?
  ```
  let globalName = "global name";
{
	let name = "local";
	console.log(name);
	console.log(globalName);
}
console.log(name);
console.log(globalName);
  ```
  Block scope is what encloses codes with bracket. The variable in the block scope is a local variable.  
  If you declare a variable out of the scope, it is a global variable. 
  It is recommended that you use the global variable to a minimum because it is stored in memory from program execution to end.
  
## Constants : Immutable data type
```
 const number;
```
 Use const whenever possible.
 * const makes immutable reference (!= immutable varaiable)
 * It prevents the variable to be assigned to another value.
 * arrays and objects assigned to const is mutable.
 
## Data and Structure types
  * Primitive (data type) : number, string, boolean, bigint, undefined, symbol, null
  * Object (non data but structural type)
  * Function (non data structure)
      * first-class function : This is treated like other data types that can be assigned to variable, passed as parameter to another      	function, returned from other functions.
      
### number
  * We don't need int, double in Javascript. only number!
  * Even number declaration is unnecessary because a type of javascript is decided dynamically, as opposed to Typescript.
```
 let a = 10; //integer
 let b = 1.1; //decimal number
 
 //special value
 const infinity = 1/0;
 const negativeInfinity = -1/0;
 const fault = NaN; //Not a Number
```

## BigInt
```
const bigInt = 1234567890123456789012345678901234567890n;
const bigInt = Bigint(1234567890123456789012345678901234567890);
```
Bigint represents whole number larger than 2^53-1 Which is the largest number in Javascript.
To make bigint, add n to the end of an integer number or call the function BigInt().

## String
```
const char = 'c';
const name = 'Anne';
const hello = 'Hello' + name;
```
A string in javascript is one or more characters surrounded by quotes. 
```
//By using backtick, make code simpler
console.log(`value: ${helloBob}, type ${typeof helloBob}`);
//If you don't use backtick, it will be like this..
console.log('value: ' +helloBob + 'type: ` + typeof helloBob);
```

