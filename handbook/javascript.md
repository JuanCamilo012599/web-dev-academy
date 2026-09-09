# JavaScript

## Variables: let, const, var

### Scope:
let is block-scoped, so it exists only inside the nearest { } block. var is function-scoped, so it remains available throughout the entire function.

### Hoisting and TDZ:
A var declaration is hoisted and initialized as undefined, so it can be accessed before its declaration. let is in the temporal dead zone (TDZ) until its declaration is reached, so accessing it early causes an error.

### Redeclaration:
var can be redeclared in the same scope, but let cannot. This makes let safer because it prevents accidental duplicate declarations.

#### My Rule:
As a general rule, use const by default when the variable will not be reassigned. Use let when its value must change, such as for a counter. Use var only when maintaining older code that depends on its function-scoping behavior.