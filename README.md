# momocentral
A set of programming problems I cracked from the momocentral.com website written in the MokoM language, (an invented programming language). 

## Question 1 - Test Array

Write a function called **test_array** that accepts an array and tests if the last element of the array is greater than 10. If so, the function should return the value of the last element of the array, else it should return boolean false.

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

Suppose that a set of numeric data is stored in an array. You are given a bunch of such sets (so you have an array of array of numbers). For each set of numbers in the array, you need to compute the sum of all the numbers it contains. However, if any of the numbers are 0 or less, the set should be considered invalid and skipped. Your task is to write a function **summarize** that will return an array of summed values for every valid set in order, while skipping the invalid ones.

For example, for the following data:
```
array(
  array(1,2,3,4),
  array(2,3,4,5),
  array(5,6,-3),
)
```

Your **summarize** function should return:
```
array(10,14)
```

Where 10 is the sum of [1,2,3,4], 14 is the sum of [2,3,4,5], etc. The third array is skipped because it contains a number that is 0 or less, and is thus considered invalid.

Write the **summarize** function that accepts an array of arrays and processes the data in the arrays as described above and returns the result array.

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

## Answer 2 - Summarize

To solve this problem, we would create 2 custom functions of our own verifyArrayAsValid() and sumUpArray()
```
var summarize = function(array) {
	var i = 0
	var sum = 0
	var newArray = array()   
	while(i < length(array)) {
		if(verifyArrayAsValid(get(array,i))) {
			sum = sumUpArray(get(array,i))
			newArray = insert(newArray, length(newArray), sum)
		}
		i = i + 1
	}
	return newArray
}

var verifyArrayAsValid = function(array) {
	var i = 0
	var status = true
	while(i < length(array)) {
		if(get(array,i) <= 0) {
			status = false
		}
		i = i + 1
	}
	return status
}

var sumUpArray = function(array) {
	var i = 0
	var sum = 0
	while(i < length(array)) {
		sum = sum + get(array,i)
		i = i + 1
	}
	return sum
}
```

## Question 3 - Bejeweled Chains

Bejeweled, for those unacquainted with it, is a popular game that consists of a square/rectangular grid of different-colored jewels. The game is played by swapping the positions of jewels that are horizontally or vertically adjacent to create chains of three or more jewels of the same color. You can refer to wikipedia for further gameplay details.

We can represent a bejeweled game grid in MokoM with an array of array of numbers, with different numbers representing different colors. Consider the following board for example:
```
array(
  array( 3 , 3 , 3 , 4 , 1 , 2 ),
  array( 0 , 0 , 3 , 2 , 4 , 4 ),
  array( 4 , 0 , 0 , 2 , 2 , 1 ),
  array( 1 , 3 , 4 , 2 , 4 , 0 ),
  array( 0 , 1 , 0 , 2 , 0 , 1 ),
  array( 2 , 2 , 2 , 4 , 1 , 3 ),
)
```

As previously noted, the objective of the game is to form chains consisting of three or more jewels of the same color that are either horizontally or vertically adjacent. The example game board above contains 3 such chains, highlighted in red below:
```
array(
  array( 3 , 3 , 3 , 4 , 1 , 2 ),
  array( 0 , 0 , 3 , 2 , 4 , 4 ),
  array( 4 , 0 , 0 , 2 , 2 , 1 ),
  array( 1 , 3 , 4 , 2 , 4 , 0 ),
  array( 0 , 1 , 0 , 2 , 0 , 1 ),
  array( 2 , 2 , 2 , 4 , 1 , 3 ),
)
```

Your task in this question is to write a function **count_chains** that accepts a bejeweled game board as described above (an array of array of numbers) and then counts and returns the number of chains in the given game board. Each continuous horizontal or vertical chain counts as a single chain, regardless of length. However if a horizontal chain intersects a vertical chain, they still count as separate chains. 

Some examples:
```
array(
  array( 0 , 3 , 3 ),
  array( 0 , 0 , 0 ),
  array( 0 , 1 , 4 )
)
```
The above has 2 chains (first column and second row).

```
array(
  array( 3 , 3 , 3 , 3 , 3 ),
  array( 0 , 0 , 1 , 2 , 1 ),
  array( 0 , 1 , 4 , 3 , 2 )
)
```
The above has one chain (first row)

You may assume that you are always given a proper game board: ie. an array of equal-length arrays of only integer values. The length and width of the board can however be arbitrary, the number of different colors of jewels is also arbitrary.

Your final solution should just define the **count_chains** function. You don't need to call it in any way, and you should not print anything. You may however define any number of helper functions to break down the task in a sensible way.

Example code the evaluator would run:
```
print count_chains(array(array( 0 , 3 , 3 ),array( 0 , 0 , 0 ),array( 0 , 1 , 4 )))
```

Example expected output:
```
2
```

## Answer 3 - Bejeweled Chains

To solve this type of complex problem, we would have to use 2 custom helper functions - countCompleteChains() and changeArrayOrientation(). The first helper function helps us count complete chains while the second helper function helps us swap the array structure from "m x n" array to an "n x m" array arrangment. 
```
var count_chains = function(array) {
	var i = 0
	var numberOfChains = 0
	
	//Count Chains for original orientation
	while(i < length(array)) {
		numberOfChains = numberOfChains + countCompleteChains(get(array,i))
		i = i + 1
	}
	
	//Change Array's Orientation from Horizontal to Vertical
	array = changeArrayOrientation(array)
	
	//Count Chains for new array orientation
	i = 0
	while(i < length(array)) {
		numberOfChains = numberOfChains + countCompleteChains(get(array,i))
		i = i + 1
	}
	return numberOfChains
}

var countCompleteChains = function(array) {
	var i = 0
	var j = 0
	var currentNumber = 0
	var numberOfSameItems = 1
	var numberOfChains = 0
	while(i < length(array)) {
		currentNumber = get(array,i)
		j = i + 1
		if(j != length(array)) {
			if(currentNumber == get(array,j)) {
				numberOfSameItems = numberOfSameItems + 1
				if(numberOfSameItems == 3) {
					numberOfChains = numberOfChains + 1
				}
			} else {
                //Once the number is not the same reset numberOfSameItems
				numberOfSameItems = 1
			}
		}
		i = i + 1
	}
	return numberOfChains
}

var changeArrayOrientation = function(array) {
	var i = 0
	var k = 0
	var currentArray = array()
	var intermediateArray = array()
	var childArray = get(array, 0)
	var childArray_length = length(childArray)

        //Transfer item of each subarray into intermediate array for swapping
	while(i < length(array)) {
		currentArray = get(array, i)
		var j = 0
		while(j < length(currentArray)) {
			intermediateArray = insert(intermediateArray, k, get(currentArray, j))
			k = k + 1
			j = j + 1
		}
		i = i + 1
	}
	

        //Perform the swap 
	var l = 0
	var swappedArray = array()
	while(l < childArray_length) {
		var dynamicArray = array()
		var m = 0
		var n = l
		while(n < length(intermediateArray)) {
			dynamicArray = insert(dynamicArray, m, get(intermediateArray, n))
			n = n + childArray_length
			m = m + 1
		}
		swappedArray = insert(swappedArray, l, dynamicArray)
		l = l + 1
	}
	return swappedArray
}
