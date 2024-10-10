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

```
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

```
const min = (x, y) => x < y ? x : y;
```

# chapter 3 Exercises

## Recursion

We’ve seen that % (the remainder operator) can be used to test whether a number is even or odd by
using % 2 to see whether it’s divisible by two. Here’s another way to define whether a positive whole
number is even or odd:
Zero is even.
One is odd.
For any other number N, its evenness is the same as N –2.
Define a recursive function isEven corresponding to this description. The function should accept a
single parameter (a positive, whole number) and return a Boolean.
Test it on 50 and 75. See how it behaves on –1. Why? Can you think of a way to fix this?

## Solution

```
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

## Exercises

The sum of a range
The introduction of this book alluded to the following as a nice way to compute
the sum of a range of numbers:
console.log(sum(range(1, 10)));
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

```
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

```
```
