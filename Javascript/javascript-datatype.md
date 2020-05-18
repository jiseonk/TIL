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
  
# Constants : Immutable data type
```
 const number;
```
 const variable cannot be changed once it is declared.  
