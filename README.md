# momocentral
A set of programming problems &amp; answers written in the MokoM language, (an invented programming language). 

## Question 1 - Test Array

Write a function called 'test_array' that accepts an array and tests if the last element of the array is greater than 10. If so, the function should return the value of the last element of the array, else it should return boolean false.

So **test_array(array(1,2,3))** should return **false**, and **test_array(array(12,23))** should return **23**.

You may assume that your function will always be given a non-empty array, and you may assume that every element in the array is an integer.

Your final solution should just define the test_array function. You don't need to call it in any way, and you should not print anything.

## Answer 1 - Test Array
To solve this problem, we would have to make use of the proprietary length and get functions like so: 
```
var test_array = function(array) {	
	var lastvalue
	var index = length(array) - 1
	lastvalue = get(array, index)
	if(lastvalue > 10) {
		return lastvalue
	} else {
		return false
	}
}
```

## Question 2 - Summarize

A common programming task is to process a set of data kept in a particular format to yield a parsed/summarized result. Though MokoM has very little support for data structures, we can make a simple instance of such a problem using just arrays.

Suppose that a set of numeric data is stored in an array. You are given a bunch of such sets (so you have an array of array of numbers). For each set of numbers in the array, you need to compute the sum of all the numbers it contains. However, if any of the numbers are 0 or less, the set should be considered invalid and skipped. Your task is to write a function 'summarize' that will return an array of summed values for every valid set in order, while skipping the invalid ones.

For example, for the following data:
```
array(
  array(1,2,3,4),
  array(2,3,4,5),
  array(5,6,-3),
)
```

Your 'summarize' function should return:
```
array(10,14)
```

Where 10 is the sum of [1,2,3,4], 14 is the sum of [2,3,4,5], etc. The third array is skipped because it contains a number that is 0 or less, and is thus considered invalid.

Write the 'summarize' function that accepts an array of arrays and processes the data in the arrays as described above and returns the result array.

You may assume that your function is always given an array of arrays of only numeric values. Your function should not break in the case that any of the arrays are empty. Note that if a data set array is empty, it still counts as valid since it does not contain a number that is 0 or less. The sum of an empty array should simply be 0!

Your final solution should just define the summarize function. You don't need to call it in any way, and you should not print anything. You may and are encouraged to define helper functions to help you divide the problem logically.

Example code the evaluator would run:
```
print summarize(array(array(1,2,3,4),array(2,3,4,5),array(5,6,-3)))
```

Example expected output:
```
[10,14]
```
