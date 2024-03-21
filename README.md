# Python for Coding Interviews

## Variables

- Variables in Python are dynamically typed.
- You can assign values of different data types to the same variable.

```python
n = 0
print('n =', n)
>>> n = 0

n = "abc"
print('n =', n)
>>> n = abc
```

- Multiple variables can be assigned in a single line.

```python
n, m = 0, "abc"
n, m, z = 0.125, "abc", False
```

- Incrementing variables:
  - `n = n + 1` and `n += 1` are valid.
  - `n++` is not valid in Python.

- `None` represents a null value or the absence of a value.

```python
n = 4
n = None
print("n =", n)
>>> n = None
```

## If-statements

- If statements in Python don't need parentheses or curly braces.

```python
n = 1
if n > 2:
    n -= 1
elif n == 2:
    n *= 2
else:
    n += 2
```

- Parentheses are needed for multi-line conditions.
- `and` is used for logical AND (`&&` in other languages).
- `or` is used for logical OR (`||` in other languages).

```python
n, m = 1, 2
if ((n > 2 and 
    n != m) or n == m):
    n += 1
```

## Loops

- `while` loop:

```python
n = 5
while n < 5:
    print(n)
    n += 1
```

- `for` loop with `range()`:
  - `range(5)` loops from `i = 0` to `i = 4`.
  - `range(2, 6)` loops from `i = 2` to `i = 5`.
  - `range(5, 1, -1)` loops from `i = 5` to `i = 2` in reverse order.

```python
for i in range(5):
    print(i)

for i in range(2, 6):
    print(i)

for i in range(5, 1, -1):
    print(i)
```

## Math

- Division `/` returns a decimal result.
- `//` performs floor division (rounding down).
- Be careful with negative numbers in floor division, as Python rounds towards negative infinity by default.

```python
print(5 / 2)  # 2.5
print(5 // 2) # 2
print(-3 // 2) # -2
```

- To round towards zero, convert to `int` after division.

```python
print(int(-3 / 2)) # -1
```

- Modulo `%` works as expected, except for negative numbers.

```python
print(10 % 3) # 1
print(-10 % 3) # -1
```

- Use `math.fmod()` for consistent modulo behavior with negative numbers.

```python
import math
print(math.fmod(-10, 3)) # 2.0
```

- Other math helpers:
  - `math.floor()` rounds down to the nearest integer.
  - `math.ceil()` rounds up to the nearest integer.
  - `math.sqrt()` calculates the square root.
  - `math.pow()` calculates the power.

```python
print(math.floor(3 / 2)) # 1.0
print(math.ceil(3 / 2))  # 2.0
print(math.sqrt(2))      # 1.4142135623730951
print(math.pow(2, 3))    # 8.0
```

- Python uses arbitrary-precision arithmetic, so numbers don't overflow.
- `float("inf")` and `float("-inf")` represent positive and negative infinity, respectively.

```python
print(math.pow(2, 200)) # 1.6069...e+60
print(math.pow(2, 200) < float("inf")) # True
```

## Arrays

- Arrays are called "lists" in Python.

```python
arr = [1, 2, 3]
print(arr) # [1, 2, 3]
```

- Lists can be used as stacks:
  - `append()` adds an element to the end.
  - `pop()` removes and returns the last element.
  - `insert(index, value)` inserts a value at the specified index.

```python
arr.append(4)
arr.append(5)
print(arr) # [1, 2, 3, 4, 5]

arr.pop()
print(arr) # [1, 2, 3, 4]

arr.insert(1, 7)
print(arr) # [1, 7, 2, 3, 4]
```

- List elements can be modified directly using indexing.

```python
arr[0] = 0
arr[3] = 0
print(arr) # [0, 7, 2, 0, 4]
```

- Lists can be initialized with a default value using multiplication.

```python
n = 5
arr = [1] * n
print(arr) # [1, 1, 1, 1, 1]
print(len(arr)) # 5
```

- Negative indexing accesses elements from the end of the list.

```python
arr = [1, 2, 3]
print(arr[-1]) # 3
print(arr[-2]) # 2
```

- Slicing creates a sublist.

```python
arr = [1, 2, 3, 4]
print(arr[1:3]) # [2, 3]
print(arr[0:4]) # [1, 2, 3, 4]
print(arr[0:10]) # [1, 2, 3, 4]
```

- List unpacking:

```python
a, b, c = [1, 2, 3]
print(a, b, c) # 1 2 3
```

- Looping through lists:
  - Using index:

    ```python
    nums = [1, 2, 3]
    for i in range(len(nums)):
        print(nums[i])
    ```

  - Without index:

    ```python
    for n in nums:
        print(n)
    ```

  - With index and value:

    ```python
    for i, n in enumerate(nums):
        print(i, n)
    ```

- Looping through multiple lists simultaneously with unpacking:

```python
nums1 = [1, 3, 5]
nums2 = [2, 4, 6]
for n1, n2 in zip(nums1, nums2):
    print(n1, n2)
```

- Reversing a list:

```python
nums = [1, 2, 3]
nums.reverse()
print(nums) # [3, 2, 1]
```

- Sorting a list:
  - `sort()` sorts the list in ascending order.
  - `sort(reverse=True)` sorts the list in descending order.
  - You can provide a custom sorting key using `key=lambda`.

```python
arr = [5, 4, 7, 3, 8]
arr.sort()
print(arr) # [3, 4, 5, 7, 8]

arr.sort(reverse=True)
print(arr) # [8, 7, 5, 4, 3]

arr = ["bob", "alice", "jane", "doe"]
arr.sort()
print(arr) # ['alice', 'bob', 'doe', 'jane']

# Custom sort (by length of string)
arr.sort(key=lambda x: len(x))
print(arr) # ['bob', 'doe', 'jane', 'alice']
```

- List comprehension:

```python
arr = [i for i in range(5)]
print(arr) # [0, 1, 2, 3, 4]
```

- 2D lists:

```python
arr = [[0] * 4 for i in range(4)]
print(arr) # [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
print(arr[0][0], arr[3][3]) # 0 0
```

## Strings

- Strings are similar to arrays in Python.
- Slicing works the same way as with lists.

```python
s = "abc"
print(s[0:2]) # "ab"
```

- Strings are immutable, so you can't modify individual characters.

```python
s[0] = "A"  # This will raise an error
```

- To modify a string, you need to create a new string.

```python
s += "def"
print(s) # "abcdef"
```

- Valid numeric strings can be converted to integers.

```python
print(int("123") + int("123")) # 246
```

- Numbers can be converted to strings.

```python
print(str(123) + str(123)) # "123123"
```

- To get the ASCII value of a character, use `ord()`.

```python
print(ord("a")) # 97
print(ord("b")) # 98
```

- To join a list of strings, use `"".join(list)`.

```python
strings = ["ab", "cd", "ef"]
print("".join(strings)) # "abcdef"
```

## Queues

- Python has a built-in `deque` (double-ended queue) in the `collections` module.

```python
from collections import deque

queue = deque()
queue.append(1)
queue.append(2)
print(queue) # deque([1, 2])

queue.popleft()
print(queue) # deque([2])

queue.appendleft(1)
print(queue) # deque([1, 2])

queue.pop()
print(queue) # deque([1])
```

## HashSets

- Sets in Python are unordered collections of unique elements.

```python
mySet = set()

mySet.add(1)
mySet.add(2)
print(mySet) # {1, 2}
print(len(mySet)) # 2

print(1 in mySet) # True
print(2 in mySet) # True
print(3 in mySet) # False

mySet.remove(2)
print(2 in mySet) # False
```

- You can create a set from a list.

```python
print(set([1, 2, 3])) # {1, 2, 3}
```

- Set comprehension:

```python
mySet = { i for i in range(5) }
print(mySet) # {0, 1, 2, 3, 4}
```

## HashMaps

- Dictionaries in Python are hash maps (unordered key-value pairs).

```python
myMap = {}
myMap["alice"] = 88
myMap["bob"] = 77
print(myMap) # {'alice': 88, 'bob': 77}
print(len(myMap)) # 2

myMap["alice"] = 80
print(myMap["alice"]) # 80

print("alice" in myMap) # True
myMap.pop("alice")
print("alice" in myMap) # False

myMap = { "alice": 90, "bob": 70 }
print(myMap) # {'alice': 90, 'bob': 70}
```

- Dictionary comprehension:

```python
myMap = { i: 2*i for i in range(3) }
print(myMap) # {0: 0, 1: 2, 2: 4}
```

- Looping through dictionaries:
  - Keys:

    ```python
    myMap = { "alice": 90, "bob": 70 }
    for key in myMap:
        print(key, myMap[key])
    ```

  - Values:

    ```python
    for val in myMap.values():
        print(val)
    ```

  - Key-value pairs:

    ```python
    for key, val in myMap.items():
        print(key, val)
    ```

## Tuples

- Tuples are immutable sequences of values, similar to lists.

```python
tup = (1, 2, 3)
print(tup) # (1, 2, 3)
print(tup[0]) # 1
print(tup[-1]) # 3
```

- You can't modify tuple elements.

```python
tup[0] = 0  # This will raise an error
```

- Tuples can be used as keys in dictionaries and sets.

```python
myMap = { (1,2): 3 }
print(myMap[(1,2)]) # 3

mySet = set()
mySet.add((1, 2))
print((1, 2) in mySet) # True
```

- Lists can't be used as keys because they are mutable.

```python
myMap[[3, 4]] = 5  # This will raise an error
```

## Heaps

- Python has a built-in `heapq` module for creating heaps.
- Under the hood, heaps are implemented using arrays.

```python
import heapq

# Min Heap
minHeap = []
heapq.heappush(minHeap, 3)
heapq.heappush(minHeap, 2)
heapq.heappush(minHeap, 4)

# Min is always at index 0
print(minHeap[0]) # 2

while len(minHeap):
    print(heapq.heappop(minHeap))
# 2
# 3
# 4
```

- There's no built-in max heap, but you can create one by multiplying the values by -1 when pushing and popping.

```python
# Max Heap
maxHeap = []
heapq.heappush(maxHeap, -3)
heapq.heappush(maxHeap, -2)
heapq.heappush(maxHeap, -4)

# Max is always at index 0
print(-1 * maxHeap[0]) # 4

while len(maxHeap):
    print(-1 * heapq.heappop(maxHeap))
# 4
# 3
# 2
```

- You can build a heap from an initial list of values using `heapify()`.

```python
arr = [2, 1, 8, 4, 5]
heapq.heapify(arr)
while arr:
    print(heapq.heappop(arr))
# 1
# 2
# 4
# 5
# 8
```

## Functions

- Functions are defined using the `def` keyword.

```python
def myFunc(n, m):
    return n * m

print(myFunc(3, 4)) # 12
```

- Nested functions have access to variables from outer functions.

```python
def outer(a, b):
    c = "c"

    def inner():
        return a + b + c
    return inner()

print(outer("a", "b")) # "abc"
```

- You can modify mutable objects (like lists) inside functions, but not reassign variables unless using the `nonlocal` keyword.

```python
def double(arr, val):
    def helper():
        # Modifying array works
        for i, n in enumerate(arr):
            arr[i] *= 2
        
        # Will only modify val in the helper scope
        # val *= 2

        # This will modify val outside helper scope
        nonlocal val
        val *= 2
    helper()
    print(arr, val)

nums = [1, 2]
val = 3
double(nums, val)
# Output: [2, 4] 6
```

## Classes

- Classes are defined using the `class` keyword.
- The `__init__` method is the constructor.
- Member variables are created inside the `__init__` method.
- The `self` keyword is required as the first argument in instance methods.

```python
class MyClass:
    # Constructor
    def __init__(self, nums):
        # Create member variables
        self.nums = nums
        self.size = len(nums)
