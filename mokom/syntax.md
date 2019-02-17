# Basic Syntax

A program is basically a collection of statements. All statements except while, if/elif/else and function definitions should be single-line (ie. terminated by newline). Extraneous spaces and blank lines are ignored.

Only single-line comments are supported. They are denoted by '//'. Anything to the right of a '//' is considered a comment and ignored by the interpreter

Scoped code blocks for while, if/elif/else and function definitions are delimited by curly bracers '{' and '}' a'la C-style languages.

Examples of valid code blocks:

```
if (1 == 1) {
	  print "this is a"
	  print "code block"
	}

	if (1 == 1) { print "this is a"
	  print "code block"
	}

	if (1 == 1)
	{
	  print "this is a"

	  print "code block"
	}

	if (1 == 1)
	{ print "hello"
	} elif (2 == 1) {
	  print "hi again"
	}
	else
	{
	  print "else clause"
	}

	var f = function(n)
	  {
	  print n
	  print "Haha"
	  }
 ```
