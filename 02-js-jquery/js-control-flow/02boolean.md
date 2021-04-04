# Boolean Expressions

## = vs == vs === 

### Assignment Operator (=)

Recall the single equals, or "assignment operator", which assigns values to variable. Note that there is not comparison involved in assignment statements.

```js
var x = 3;
var a = b = 5;
```

That second line sets assigns both `a` and `b` to the value `5`. 
This demonstrates that the assignment operator
* returns the value that is assigned 
* _right-to-left_ associativity, meaning `a = b = 5` is the same things as `a = (b = 5)`
More on this [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Associativity).

***Note: almost all operators have left-to-right associativity, this is a rarity***

### Equality Operator (==)

The equality operator aka double equals (`==`) is used to compare two values. In english, it translates to [blank] "is the same value as" [blank].

```js
3 == 3
//true

4 == 3
//false
```

The equality operator allows type coercion which means that it doesn't care if the values are different types.

```js
3 == "3"
//true

0 == false
//true

1 == true
//true
```

### Identity Operator (===)

The identity operator aka triple equals works exactly like the equality operator, except it cares about type! Because it is a stricter comparison, it is generally preferred over the equality operator. 

```js
3 === 3
//true

4 === 3
//false

3 === "3"
//false
```

#### How to remember which is which:
* increasing strictness
* "equality" implies inclusive
* "identity implies exclusive/uniqueness

#### Exercise: Venn diagram
Draw a Venn diagram (two circles that have some overlap). Label one circle "equality ==", the other circle "identity ===", and the overlapping section will represent both. Place each of the following pairs of values into one of the three sections according to which operator will yeild a "true" output.

```js
true
"true"

5
"5"

["x"]
"x"
```
What do you notice about the equality-only section?

### Additional Boolean Operators

There are also ways to check if a value is greater than, greater than or equal to, less than, less thanor equal to, or not equal to another value. Note that the "not" (!) always takes the place of once set of equal bars. So, "!=" is the negation of "==" and "!==" is the negation of "===", (and "!===" is just not a thing).

```js
4 > 5
//false

4 < 5
//true

4 >= 5
//false

5 <= 5
//true

4 != 5
//true

5 !== "5"
//true
```

### Logical Operators

Lastly, we can combine different boolean expressions by using logic operators.

* `&&` - and
* `||` - or
* `!` - not

```js
(4 > 5) && (5 == 5)
//false, the "and" operator requires both statements to be true

(4 > 5) || (5 == 5)
//true, the "or" operator requires at least one of the statements to be true

!(4 > 5) && (5 == 5)
//true, the "not" operator negates the first expression (!false ends up being true)
```

We'll be using these expressions throughout the course. If you find that an expression evaluates to a value that you weren't expecting, check out the [operator precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table) to see what order the expression is being evaluated. This is like the order of operations, or PEMDAS of javascript. 

#### Class Exercise

What is the result of this statement? Tip: Evaluate each of the expressions between the operators first, and replace them with true or false, then evaluate the entire statement.

```js
!(5 === "5") && (6 > 5) && (1 >= 0)
```

#### Partner Exercise

Turn to your partner and discuss the result of this statement:

```js
(5 < 4) || !(3 == 3) && true
```
