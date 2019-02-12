# momocentral
A set of programming problems &amp; answers written in the MokoM language, (an invented programming language). 

## Question 1 - Test Array

Write a function called 'test_array' that accepts an array and tests if the last element of the array is greater than 10. If so, the function should return the value of the last element of the array, else it should return boolean false.

So test_array(array(1,2,3)) should return false, and test_array(array(12,23)) should return 23.

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
