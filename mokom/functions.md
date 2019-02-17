# Functions

## Definition

Function definition follows a structure similar to anonymous functions in Javascript: the keyword function, followed by an argument signature in the form of paranthesis-enclosed, comma-separated parameter names, and then a code block containing the function body. 

Like with variable declaration, no type information needs to be specified for the parameters - the parameters are dynamic and can be assigned values of any type. 

Note that functions are first class values and are anonymous by default - there is no syntactic sugar to directly create a named function. Functions should be defined and assigned immediately to a variable, or returned from a function

The return keyword is used to immediately 'return' from the function, ignoring all statements after the return statement, and returning the given expression's evaluated value as the return value of the function.return can be used alone without an accompanying expression.

```
var functname = function(arg1, arg2) {
  return arg1 + arg2
  print "this is ignored"
}

var functname2 = function(arg1, arg2) {
  return function(arg3) {
     return arg1 + arg2 + arg3
  }
}

// this is invalid: function definitions are always anonymous!
// function myname(arg1, arg2) {
//    return arg1 + arg2
// }
```

## Calls

Once functions have been defined and assigned to a variable, they can be called with the familiar syntax of 'variable/function name' followed by paranthesis-enclosed, comma-separated argument values. Expressions given as arguments will be evaluated in-place first before being passed as parameters to the function. 

Lazy evaluation is not supported. All arguments are pass-by-value so functions can not mutate variables passed to them. Function calls should provide exactly as many arguments as the function definition expects. Note that any of the 5 data types can be passed as function arguments, including functions, making higher-order functions possible!

Notably, it is not possible to directly call an anonymous function at definition-time. It is also not possible to call a returned function directly, so the only way to call a function is to assign it to a variable first, then applying the syntax described above to that variable.

```
var functname = function(arg1, arg2) {
  return arg1 + arg2
  print "this is ignored"
}

var functname2 = function(arg1, arg2) {
  return function(arg3) {
     return arg1 + arg2 + arg3
  }
}

print functname(3,(4 + 7 - 3 - 4)) // gives 7
// print functname2(3,4)(5) // not allowed
// print function (arg) {
//   return arg
// } (1)                    // not allowed

// print functname(1)       // not enough arguments
// print functname(1,2,3,4) // too many arguments

var add2 = function(val) {
   val = val + 2
   return val
}
var b = 2
add2(b)
print b   // still 2 because pass by value!
b = add2(b)
print b   // now b is 4!

var apply_func_twice = function(func, arg) { // take function as parameter!
  arg = func(arg)
  arg = func(arg)
  return arg
}

print apply_func_twice(add2, 5)         // outputs 9
```
