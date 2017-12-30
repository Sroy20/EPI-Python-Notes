# EPI-Python-Notes
I have been learning lots of new Python features and programming techniques while reading the EPI Python book. This is my attempt to jot them down question-wise.

## Table of Contents

- [Chapter 5: Arrays](#chapter-5-arrays)
- [Chapter 6: String](#chapter-6-strings)
- [Chapter 10: Heaps](#chapter-10-heaps)

## Chapter 5: Arrays

### Problem 5.2: Increment an arbitrary precision integer

Note the phrase "arbitrary precision". That rules out the method of converting them into integers and adding them since overflow error might occur in some languages.

This problem is a simple, however, note the slick way of adding a 1 in the front when an extra digit has to be added (for example, for 99, 999, etc.). In contrast to insert(0, 1) which takes O(n) time, the showed method is O(1). 

### Problem 5.3: Multiply two arbitrary precision integers

Note how the sign of the result is handled and how the size of the list is initialized. At the end, the leading zeros are removed by using generator and next(). Note the trick to obtain all the remaining items instead of just the next one.

The same problem can be slightly modified by giving the input as strings for example as seen in [Leetcode](https://leetcode.com/problems/multiply-strings/description/). In this case, conversion from characters to integers and vice versa have to properly taken care off. Moreover, remember that str.join function doesn't automatically convert digits into strings.

## Chapter 6: Strings

### Problem 6.1: Interconvert strings and integers

Note how special care has to be taken for handling negative numbers and zeros.

Furthermore, note the method of converting one character to one digit and vice-versa.

One-character to one-digit: string.digits.index(c)

One-digit to one-character: chr(ord('0')+i)

Also note the beautiful usage of [functools.reduce()](https://docs.python.org/3/library/functools.html#functools.reduce) fuction. This function takes three inputs: a function, an iterable, an initializer and accumulates to return one value.

### Problem 6.2: Base conversion

Base conversion is a more general form and combination of the two programs of 6.1. Nevertheless, few things to note:

The check at the middle of the program that determines whether the input number is negative or not should check for a leading '-' in the input string and not check whether the converted decimal is postive ot negative. This is to handle the -0 situation.

Also note how the string.hexdigits is used to get the digit after base conversion. No need to maintain a dictionary. And upper() has to been used string in string.hexdigits after the numerals, lower case numbers are there.

The time complexity is quite interesting.











## Chapter 10: Heaps

### Problem 10.1: Merge sorted files/arrays/lists

First, note the usage of enumerate to get both the index and the value at the index. 

Next, note the usage of the [iter()](https://docs.python.org/3/library/functions.html#iter) and [next()](https://docs.python.org/3/library/functions.html#next) function. 

Also see how a default value of None has been added to the next() function. This is done not only to avoid the StopIteration exception but also to conveniently skip adding items to the heap when a list/array is exhausted. As more and more arrays get exhausted, the length of min_heap reduces until it becomes 0. At this point the merge is complete!

Another general take away from this solution is that this allows an efficient way to handle simultaneously iterating through multiple arrays/lists.

Note the Pythonic solution using heapq.merge. This might be handy in other situations where this problem becomes a sub-problem.

Also checkout the Leetcode problem which asks to [merge sorted linked lists](https://leetcode.com/problems/merge-k-sorted-lists/). The same principles can be used there without explicitly creating the iterators.

### Problem 10.3: Sort an almost sorted array

Note the awesome usage of the [islice](https://docs.python.org/3/library/itertools.html#itertools.islice) function from itertools. Particularly note how to extract the first k and all but first k elements.

The solution to this problem is probably wrong. The second for loop will be:

_for x in itertools.islice(nums, k, None)_

Otherwise the smallest values from first k elements are extracted twice.







