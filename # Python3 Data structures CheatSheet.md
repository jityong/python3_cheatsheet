# Python3 Data structures CheatSheet

## Time Complexity:
Usually 10^8 operations per sec. 
1. n <= 100 : O(n^4)
2. n <= 500 : O(n^3)
3. n <= 10^4 : O(n^2)
4. n <= 10^6 : O(n logn)
5. n <= 10^8 : O(n)
6. n > 10^8 : O(log n) 


# Ranges 
1. int (4bytes) = 2^31 (because signed) [ 10 digits in total ]
## Strings
* get character at index: `s[i]`
* find if substring exists: `x in s`
* slice `s[i:j]`, j excluded
  ``` 
  s = "01234"
  s[0:4] --> 0123 
  ```
* slice with step k: `s[i:j:k]`
  ```
  s = "01234"
  s[0:4:2] --> 02
  ```
* find min in string: `min(s)`
* find max in string: `max(s)`
* number of occurences in string: `str.count(x)` 
* find lowest index of substring in string, returns -1 if not found: `str.find(substring)`
* check if starts with a prefix: `str.startswith(substring)`
* JOINS iterable such as list elements of strings into a string: `str.join(iterable`
  ```
  ",".join(ls)` --> "a,b,c"
  ```
* SPLIT string into list using delimiter: `str.split(" ")`
  ```
  s = "1 2 3 4"
  a = s.split(" ")
  a
  >> ['1','2','3','4']
  ```

* 
### Queue
`
import queue
`  

* initialize: `q = queue.Queue(maxsize=0)`
* `q.get()`: removes & return item from queue -- O(1)
* `q.put()`: puts item in queue -- O(1)
* `q.empty() q.full()`: returns `Boolean`
* 


## List

* initialize: ` ls = []`
* reverse list: `ls.reverse()`
  * Reverses the list in place (modifies the list)
* concatenate lists = `[1] + [2] = [1,2]`
* sort:  // by default in increasing order
  * `sorted(ls)` // create new list (not in-place)
  * `sorted(list, key = , reverse = True)`
  * `ls.sort()` // modify this list (in-place, tim-sort)
  * `ls.sort( key= , reverse= True)`
  * key is a function that takes in one argument --> possible to ammend the element and/or sort them based on the computed value from this function
* remove duplicates from list: 
  * `mylist = list(dict.fromkeys(mylist))`
  * `myList = list(set(myList))`
* remove element from list: 
  * `ls.remove(element)` //removes first matching element (no return value)
  * `ls.pop(index)` //removes index, -1 is default (rhs of list) (retunrs popped value)
* Inserts into position:
  * ls.insert(index, element) //push original index element to its right
* Traverse in reversed order: 
  ```
  1)for item in my_list[::-1]:
    print item
  
  2)for i in reversed(a):
      print(i)
      # Note that reversed doesn't actually reverse anything, it merely returns an obj that can be used to iterate over container's elements in reverse order.

  3)for i in range(len(ls)-1, -1, -1): #start(include),end(exclude), step
    print collection[i]
  ```
* Create 2D array:
  ```
  Good:
  A = [[0] * k for k in xrange(1, 102)]

  Bad:
  A = [[0]*102] *102
  // This is because the "inner arrays copied" are basically shallow copies, referencing one array. hence a change to any of them will reuslt in change to ALL of them. 
  ```

* Modifying list in-place ( ie passed as argument to a function and want to modify inside function, reflecting the change after function completes)
  * If we assign something to it, it will point to a new value. Value it pointed to before assignment( original list ) will remain unchanged.
  * Instead, assign something to the elements of the list, which will change the original list.
  ```
  list_arg[:] = nums[:2] + sorted(nums[2:])
  ```
### Behaviors:
* `+=` vs `+ then assign`. [more info](https://stackoverflow.com/questions/2347265/why-does-behave-unexpectedly-on-lists)
    `+=` | ` b = b + a`
    ---| ---
    __iadd__ special method | __add__
    in-place addition, mutates object it acts on | returns new object, used for standard `+` op
    object (of mutable types) like list: changes the objects value  |   objects (of immutable types): new object is returned & assigned (if used +=, equivalent to using +)
    `a1=a2=[1,2]  a1+=[3]  a2:[1,2,3]` | `b1=b2=[1,2]  b1 =b1+[3]   b2: [1,2]`
* concantenate list `[1] + [2] == [1,2]`

* List vs Array

    LIST	| ARRAY 
    ---|---|
    | Can consist of elements belonging to different data types	| Only consists of elements belonging to the same data type
    No need to explicitly import a module for declaration	| Need to explicitly import a module for declaration
    Cannot directly handle arithmetic operations |	Can directly handle arithmetic operations
    Can be nested to contain different type of elements |	Must contain either all nested elements of same size
    Preferred for shorter sequence of data items |	Preferred for longer sequence of data items
    Greater flexibility allows easy modification (addition, deletion) of data	| Less flexibility since addition, deletion has to be done element wise
    The entire list can be printed without any explicit looping	| A loop has to be formed to print or access the components of array
    Consume larger memory for easy addition of elements |	Comparatively more compact in memory size

## Heapq

`import heapq`
* Uses a list ` pq = [] `
* `heappush(pq, item)`
* `heappop(pq)`
* `heapify(pq)` - transforms list into pq
* 

## Set:
* initialize: `s = set()`
* if use `s = {}` it becomes an empty dict instead of set
* add(elem)
  Add element elem to the set.


* remove(elem)
Remove element elem from the set. Raises KeyError if elem is not contained in the set.

* discard(elem)
Remove element elem from the set if it is present.

* pop()
Remove and return an arbitrary element from the set. Raises KeyError if the set is empty.

* clear()
Remove all elements from the set

## Dictionary:

* initialize: `dict = {}`
* `dict = {'key1' : 'value1', 'key2': 'value2'}`
* list of keys in dict: `list(dict)` -- O(n)
* number of keys in dict: `len(dict)` -- O(n)
* access value : `dict[key]` -- O(1) | raises KeyError if key not inside
* get key , returns default (none if no default): `dict.get(key)` -- O(1)
* check if key exists: `key in dict`  -- O(1)
* remove key from dict: `del dict[key]` -- O(1)
* remove all items : `dict.clear()`
* shallow copy of dict: `dict.copy()`
* dict with default values: `dict.setdefault(key, default_val)` | if dict[key] not inside, assigns & return default val & no KeyError. This is actly simialr to get, just that it sets a default value if null before getting. 
* `dict = defaultdict(lambda:0)`


## Mutable vs Immutable objects in python
[more info](https://medium.com/@meghamohan/mutable-and-immutable-side-of-python-c2145cf72747#:~:text=Simple%20put%2C%20a%20mutable%20object,Custom%20classes%20are%20generally%20mutable)

![alt text](mutable_immutable.png "mutable vs immutable table")

* id() identifies object - corresponds to location in memory
* Immutable objects doesn’t allow modification after creation -- will create a new copy
    >Example: 
    ```
    x = 1  
    y = x #id(x) == id(y) 
    y = x + 1 #id(x) != id(y), because int 1 (and x) cannot be modified and creates a copy for this new value
    >> x is 1
    >> y is 2
    ```
* Mutable objects will change the object if a operation modifies it
  >Example:
  ```
  x = [1]
  y = x #id(x) == id(y) 
  y.pop() #id(x) == id(y) since the object is mutable, so modified in place
  >> x is []
  >> y is []
  ```

* Exception: the “value” of an immutable object can’t change, but it’s constituent objects can. 
  > Example: list inside a tuple can change, but the tuple itself will not change.


## Copy objects (esp list)
* copy.copy(object) -- returns a shallow copy
* copy.deepcopy(obj) -- returns a deep copy
```
import copy
a = [1,2]
b = copy.deepcopy(a)
a.pop()
>> a: [1]
>> b: [1,2]
```

## Time complexity:
https://wiki.python.org/moin/TimeComplexity

## MSC
1. Breaking out of outer for loop: can use a flag to indicate when inner for loop is broken
2. Power: 2**32[return type same as operand, unless its raised to power of -ve num, in which case it will return float], math.pow(2,31) [return type: float] 

