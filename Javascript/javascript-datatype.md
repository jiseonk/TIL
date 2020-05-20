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
