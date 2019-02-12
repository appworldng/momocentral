# momocentral
A set of programming problems &amp; answers written in the MokoM language, (an invented programming language). 

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
