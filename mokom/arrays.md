# Arrays

Arrays are supported as dynamic lists in the spirit of modern scripted languages (cf. fixed-sized memory arrays in languages like C). Arrays are created and manipulated with a minimal set of built in functions, from which more complex operations can be derived. The following is a list of built in functions with description.

<table class="table table-striped table-bordered" border="1">
  <tr>
    <th width="300px">Function signature</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>array(element1, element2, ...)</td>
    <td>Creates and returns an array, can take arbitrary number of arguments. All arguments
    are inserted into the returned array in order.
    If no arguments is given an empty array is returned</td>
  </tr>
  <tr>
    <td>get(array, index)</td>
    <td>Retrieves and returns the value at the given index in the array</td>
  </tr>
  <tr>
    <td>set(array, index, val)</td>
    <td>Sets the value at the given index in the array to val, and returns the array</td>
  </tr>
  <tr>
    <td>insert(array, index, val)</td>
    <td>Inserts the given value val at the given index in the array. All existing indices
    in the array after 'index' will be pushed back by one. Returns the result array.</td>
  </tr>
  <tr>
    <td>remove(array, index)</td>
    <td>Removes the element at the given index. All existing indices after 'index' will
    be brought forward by one. Returns the result array.</td>
  </tr>
  <tr>
    <td>length(array)</td>
    <td>Returns the number of elements currenty in the array.</td>
  </tr>
</table>

Note again that like everything else, these functions' arguments are passed by value! **So none of these functions actually mutate an existing array**. Instead, functions like 'insert' and 'remove' return a new array after applying their intended effect.

```
var ar1 = array()                       // empty array
var ar2 = array(1,2,false,"hello")      // array with 4 elements
var func1 = function(x) {
  return x
}
ar2 = set(ar2, 0, func1)                // ar2 is now [function,2,false,hello]
set(ar2, 1, "foobar")                   // ar2 is unchanged! set doesn't mutate!
ar2 = set(ar2, 1, "foobar")             // ar2 is now [function,foobar,false,hello]
print get(ar2, 1)                       // foobar
print insert(ar1, 0, "hi")              // [hi]
print ar1                               // [] - insert doesn't mutate!
ar1 = insert(ar1, 0, "hi")
print ar1                               // [hi]
print remove(ar1, 0)                    // []
print ar1                               // [hi] - remove doesn't mutate
ar1 = remove(ar1, 0)
print ar1                               // []
```
