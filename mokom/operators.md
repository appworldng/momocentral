# Operators

The following is a table of supported operators, ordered by descending precedence:

<table border="1" class="table table-striped table-bordered">
    <tr>
      <th>Operator</th>
      <th width="300px">Type information</th>
      <th>Description</th>
    </tr>
    <tr>
      <td>!</td>
      <td>!boolean<br />produces a boolean</td>
      <td>Not operator. Inverts the truth of a given boolean value</td>
    </tr>
    <tr>
      <td>**</td>
      <td>number1 ** number2<br />produces a number</td>
      <td>Power operator. Produces number1 to the power of number2</td>
    </tr>
    <tr>
      <td>%</td>
      <td>number1 % number2<br />produces a number</td>
      <td>Modulo operator. Produces number1 modulo number2</td>
    </tr>
    <tr>
      <td>/</td>
      <td>number1 / number2<br />produces a number</td>
      <td>Division operator. Produces number1 divided by number2</td>
    </tr>
    <tr>
      <td>*</td>
      <td>number1 * number2<br />produces a number</td>
      <td>Multiplication operator. Produces number1 multiplied by number2</td>
    </tr>
    <tr>
      <td>-</td>
      <td>number1 - number2<br />produces a number</td>
      <td>Subtraction operator. Produces number1 minus number2</td>
    </tr>
    <tr>
      <td>+</td>
      <td>number1 + number2<br />produces a number</td>
      <td>Addition operator. Produces number1 plus number2</td>
    </tr>
    <tr>
      <td>+</td>
      <td>string1 + string2<br />produces a string</td>
      <td>Concatenation operator. Produces string1 concatenated with string2</td>
    </tr>
    <tr>
      <td>+</td>
      <td>number1 + string2<br />produces a string</td>
      <td>Concatenation operator. Produces number1 coerced to a string concatenated with string2</td>
    </tr>
    <tr>
      <td>+</td>
      <td>string1 + number2<br />produces a string</td>
      <td>Concatenation operator. Produces string1 concatenated with number2 coerced to a string</td>
    </tr>
    <tr>
      <td>&gt;=</td>
      <td>number1 &gt;= number2<br />produces a boolean</td>
      <td>Greater-than-or-equal operator. Produces boolean true if number1 is greater than or equal to number 2, false otherwise</td>
    </tr>
    <tr>
      <td>&gt;</td>
      <td>number1 &gt; number2<br />produces a boolean</td>
      <td>Greater-than operator. Produces boolean true if number1 is greater than number 2, false otherwise</td>
    </tr>
    <tr>
      <td>&lt;=</td>
      <td>number1 &lt;= number2<br />produces a boolean</td>
      <td>Less-than-or-equal operator. Produces boolean true if number1 is less than or equal to number 2, false otherwise</td>
    </tr>
    <tr>
      <td>&lt;</td>
      <td>number1 &lt; number2<br />produces a boolean</td>
      <td>Less-than operator. Produces boolean true if number1 is less than number 2, false otherwise</td>
    </tr>
    <tr>
      <td>!=</td>
      <td>value1 != value2<br />produces a boolean</td>
      <td>Not-equal operator. If value1 and value2 are the same type and <strong>are not arrays</strong>, produces boolean true if they are also not of the same value, false otherwise.
      If they are not of the same type (<strong>including arrays</strong>), produces boolean true.</td>
    </tr>
    <tr>
      <td>==</td>
      <td>value1 == value2<br />produces a boolean</td>
      <td>Equal operator. If value1 and value2 are the same type and <strong>are not arrays</strong>, produces boolean true if they are also of the same value, false otherwise.
      If they are not of the same type (<strong>including arrays</strong>), produces boolean false.</td>
    </tr>
    <tr>
      <td>&&</td>
      <td>boolean1 && boolean2<br />produces a boolean</td>
      <td>Boolean And operator. Produces boolean true if boolean1 and boolean2 are both true, false otherwise</td>
    </tr>
    <tr>
      <td>||</td>
      <td>boolean1 || boolean2<br />produces a boolean</td>
      <td>Boolean Or operator. Produces boolean true if boolean1 is true, or if boolean2 is true, or if both boolean1 and boolean 2 are true, false otherwise.
      <strong>Expressions on both side of the || operator will always be evaluated, short-circuit evaluation is not supported</strong></td>
    </tr>
    <tr>
      <td>=</td>
      <td>variable1 = expression2</td>
      <td>Assignment operator. Assigns the evaluated value of expression2 to variable1. Variable1 must be a previously declared variable</td>
    </tr>
  </table>
  
  Of course, like with most familiar languages, expressions enclosed in paranthesis '(...)' are always given highest priority and are evaluated first.

Again, all expressions are evaluated before assignment/function passing. Lazy evaluation is not supported. Both sides of the || operator will also always be evaluated - short-circuit evaluation is not supported.
