## Week 3 Outline
### Chapter 3 - Built-in Data Structures, Functions, and Files

#### Tuple
* Fixed-length, immutable sequence of Python objects.
```
In [1]: tup = (1, 2, 3)
In [2]: tup
In [3]: ((1, 2, 3))
```
* Can convert any sequence or iterator to a tuple by invoking tuple:
```
In[5]: tup = tuple('string')
In[6]: tup
In[7]: ('s', 't', 'r', 'i', 'n', 'g')
```
* Elements can be accessed with square brackets []. Python elements are 0-indexed. Or, in other words, the first element begins at 0.

* You can append mutable objects such as a list inside tuples.
* You can concatenate tuples using the '+' operator.
```
In [13]: (4, None, 'foo') + (6, 0) + ('bar',)
Out[13]: (4, None, 'foo', 6, 0, 'bar')
```
* You can multiply a tuple to concatenate it. This creates multiple copies of that tuple.
```
In [14]: ('foo', 'bar') * 4
Out[14]: ('foo', 'bar', 'foo', 'bar', 'foo', 'bar', 'foo', 'bar')
```

##### Unpacking Tuples
* Python tries to assign values from the right hand side to the variables on the left hand side.
```
In [15]: tup = (4, 5, 6)
In [16]: a, b, c = tup
In [17]: b
Out[17]: 5
```
* Tuples make it convenient to swap variables.
```
In [21]: a, b = 1, 2
In [22]: b, a = a, b
In [23]: a
Out[24]: 2
In [25]: b
Out[26]: 1
```
* A common use of variable unpacking is iterating over sequences of tuples or lists:
```
In [27]: seq = [(1, 2, 3), (4, 5, 6), (7, 8, 9)]
In [28]: for a, b, c in seq:
 ....: print('a={0}, b={1}, c={2}'.format(a, b, c))
a=1, b=2, c=3
a=4, b=5, c=6
a=7, b=8, c=9
```
* New method to return multiple values or discard values you don't want.
```
In [29]: values = 1, 2, 3, 4, 5
In [30]: a, b, *rest = values
In [31]: a, b
Out[31]: (1, 2)
In [32]: rest
Out[32]: [3, 4, 5]
```
##### Tuple Methods
* Since tuples are immutable, it cannot be modified. Accessors such as count, count the number of occurrences of a value.

#### List
* Lists are variable-length and contents are mutable.

##### Adding and Removing Elements
* Use the **append** method to append to the end of the list.
* Use the **insert** method to insert to a specific location.
* To remove an element, use **pop** which returns an element at a specific index.
* To remove an element by value, use **remove**, which locates the first such value and removes it from the list.
* To check if a list contains a value, use in.
```
In[55]: 'dwarf' in b_list
Out[55]: True
```
* The keyword not signifies negation.
##### Concatentating and Combining Lists
* You can concatenate lists with '+' operator. However, this is expensive.
* Using **extend** builds up an existing list.
```
everything = []
for chunk in list_of_lists:
  everything.extend(chunk)
```
* The above example is faster than concatenating a list with '+'.
##### Sorting
* You can sort a list in-place with **sort.**
  * The **sort** function allows you to pass in a key. If you want to sort strings by length:
```
In [64]: b = ['saw', 'small', 'He', 'foxes', 'six']
In [65]: b.sort(key=len)
In [66]: b
Out[66]: ['He', 'saw', 'six', 'small', 'foxes']
```
##### Binary Search and Maintaining a Sorted List
* The **bisect** module implements binary search and insertion into a sorted list.
  * The **bisect.bisect** tells you where an element, if inserted, should go to keep it sorted.
  * The **biset.insort** inserts element into the location.
##### Slicing
* You can select selections of most sequence types using slice notation. **[start:stop]**
```
In [73]: seq = [7, 2, 3, 7, 5, 6, 0, 1]
In [74]: seq[1:5]
Out[74]: [2, 3, 7, 5]
```
* Slices can also be assigned to with a sequence:
```
In [75]: seq[3:4] = [6, 3]
In [76]: seq
Out[76]: [7, 2, 3, 6, 3, 5, 6, 0, 1]
```
* Using **:stop** will default to the start of the sequence and end at the stop index.
* Using **start:** will default to the start index and end at the end.
* Using **::end** will step by every other element.
* Using **::-1** will reverse a list or tuple.

#### Built-in Sequence Functions
* Using **enumerate** keeps track of the index of the current items
* Using **sorted** returns a new sorted list from the elements of any sequence.
* Using **zip** pairs up elements of a number of lists, tuples, or other sequence to create a list of tuples.
 * A common use for zip is to simultaneously iterate over multiple sequences, possibly combined with enumerate.
 * An example would be converting list of rows into a list of columns.
```
In [96]: pitchers = [('Nolan', 'Ryan'), ('Roger', 'Clemens'),
 ....: ('Schilling', 'Curt')]
In [97]: first_names, last_names = zip(*pitchers)
In [98]: first_names
Out[98]: ('Nolan', 'Roger', 'Schilling')
In [99]: last_names
Out[99]: ('Ryan', 'Clemens', 'Curt')
```
