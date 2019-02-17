# Variables

Variable names may contain any alphanumeric character as well as underscore.

All variables need to be declared before use. Variables are declared using the var keyword, followed by a space, and then a variable name, or a comma-separated list of variable names. Once declared, variables can then be assigned values and used in expressions, until the end of the variable's scope (see Scoping and Closures section for details).

Variables are assigned values using the assignment operator = with the syntax 'variablename'='expression or value', wherein the value or the evaluated result of the expression will be assigned to the given variablename. Variables can also be assigned values at declaration time.

All expressions are evaluated before assignment. Lazy evaluation is not supported. All parts of an expression will be evaluated - there is no short circuit evaluation.

All assignments are by value. MokoM does not support any kind of pointer or reference.

```
// declare a variable called myVar
	var myVar

	// assign values
	myVar = 3
	myVar = (7 - 9) * 2

	// declare 3 variables at once
	var var_1, var_2, var_3
	var_1 = "hello"
	var_2 = 7
	var_3 = var_2 + 3

	// cannot assign to undeclared variable:
	// var_4 = 3

	// invalid variable names
	// var var!, 3var, $var

	// assigning values at declaration time:
	var new_var = "a value"
	var var_4 = 7, var_5 = 9, var_6 = "a string"
  ```
