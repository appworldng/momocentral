# Loops

Only while loops are presently supported (note that one can also create loop behavior with recursive functions). The syntax is simple: the while keyword followed by a boolean expression enclosed in paranthesis, and then a code block to be repeatedly executed while the boolean expression evaluates to true.

The break and continue keywords can be used at any time within the loop block as an individual statement. break immediately exits the current loop, whereas continue starts the loop block again from the beginning ignoring any statements below it.

Again it is compulsory for the code blocks to be enclosed with curly bracers, even if it contains only one statement!

```
  var i = 0
	while (i != 5) { // loops 5 times printing 0 through 4
	  print i
	  i = i + 1
	}
	while (true) {
	  print i
	  i = i - 1
	  if (i == 0) {
	    break
	  }
	}

	// The following is invalid! Block needs to be enclosed in '{' and '}' even if
	// there is only one statement!
	// while (true)
	//   print "zz"
```
