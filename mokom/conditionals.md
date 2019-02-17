# Conditionals

MokoM supports the familiar if-elseif-else conditional structure. The syntax is simple: the **if** keyword followed by a boolean expression enclosed in paranthesis, followed by a code block to execute if the boolean expression evaluates to true. 

Optionally the **elif** keyword can be added at the end of the code block followed by a boolean expression enclosed in paranthesis and then another code block to be executed if the current expression evaluates to true while all previous expressions evaluate to false. 

Also optionally the **else** keyword can be added at the end of the code block followed by a code block to be executed only if all previous expressions evaluated to false. 

A conditional must always begin with an if block, may contain any number of elif blocks before being optionally ended with an else block.

Note that unlike languages like C, it is compulsory for the code blocks to be enclosed with curly bracers, even if it contains only one statement!

Example of valid conditional:

```
if (1 == 0) {
	print "this block won't be executed!"
	print "unfortunately"
} elif (5 <= 4) {
	print "this block won't either"
} else {
	print "this should get printed"
}
```	

Examples of invalid conditionals: 

```
// if block MUST be enclosed in '{' and '}'
if (1 == 0)
	print "this block won't be executed!"

// else block MUST be enclosed in '{' and '}'
if (1 == 0) {
	print "this block won't be executed!"
	print "unfortunately"
}
else
	print "this should (not) get printed"

// else block must be at the end of the conditional!
if (1 == 0) {
	print "this block won't be executed!"
	print "unfortunately"
}
else {
	print "this should (not) get printed"
}
elif (5 <= 4) {
	print "this block won't either"
}
```
