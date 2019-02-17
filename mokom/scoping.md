# Scoping & Closures

In general all variables live in the global scope unless they are declared inside a function definition. Variables in the global scope live from the point they are declared until the end of the program's execution. Conditional and loop code-blocks do not create an inner scope and all the code in the code blocks are executed in the global scope.

Functions are the only language construct that create inner scopes. Hence variables declared inside a function's body, as well as the function's parameters, only live inside the function's body.

```
while (true) {
  var var1 = 99
}
print var1              // gives 99, because var1 is global

var f1 = function() {
  var var2 = 55
}

// print var2           // error! var2 doesn't exist outside the function body!
f1()
// print var2           // var2 ceases to live once the function returns
```

MokoM is **lexically/statically scoped**, which means a function's scope is limited in the function's code body (cf. dynamically scoped, where a function's scope is the time period of the function's execution, see Wikipedia for details). Ultimately, this means that a function called within another function does not have access to the calling 'parent' function's variables: 

```
var func1 = function() {
  print var1
}

var func2 = function() {
  var var1 = "hello"
  func1()               // error! func1 does not have access to var1 declared in func2!
}

// func2()
```

Inner scopes do have access to variables in the parent scope, however, so all global variables are accessible from inside function body's - as long as the global variable is declared before the function is called. This also makes recursive functions possible.

```
var func1 = function() {
  print var1
}

// func1()              // error! var1 not declared!
var var1 = "hello"
func1()                 // ok! will print 'hello'

var recursive = function(n) {
  if (n == 0) {
    return "done!"
  }
  recursive(n-1)        // recursive call!
}

print recursive(10)
```

It is possible to override global variables in an inner scope by simply declaring the same variable name in an inner scope. The variable name then refers to the inner-scope version from that point onwards.

```
var var1 = "foo"        // global variable!
var func1 = function() {
  print var1            // prints "foo"
  var var1              // overrides global with local version
  var1 = "bar"          // assign local version to "bar"
                        // this doesn't affect the global var1!
  print var1            // prints "bar"
}

func1()
print var1              // still "foo"!
```

Functions in MokoM are **closures** (see Wikipedia for details), which means functions remember the lexical referencing environment they are defined in. In other words, functions have access to all variables in the scope they are defined in (not called in as in dynamic scoping), including function scope local variables if the function is defined inside another function, no matter where the function is eventually called.

```
var func1 = function() {
  var counter = 1
  return function() {           // function defined in another function
    counter = counter + 1       // has access to local variable in 'parent' function
    return counter
  }
}

var counterinc = func1()
print counterinc()              // gives 2
print counterinc()              // gives 3
print counterinc()              // gives 4
// print counter                // counter is not global!

var func2 = function(param1) {
  return function(param2) {
    return param1 + param2       // works for parameters as well as local variables
  }
}
var add2 = func2(2)
var add5 = func2(5)
print add2(2)                   // gives 4
print add2(7)                   // gives 9
print add5(2)                   // gives 7
print add5(7)                   // gives 12
```

In the case of 'add2' and 'add5' above, the returned function for func2(2) and func2(5) are defined under different scopes - in func2(2), param1 has value 2 and so the returned function also sees param1 as having value 2, and in func2(5), param1 has value 5, so the returned function sees param1 as having value 5. A function creates a new inner scope every time it is called and so a function defined in another function always remembers a unique referencing environment.

```
var func1 = function() {
  var counter = 1
  return function() {           // function defined in another function
    counter = counter + 1       // has access to local variable in 'parent' function
    return counter
  }
}

var counterinc = func1()
var counterinc2 = func1()

// counterinc and counterinc2 remembers different environments
// because each call of func1 creates a new unique scope!
print counterinc()              // gives 2
print counterinc()              // gives 3
print counterinc()              // gives 4
print counterinc2()             // gives 2
print counterinc2()             // gives 3
print counterinc()              // gives 5
```
