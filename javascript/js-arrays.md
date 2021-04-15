# Arrays

Unfortunately, strings and numbers are not enough for most programming purposes. What is needed are collections of data that we can use efficiently, Arrays.

Arrays are great for:

* Storing data
* Enumerating data, i.e. using an index to find them.
* Quickly reordering data

```javascript
const friends = ['Moe', 'Larry', 'Curly'];
// => ['Moe', 'Larry', 'Curly']
```

Items in an array are stored in sequential order, and indexed starting at `0` and ending at `length - 1`.

```javascript
// First friend
let firstFriend = friends[0];
// => 'Moe'

// Get the last friend
let lastFriend = friends[2]
// => 'Curly'
```

## Pair Exercise: String Manipulation

With your pair, have one person create a variable that equals a comma delimited string with at least four of your favorite foods.

```javascript
const favorites = "noodles,bread,cheese,filet mignon";
```

Have the second person turn that string into an array, then the first person should retrieve the third favorite food from the array.

## Iterating Over Arrays

Often we want to write code that interacts with everything in an array. Let's say we have a list of numbers representing sub-totals on a receipt.

For a moment, let's assume we have four items on our receipt. We could "hard-code" a program to manually add up all of the items:

```javascript
const subTotals = [2.99, 3.00, 2.75, 14.99];
let total = subTotals[0] + subTotals[1] + subTotals[2] + subTotals[3];
```

We say the above example is "hard-coded" because it's brittle. The code assumes there's exactly four items in the array. The code would cause an error if there were less than four items. The code would fail to add anything beyond the first four items in the list. Instead of hard-coding our program we can use a for loop to _iterate_ over the array and calculate a total no matter how many things are in the array!

```javascript
// Make a variable to keep track of the total. Start it at zero.
let total = 0;

// Create a for loop that starts at i = 0, and increments i++
// as long as i is less than the length of the list.
for (let i = 0; i < subTotals.length; i++) {
  // add the subtotal of each item to our total.
  total += subTotals[i];
}
```

Iterating over arrays is very common.

## Pair Exercise: Finding Averages

With your pair, use a for loop to iterate over an array. Calculate the average value of all numbers in the array. Consider how your code would operate on empty arrays, arrays with one value, arrays with two values, and arrays of any length. Test your code on each of the following arrays:

```javascript
const a1 = [];
const a2 = [14];
const a3 = [29, 32];
const a4 = [16, 99, -40];
const a5 = [12, 28, 92, 23, 94, 23, 99, 99, 99, 92];
```

## Array Methods

Arrays come with special methods attached to themselves that allow you to perform common operations.

### Adding and Removing Single Items

* `.push('element')` - add an element to the end of an array
* `.pop()` - remove and return the last element in an array
* `.shift()` - remove an element off the front of the array
* `.unshift(3)` - add an element to the beginning of an array

### Reorder an array:
* `.sort()` - sort the elements in an array 
* `.reverse()` - reverse the array

### Other useful methods
* `.concat([1, 2])` - concatenate two arrays together
* `.slice(1, 3)` - return a copy of a portion of an array
* `.splice()` - alter an array by adding or removing elements
  * [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
* `.join(' ')` - take an array and join the elements together as a string
