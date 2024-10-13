# Chapter 2 Exercises

## Looping a triangle

Write a loop that makes seven calls to console.log to output the following triangle:
```
#
##
###
####
#####
######
#######
```

## Solution

```js
for (let i = 1; i < 8; i++) {
	console.log('#'.repeat(i));
}

```

## FizzBuzz

Write a program that uses console.log to print all the numbers from 1 to 100, with two exceptions.
For numbers divisible by 3, print "Fizz" instead of the number, and for numbers divisible by 5 (and
not 3), print "Buzz" instead.

When you have that working, modify your program to print "FizzBuzz" for numbers that are
divisible by both 3 and 5 (and still print "Fizz" or "Buzz" for numbers divisible by only one of those).
(This is actually an interview question that has been claimed to weed out a significant percentage
of programmer candidates. So if you solved it, your labor market value just went up.)

## Soution

```js
for (let i = 1; i < 101; i++) {
	if (i % 15 == 0) {
		console.log("fizzbuzz");
	} else if (i % 3 == 0) {
		console.log("fizz");
	} else if (i % 3 == 0) {
		console.log("buzz");
	} else {
		console.log(i);
	}
}
```


## Chessboard

Write a program that creates a string that represents an 8×8 grid, using new-line characters to
separate lines. At each position of the grid there is either a space or a # character. The characters
should form a chessboard.

Passing this string to console.log should show something like this:

```
 # # # #
# # # #
 # # # #
# # # #
 # # # #
# # # #
 # # # #
# # # #
```

When you have a program that generates this pattern, define a binding size = 8 and change the
program so that it works for any size, outputting a grid of the given width and height.

## Solution

```js
const board_size = 8;
let board_string = "";

for (let i = 0; i < board_size; i++) {
	for (let j = 0; j < board_size; j++) {
		if (((i + j) % 2) === 0) {
			board_string = board_string + '#';
		} else {
			board_string = board_string + ' ';
		}
	}
	board_string = board_string + '\n';
}

console.log(board_string);
```

# Chapter 3 Exercises

## Minimum

Chapter 2 introduced the standard function Math.min, which returns its smallest argument (see
“Return Values” on page 27). We can build something like that now. Write a function min that takes
two arguments and returns their minimum.

## Solution

```js
const min = (num1, num2) => {
	if (num1 < num2) {
		return num1
	} else {
		return num2
	}
}
```

## Chessboard

Write a program that creates a string that represents an 8×8 grid, using new-line characters to
separate lines. At each position of the grid there is either a space or a # character. The characters
should form a chessboard.
Passing this string to console.log should show something like this:

```
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
 # # # #
# # # # 
```

When you have a program that generates this pattern, define a binding size = 8 and change the
program so that it works for any size, outputting a grid of the given width and height.

## Solution

```js
const size = 8;
let board = "";

for (let i = 1; i <= size; i++) {
	for (let j = 1; j <= size; j++) {
		if ((i+j) % 2 == 0) {
			board = board + ' ';
		} else {
			board = board + '#';
		}
	}
	board = board + '\n';
}


console.log(board);
```

## Minimum

Chapter 2 introduced the standard function Math.min, which returns its smallest argument (see
“Return Values” on page 27). We can build something like that now. Write a function min that takes
two arguments and returns their minimum.

## Solution

```js
const min = (x, y) => x < y ? x : y;
```

# chapter 4 Exercises

## Recursion

We’ve seen that % (the remainder operator) can be used to test whether a number is even or odd by
using % 2 to see whether it’s divisible by two. Here’s another way to define whether a positive whole
number is even or odd:

- Zero is even.
- One is odd.

For any other number N, its evenness is the same as N –2.
Define a recursive function isEven corresponding to this description. The function should accept a
single parameter (a positive, whole number) and return a Boolean.
Test it on 50 and 75. See how it behaves on –1. Why? Can you think of a way to fix this?

## Solution

```js
const is_even = (x) => {
	if (x == 0) {
		return true;
	} if (x == 1) {
		return false;
	} else {
		return is_even(x - 2);
	}
}

console.log(is_even(11));
```

## Bean Counting

You can get the Nth character, or letter, from a string by writing "string"[N]. The returned value will
be a string containing only one character (for example, "b"). The first character has position 0, which
causes the last one to be found at position string.length - 1. In other words, a two-character string has
length 2, and its characters have positions 0 and 1.

Write a function countBs that takes a string as its only argument and returns a number that
indicates how many uppercase “B” characters there are in the string.

Next, write a function called countChar that behaves like countBs, except it takes a second argument
that indicates the character that is to be counted (rather than counting only uppercase “B”
characters). Rewrite countBs to make use of this new function.

## Solution

```js
const countChar = (string, char) => {
	let charCount = 0;
	for (let i = 0; i < string.length; i++) {
		if (string[i] === char) {
			charCount = charCount + 1;
		}
	}
	return charCount;
}

const countChar2 = (string, char) => {
	return string.split('').filter(c => c === char).length;
}
```

# Chapter 4 Exercises

## The sum of a range

The introduction of this book alluded to the following as a nice way to compute
the sum of a range of numbers:

``` js
console.log(sum(range(1, 10)));
```

Write a range function that takes two arguments, start and end, and returns
an array containing all the numbers from start up to and including end.
Next, write a sum function that takes an array of numbers and returns the
sum of these numbers. Run the example program and see whether it does
indeed return 55.

As a bonus assignment, modify your range function to take an optional third
argument that indicates the “step” value used when building the array. If no
step is given, the elements should go up by increments of one, corresponding
to the old behavior. The function call range(1, 10, 2) should return [1,
3, 5, 7, 9]. Make sure this also works with negative step values so that
range(5, 2, -1) produces [5, 4, 3, 2].

## Solution

```js
const my_range = (start, end, step = 1) => {
	result = []
	if (step === 0) {
		throw new Error("step cannot be zero.");
	} if (step > 0) {
		for (let i = start; i <= end; i += step) {
			result.push(i);
		}
	} else {
		for (let i = end; i >= end; i += step) {
			result.push(i);
		}
	}
	return result;
}


const my_sum = (list) => {
	let total = 0;
	for (const elem of list) {
		total = total + elem;
	}
	return total;
}

console.log(my_sum(my_range(1, 10)));
```

## Reversing an array

Arrays have a reverse method that changes the array by inverting the order in
which its elements appear. For this exercise, write two functions, reverseArray
and reverseArrayInPlace. The first, reverseArray, should take an array as its
argument and produce a new array that has the same elements in the inverse
order. The second, reverseArrayInPlace, should do what the reverse method
does: modify the array given as its argument by reversing its elements. Neither
may use the standard reverse method.
Thinking back to the notes about side effects and pure functions in the
previous chapter, which variant do you expect to be useful in more situations?
Which one runs faster?

```js
const reverseArrayInPlace = (array) => {
	for (let i = 0; i < Math.floor(array.length) / 2; i++) {
		let temp = array[i];
		array[i] = array[array.length - 1 - i];
		array[array.length - 1 - i] = temp;
	}
}

const reverseArray = (array) => {
	let result = [];
	for (let i = array.length - 1; i >= 0; i--) {
		result.push(array[i]);
	}
	return result;
}
```


## A list

As generic blobs of values, objects can be used to build all sorts of data struc-
tures. A common data structure is the list (not to be confused with arrays).
A list is a nested set of objects, with the first object holding a reference to the
second, the second to the third, and so on:

``` js
let list = {
	value: 1,
	rest: {
		value: 2,
		rest: {
			value: 3,
			rest: null
		}
	}
};
```

The resulting objects form a chain, as shown in the following diagram:

```
value: 1
rest:
value: 2
rest:
value: 3
rest: null
```

A nice thing about lists is that they can share parts of their structure. For
example, if I create two new values {value: 0, rest: list} and {value: -1,
rest: list} (with list referring to the binding defined earlier), they are both
independent lists, but they share the structure that makes up their last three
elements. The original list is also still a valid three-element list.

Write a function arrayToList that builds up a list structure like the one
shown when given [1, 2, 3] as argument. Also write a listToArray function
that produces an array from a list. Add the helper functions prepend, which
takes an element and a list and creates a new list that adds the element to the
front of the input list, and nth, which takes a list and a number and returns
the element at the given position in the list (with zero referring to the first
element) or undefined when there is no such element.

If you haven’t already, also write a recursive version of nth.

``` js
const arrayToList = (array) => {
	let list = null;
	for (let i = array.length - 1; i >= 0; i--) {
		list = { value: array[i], rest: list };
	}
	return list;
}

const listToArray = (list) => {
	array = [];
	for (let node = list; node; node = node.rest) {
		array.push(node.value);
	}
	return array;
}

const prepend = (value, list) => {
	return { value: value, rest: list }
}

const nth = (n, list) => {
	let i = 0;
	for (let node = list; node; node = node.rest) {
		if (i === n) {
			return node.value;
		}
		i = i + 1;
	}
	return undefined;
}

const nthRecursive = (n, list) => {
	if (n === 0) {
		return list.value;
	} else {
		return nthRecursive(n - 1, list.rest)
	}
}
```

## Deep comparison
The == operator compares objects by identity, but sometimes you’d prefer to
compare the values of their actual properties.

Write a function deepEqual that takes two values and returns true only
if they are the same value or are objects with the same properties, where
the values of the properties are equal when compared with a recursive call to
deepEqual.

To find out whether values should be compared directly (using the === op-
erator for that) or have their properties compared, you can use the typeof
operator. If it produces "object" for both values, you should do a deep com-
parison. But you have to take one silly exception into account: because of a
historical accident, typeof null also produces "object".
The Object.keys function will be useful when you need to go over the prop-
erties of objects to compare them

```js
function deepEqual(a, b) {
  if (a === b) return true;

  if (a == null || typeof a != "object" ||
      b == null || typeof b != "object") {
	  return false;
  }

	let keysA = Object.keys(a)
	let keysB = Object.keys(b);

	if (keysA.length != keysB.length) {
		return false;
	}

  for (let key of keysA) {
      if (!keysB.includes(key) || !deepEqual(a[key], b[key])) {
		  return false;
	  }
  }

  return true;
}

let obj = {here: {is: "an"}, object: 2};
console.log(deepEqual(obj, obj));
// → true
// console.log(deepEqual(obj, {here: 1, object: 2}));
// // → false
// console.log(deepEqual(obj, {here: {is: "an"}, object: 2}));
// // → true


(add-to-list 'exec-path "./node_modules/.bin")
```

# Chapter 5

## Flattening
Use the reduce method in combination with the concat method to “flatten”
an array of arrays into a single array that has all the elements of the original
arrays.

``` js
const flatten = (arr) => {
  return arr.reduce((accumulator, currentArr) => {
	return accumulator.concat(currentArr);
  }, [])
}
```

## Your own loop
Write a higher-order function loop that provides something like a for loop
statement. It should take a value, a test function, an update function, and
a body function. Each iteration, it should first run the test function on the
current loop value and stop if that returns false. It should then call the body
function, giving it the current value, and finally call the update function to
create a new value and start over from the beginning.
When defining the function, you can use a regular loop to do the actual
looping.

``` js
function loop(initialValue, testFn, updateFn, bodyFn) {
  for (let value = initialValue; testFn(value); value = updateFn(value)) {
    bodyFn(value);
  }
}
```

