# Python List Methods - Complete Guide

This guide covers all 11 built-in list methods in Python with detailed explanations and examples.

## 1. `append(item)`

**Purpose**: Adds a single item to the end of the list.

**Key Points**:
- Adds exactly one element, regardless of the item type
- If you append a list, the entire list becomes one element
- Modifies the original list in place
- Returns `None`

```python
# Basic append
fruits = ['apple', 'banana']
fruits.append('orange')
print("After append:", fruits)  # ['apple', 'banana', 'orange']

# Appending a list creates a nested structure
numbers = [1, 2, 3]
numbers.append([4, 5])  # adds the entire list as one element
print("Append list:", numbers)  # [1, 2, 3, [4, 5]]

# Appending different data types
mixed = []
mixed.append(42)
mixed.append("hello")
mixed.append(True)
print("Mixed types:", mixed)  # [42, 'hello', True]
```

---

## 2. `clear()`

**Purpose**: Removes all elements from the list, making it empty.

**Key Points**:
- Takes no parameters
- Equivalent to `del list[:]` or `list[:] = []`
- More readable than alternatives
- Modifies original list, returns `None`

```python
colors = ['red', 'green', 'blue', 'yellow']
print("Before clear:", colors)  # ['red', 'green', 'blue', 'yellow']

colors.clear()
print("After clear:", colors)   # []
print("Length:", len(colors))   # 0
```

---

## 3. `copy()`

**Purpose**: Creates a shallow copy of the list.

**Key Points**:
- Returns a new list object with the same elements
- Changes to the new list don't affect the original
- **Shallow copy**: nested mutable objects are still referenced, not copied
- Equivalent to `list[:]` or `list(original_list)`

```python
# Basic copy
original = [1, 2, 3]
copied = original.copy()
copied.append(4)
print("Original:", original)  # [1, 2, 3]
print("Copied:", copied)      # [1, 2, 3, 4]

# Shallow copy demonstration with nested lists
nested_original = [1, 2, [3, 4]]
nested_copied = nested_original.copy()

# Modifying top-level doesn't affect original
nested_copied.append(5)
print("Original after top-level change:", nested_original)  # [1, 2, [3, 4]]

# But modifying nested objects affects both!
nested_copied[2].append(99)
print("Original after nested change:", nested_original)  # [1, 2, [3, 4, 99]]
print("Copied after nested change:", nested_copied)      # [1, 2, [3, 4, 99], 5]
```

---

## 4. `count(item)`

**Purpose**: Returns the number of times an item appears in the list.

**Key Points**:
- Returns an integer (0 if item not found)
- Uses `==` for comparison
- Case-sensitive for strings
- Works with any data type

```python
letters = ['a', 'b', 'a', 'c', 'a', 'b']
print("Count of 'a':", letters.count('a'))  # 3
print("Count of 'b':", letters.count('b'))  # 2
print("Count of 'z':", letters.count('z'))  # 0 (not found)

# Case sensitivity
words = ['Hello', 'hello', 'HELLO', 'world']
print("Count 'hello':", words.count('hello'))    # 1
print("Count 'Hello':", words.count('Hello'))    # 1

# With numbers
numbers = [1, 2, 1, 3, 1, 2, 4]
print("Count of 1:", numbers.count(1))  # 3
```

---

## 5. `extend(iterable)`

**Purpose**: Adds all elements from an iterable to the end of the list.

**Key Points**:
- Takes any iterable (list, tuple, string, set, etc.)
- Adds elements individually (unlike `append`)
- Modifies original list in place
- More efficient than multiple `append()` calls

```python
# Extending with a list
list1 = [1, 2, 3]
list1.extend([4, 5, 6])
print("Extended with list:", list1)  # [1, 2, 3, 4, 5, 6]

# Extending with a string (each character added separately)
list2 = ['x', 'y']
list2.extend('abc')
print("Extended with string:", list2)  # ['x', 'y', 'a', 'b', 'c']

# Extending with a tuple
list3 = [10, 20]
list3.extend((30, 40, 50))
print("Extended with tuple:", list3)  # [10, 20, 30, 40, 50]

# Extending with a range
list4 = [0]
list4.extend(range(1, 4))
print("Extended with range:", list4)  # [0, 1, 2, 3]

# Comparison: extend vs append
append_demo = [1, 2]
extend_demo = [1, 2]

append_demo.append([3, 4])    # adds list as single element
extend_demo.extend([3, 4])    # adds each element separately

print("After append:", append_demo)  # [1, 2, [3, 4]]
print("After extend:", extend_demo)  # [1, 2, 3, 4]
```

---

## 6. `index(item, start=0, end=len)`

**Purpose**: Returns the index of the first occurrence of an item.

**Key Points**:
- Raises `ValueError` if item is not found
- Optional `start` parameter: where to begin searching
- Optional `end` parameter: where to stop searching (exclusive)
- Returns the first match only

```python
animals = ['cat', 'dog', 'cat', 'bird', 'cat']

# Basic usage
print("First 'cat' at index:", animals.index('cat'))  # 0

# Start searching from a specific index
print("Second 'cat' at index:", animals.index('cat', 1))  # 2

# Search within a range
print("'cat' between index 1-4:", animals.index('cat', 1, 4))  # 2

# Search in the last part
print("Last 'cat' found:", animals.index('cat', 3))  # 4

# Handling errors
try:
    animals.index('elephant')
except ValueError:
    print("'elephant' not found in the list")

# Using with strings
sentence = "hello world hello python"
words = sentence.split()
print("Words:", words)  # ['hello', 'world', 'hello', 'python']
print("First 'hello' at:", words.index('hello'))     # 0
print("Second 'hello' at:", words.index('hello', 1)) # 2
```

---

## 7. `insert(index, item)`

**Purpose**: Inserts an item at a specified position.

**Key Points**:
- First parameter is the index, second is the item
- Shifts existing elements to the right
- If index > length, item is appended to the end
- Negative indices work (count from the end)

```python
cities = ['New York', 'London', 'Tokyo']

# Insert in the middle
cities.insert(1, 'Paris')
print("After insert at 1:", cities)  # ['New York', 'Paris', 'London', 'Tokyo']

# Insert at the beginning
cities.insert(0, 'Sydney')
print("After insert at 0:", cities)  # ['Sydney', 'New York', 'Paris', 'London', 'Tokyo']

# Insert at the end (equivalent to append)
cities.insert(len(cities), 'Mumbai')
print("Insert at end:", cities)  # ['Sydney', 'New York', 'Paris', 'London', 'Tokyo', 'Mumbai']

# Insert beyond list length (appends to end)
cities.insert(100, 'Cairo')
print("Insert beyond length:", cities)  # ['Sydney', 'New York', 'Paris', 'London', 'Tokyo', 'Mumbai', 'Cairo']

# Negative indices
numbers = [1, 2, 3, 4]
numbers.insert(-1, 99)  # insert before the last element
print("Insert at -1:", numbers)  # [1, 2, 3, 99, 4]
```

---

## 8. `pop(index=-1)`

**Purpose**: Removes and returns an item at a given position.

**Key Points**:
- Default removes the last item (index -1)
- Returns the removed item
- Raises `IndexError` if index is out of range
- Useful for implementing stacks (LIFO) and queues

```python
scores = [85, 92, 78, 96, 88]

# Pop last item (default behavior)
last_score = scores.pop()
print("Popped last:", last_score)  # 96
print("Remaining scores:", scores)  # [85, 92, 78, 88]

# Pop specific index
second_score = scores.pop(1)
print("Popped index 1:", second_score)  # 92
print("After pop(1):", scores)  # [85, 78, 88]

# Pop first item
first_score = scores.pop(0)
print("Popped first:", first_score)  # 85
print("Final scores:", scores)  # [78, 88]

# Using pop for stack operations (LIFO - Last In, First Out)
stack = []
stack.append('first')
stack.append('second')
stack.append('third')
print("Stack:", stack)  # ['first', 'second', 'third']

while stack:
    item = stack.pop()
    print(f"Popped: {item}")
# Output: Popped: third, Popped: second, Popped: first

# Error handling
empty_list = []
try:
    empty_list.pop()
except IndexError:
    print("Cannot pop from empty list")
```

---

## 9. `remove(item)`

**Purpose**: Removes the first occurrence of a specified item.

**Key Points**:
- Removes only the first match
- Raises `ValueError` if item is not found
- Uses `==` for comparison
- Returns `None`

```python
vegetables = ['carrot', 'broccoli', 'carrot', 'spinach', 'carrot']

# Remove first occurrence
vegetables.remove('carrot')
print("After removing 'carrot':", vegetables)  # ['broccoli', 'carrot', 'spinach', 'carrot']

# Remove another item
vegetables.remove('spinach')
print("After removing 'spinach':", vegetables)  # ['broccoli', 'carrot', 'carrot']

# Error handling for non-existent item
try:
    vegetables.remove('tomato')
except ValueError:
    print("'tomato' not found in the list")

# Safe removal function
def safe_remove(lst, item):
    if item in lst:
        lst.remove(item)
        return True
    return False

result = safe_remove(vegetables, 'broccoli')
print("Removal successful:", result)  # True
print("After safe removal:", vegetables)  # ['carrot', 'carrot']

# Remove all occurrences (using while loop)
numbers = [1, 2, 3, 2, 4, 2, 5]
while 2 in numbers:
    numbers.remove(2)
print("After removing all 2's:", numbers)  # [1, 3, 4, 5]
```

---

## 10. `reverse()`

**Purpose**: Reverses the elements of the list in place.

**Key Points**:
- Modifies the original list
- Returns `None`
- More efficient than creating a new reversed list
- Different from `reversed()` built-in function

```python
# Basic reverse
months = ['January', 'February', 'March', 'April']
print("Original:", months)

months.reverse()
print("Reversed:", months)  # ['April', 'March', 'February', 'January']

# Reverse numbers
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
print("Reversed numbers:", numbers)  # [5, 4, 3, 2, 1]

# Comparison with reversed() function
original = [1, 2, 3, 4]
copy_for_reverse = original.copy()

# Method 1: reverse() - modifies original
copy_for_reverse.reverse()
print("Using reverse():", copy_for_reverse)  # [4, 3, 2, 1]

# Method 2: reversed() - returns iterator, original unchanged
reversed_iter = list(reversed(original))
print("Using reversed():", reversed_iter)  # [4, 3, 2, 1]
print("Original unchanged:", original)     # [1, 2, 3, 4]

# Method 3: Slicing - creates new list
sliced_reverse = original[::-1]
print("Using slicing:", sliced_reverse)  # [4, 3, 2, 1]
```

---

## 11. `sort(key=None, reverse=False)`

**Purpose**: Sorts the list in place.

**Key Points**:
- Modifies the original list
- `key` parameter: function to customize sort logic
- `reverse=True` for descending order
- Returns `None`
- Uses TimSort algorithm (stable sort)

```python
# Basic ascending sort
numbers = [64, 34, 25, 12, 22, 11, 90]
numbers.sort()
print("Sorted ascending:", numbers)  # [11, 12, 22, 25, 34, 64, 90]

# Descending sort
numbers.sort(reverse=True)
print("Sorted descending:", numbers)  # [90, 64, 34, 25, 22, 12, 11]

# String sorting (lexicographic)
words = ['banana', 'pie', 'Washington', 'book']
words.sort()
print("Default string sort:", words)  # ['Washington', 'banana', 'book', 'pie']

# Case-insensitive sorting
words.sort(key=str.lower)
print("Case-insensitive sort:", words)  # ['banana', 'book', 'pie', 'Washington']

# Sort by string length
words = ['elephant', 'cat', 'hippopotamus', 'dog']
words.sort(key=len)
print("Sorted by length:", words)  # ['cat', 'dog', 'elephant', 'hippopotamus']

# Sort by length, then alphabetically
words.sort(key=lambda x: (len(x), x.lower()))
print("By length, then alphabetically:", words)  # ['cat', 'dog', 'elephant', 'hippopotamus']

# Sorting tuples and complex objects
students = [('Alice', 85), ('Bob', 90), ('Charlie', 78), ('Alice', 92)]

# Sort by grade (second element)
students.sort(key=lambda student: student[1])
print("Sorted by grade:", students)  # [('Charlie', 78), ('Alice', 85), ('Bob', 90), ('Alice', 92)]

# Sort by name, then by grade
students.sort(key=lambda student: (student[0], student[1]))
print("By name, then grade:", students)  # [('Alice', 85), ('Alice', 92), ('Bob', 90), ('Charlie', 78)]

# Custom sorting with multiple criteria
products = [
    {'name': 'laptop', 'price': 1000, 'rating': 4.5},
    {'name': 'phone', 'price': 800, 'rating': 4.7},
    {'name': 'tablet', 'price': 600, 'rating': 4.3},
    {'name': 'watch', 'price': 300, 'rating': 4.6}
]

# Sort by rating (descending), then by price (ascending)
products.sort(key=lambda x: (-x['rating'], x['price']))
print("Sorted products:")
for product in products:
    print(f"  {product['name']}: ${product['price']}, Rating: {product['rating']}")

# Comparison with sorted() function
original_numbers = [3, 1, 4, 1, 5, 9, 2, 6]
copy_for_sort = original_numbers.copy()

# Method 1: sort() - modifies original
copy_for_sort.sort()
print("Using sort():", copy_for_sort)  # [1, 1, 2, 3, 4, 5, 6, 9]

# Method 2: sorted() - returns new list, original unchanged
sorted_numbers = sorted(original_numbers)
print("Using sorted():", sorted_numbers)  # [1, 1, 2, 3, 4, 5, 6, 9]
print("Original unchanged:", original_numbers)  # [3, 1, 4, 1, 5, 9, 2, 6]
```

---

## Summary

| Method | Modifies Original | Returns | Purpose |
|--------|-------------------|---------|---------|
| `append()` | Yes | `None` | Add single item to end |
| `clear()` | Yes | `None` | Remove all elements |
| `copy()` | No | New list | Create shallow copy |
| `count()` | No | Integer | Count occurrences |
| `extend()` | Yes | `None` | Add all items from iterable |
| `index()` | No | Integer | Find first occurrence index |
| `insert()` | Yes | `None` | Insert item at specific position |
| `pop()` | Yes | Removed item | Remove and return item |
| `remove()` | Yes | `None` | Remove first occurrence |
| `reverse()` | Yes | `None` | Reverse list order |
| `sort()` | Yes | `None` | Sort list in place |

### Key Concepts:
- **In-place operations**: Most methods modify the original list and return `None`
- **Shallow copy**: `copy()` creates a new list but doesn't copy nested objects
- **Error handling**: `index()`, `remove()`, and `pop()` can raise exceptions
- **Flexibility**: Methods like `sort()` and `index()` accept additional parameters for customization