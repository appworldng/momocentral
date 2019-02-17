# MokoM

## Introduction

The MokoM programming language is a minimalistic programming language that hopefully inherits the syntactic/structural familiarity of popular modern programming languages while eliminating bias between programmers familiar with particular languages. The following is a program that quickly demonstrates the range of language features available:

```
// this is a one-line comment
	print "this is a string!"
	print 7
	print true                              // boolean true and false support
	print (7 * (2 + 5)) ** 2                // expressions
	print ((1 == 1 && false) || 5 >= 3)     // boolean expressions
	var a = 7                               // variable declaration
	print a
	a = "stringy"                           // variables are dynamically typed
	print a
	while (true) {                          // while loops
	  if (2 != 1) {                         // if conditionals
	    break
	  } else {
	    continue
	  }
	}
	var addx = function(to_add) {           // functions are first class values
	  return function(x) {                  // and are closures
	    return x + to_add
	  }
	}
	var add2 = addx(2)
	print add2(7)                           // gives 9
	var ar = array()                        // an empty array
	ar = insert(ar, 0, "hello")             // insert "hello" at index 0
	insert(ar, 0, "how are you")            // doesn't do anything! No mutation!
	print ar                                // [hello]. Everything is passed by value!
	ar = insert(ar, 0, "how are you")       // Must assign!
	print ar                                // [how are you, hello]
	ar = insert(ar, 0, 55)
	print ar                                // [55, how are you, hello]
	print get(ar, 0)                        // get value at index 0 (55)
	ar = set(ar, 1, "bye")                  // set value at index 1 to bye
	print ar                                // [55, bye, hello]
	ar = remove(ar, 0)                      // remove value at index 0
	print ar                                // [bye, hello]
	print length(ar)                        // length of array, 2
  ```
  
  Quick language notes:
One statement per line.
Variables are dynamically typed, there are 5 basic types: number, string, boolean, function, array
New variables need to be declared with 'var'
Statically scoped
All expressions are evaluated before assignment/function passing. Lazy evaluation is not supported.
Short-circuit evaluation is not currently supported!
Functions are closures and are first class values. There is no syntactic sugar for named function definition, so it has to be done in "var funcname = function() { .." format.
Arrays are manipulated with 6 basic calls:
array() to create a new array
get(arr, index) to get the value at the index
set(arr, index, val) to set the value at the index
insert(arr, index, val) to insert a value at that index
remove(arr, index) to remove the value at that index
length(arr) to get the length of the array
other operations should be derivable from these basic operations.
**Everything is passed by value including arrays**. None of the array manipulation functions actually mutate the argument array but creates and returns a new array
Only single line comments with // are supported
for loops are not supported
