# Complete Python String Methods Guide with Examples

## 1. capitalize()
Converts the first character to uppercase and the rest to lowercase.

```python
text = "hello WORLD"
result = text.capitalize()
print(result)  # Output: "Hello world"

# Works even with numbers or symbols at the start
text2 = "123abc"
print(text2.capitalize())  # Output: "123abc"

# Empty string
print("".capitalize())  # Output: ""
```

## 2. casefold()
Returns a casefolded version of the string, suitable for caseless comparisons. More aggressive than `lower()` for Unicode characters.

```python
text = "Hello WORLD"
print(text.casefold())  # Output: "hello world"

# Handles special Unicode characters
german = "Straße"
print(german.casefold())  # Output: "strasse" (ß becomes ss)

# Comparison with lower()
print("HELLO".lower())     # Output: "hello"
print("HELLO".casefold())  # Output: "hello"
```

## 3. center()
Centers the string in a field of specified width, optionally with a fill character.

```python
text = "Python"

# Basic centering with spaces (default)
print(text.center(12))        # Output: "   Python   "
print(text.center(10))        # Output: "  Python  "

# With custom fill character
print(text.center(12, '*'))   # Output: "***Python***"
print(text.center(12, '-'))   # Output: "---Python---"

# If width is less than string length, returns original string
print(text.center(3))         # Output: "Python"
```

## 4. count()
Counts non-overlapping occurrences of a substring.

```python
text = "banana"

# Basic counting
print(text.count('a'))        # Output: 3
print(text.count('an'))       # Output: 2
print(text.count('ana'))      # Output: 1 (non-overlapping)

# With start parameter
print(text.count('a', 1))     # Output: 3 (start from index 1)
print(text.count('a', 2))     # Output: 2 (start from index 2)

# With start and end parameters
print(text.count('a', 1, 4))  # Output: 2 (from index 1 to 3)
print(text.count('a', 0, 3))  # Output: 2 (from index 0 to 2)

# Case sensitive
print("BaNaNa".count('a'))    # Output: 2
print("BaNaNa".count('A'))    # Output: 0
```

## 5. encode()
Encodes the string using the specified encoding.

```python
text = "Hello, 世界"

# Default UTF-8 encoding
encoded = text.encode()
print(encoded)  # Output: b'Hello, \xe4\xb8\x96\xe7\x95\x8c'
print(type(encoded))  # Output: <class 'bytes'>

# Explicit UTF-8
print(text.encode('utf-8'))   # Same as above

# ASCII encoding with error handling
ascii_text = "Hello"
print(ascii_text.encode('ascii'))  # Output: b'Hello'

# Error handling options
try:
    text.encode('ascii')  # Will raise UnicodeEncodeError
except UnicodeEncodeError:
    print("Cannot encode with ASCII")

# With error handling
print(text.encode('ascii', 'ignore'))    # Output: b'Hello, '
print(text.encode('ascii', 'replace'))   # Output: b'Hello, ??'
print(text.encode('ascii', 'xmlcharrefreplace'))  # Output: b'Hello, &#19990;&#30028;'
```

## 6. endswith()
Checks if the string ends with specified suffix(es).

```python
text = "hello.txt"

# Single suffix
print(text.endswith('.txt'))     # Output: True
print(text.endswith('.py'))      # Output: False

# Multiple suffixes (tuple)
print(text.endswith(('.txt', '.py', '.pdf')))  # Output: True
print(text.endswith(('.doc', '.py')))          # Output: False

# With start parameter
print(text.endswith('lo', 0, 5))  # Check "hello" ends with "lo" - True
print(text.endswith('xt', 6))     # Check from index 6 onwards - True

# With start and end parameters
print(text.endswith('ll', 0, 4))  # Check "hell" ends with "ll" - True
```

## 7. expandtabs()
Replaces tab characters with spaces.

```python
text = "Name\tAge\tCity"

# Default tab size (8 spaces)
print(text.expandtabs())         # Output: "Name    Age     City"
print(repr(text.expandtabs()))   # Shows spaces clearly

# Custom tab size
print(text.expandtabs(4))        # Output: "Name    Age City"
print(text.expandtabs(2))        # Output: "Name  Age City"

# Multiple tabs
text2 = "A\t\tB\tC"
print(text2.expandtabs(4))       # Output: "A       B   C"

# No tabs
text3 = "No tabs here"
print(text3.expandtabs())        # Output: "No tabs here" (unchanged)
```

## 8. find()
Finds the lowest index of substring. Returns -1 if not found.

```python
text = "banana"

# Basic search
print(text.find('a'))      # Output: 1 (first occurrence)
print(text.find('an'))     # Output: 1
print(text.find('na'))     # Output: 2 (first occurrence)
print(text.find('x'))      # Output: -1 (not found)

# With start parameter
print(text.find('a', 2))   # Output: 3 (search from index 2)
print(text.find('a', 4))   # Output: 5 (search from index 4)

# With start and end parameters
print(text.find('a', 1, 4))  # Output: 1 (search in "ana")
print(text.find('a', 2, 4))  # Output: 3 (search in "an")

# Case sensitive
print("BaNaNa".find('a'))    # Output: 1
print("BaNaNa".find('A'))    # Output: -1
```

## 9. format()
Formats the string using positional and keyword arguments.

```python
# Positional arguments
template = "Hello, {}! You are {} years old."
print(template.format("Alice", 25))  # Output: "Hello, Alice! You are 25 years old."

# Positional with indices
template2 = "Hello, {0}! {0} is {1} years old."
print(template2.format("Bob", 30))   # Output: "Hello, Bob! Bob is 30 years old."

# Keyword arguments
template3 = "Hello, {name}! You are {age} years old."
print(template3.format(name="Charlie", age=35))

# Mixed arguments
template4 = "Hello, {0}! {name} is {1} years old."
print(template4.format("David", 40, name="David"))

# Formatting options
print("Pi is approximately {:.2f}".format(3.14159))  # Output: "Pi is approximately 3.14"
print("Number: {:05d}".format(42))                   # Output: "Number: 00042"
print("Percentage: {:.1%}".format(0.875))            # Output: "Percentage: 87.5%"
```

## 10. format_map()
Similar to format() but takes a mapping object.

```python
data = {'name': 'Eve', 'age': 28}
template = "Hello, {name}! You are {age} years old."

# Using dictionary
print(template.format_map(data))  # Output: "Hello, Eve! You are 28 years old."

# Using custom mapping
class SafeDict(dict):
    def __missing__(self, key):
        return f"{{{key}}}"

safe_data = SafeDict(name='Frank')
template2 = "Hello, {name}! You are {age} years old."
print(template2.format_map(safe_data))  # Output: "Hello, Frank! You are {age} years old."
```

## 11. index()
Like find() but raises ValueError if substring is not found.

```python
text = "banana"

# Basic search
print(text.index('a'))      # Output: 1
print(text.index('an'))     # Output: 1

# With start parameter
print(text.index('a', 2))   # Output: 3

# With start and end parameters
print(text.index('a', 1, 4))  # Output: 1

# Raises ValueError if not found
try:
    print(text.index('x'))
except ValueError as e:
    print(f"Error: {e}")  # Output: "Error: substring not found"
```

## 12. isalnum()
Checks if all characters are alphanumeric (letters and digits).

```python
# All alphanumeric
print("abc123".isalnum())    # Output: True
print("ABC123".isalnum())    # Output: True

# Contains non-alphanumeric characters
print("abc 123".isalnum())   # Output: False (space)
print("abc-123".isalnum())   # Output: False (hyphen)
print("abc!".isalnum())      # Output: False (exclamation)

# Only letters
print("abc".isalnum())       # Output: True

# Only digits
print("123".isalnum())       # Output: True

# Empty string
print("".isalnum())          # Output: False
```

## 13. isalpha()
Checks if all characters are alphabetic letters.

```python
# All letters
print("abc".isalpha())       # Output: True
print("ABC".isalpha())       # Output: True
print("AbC".isalpha())       # Output: True

# Contains non-letter characters
print("abc123".isalpha())    # Output: False (digits)
print("abc ".isalpha())      # Output: False (space)
print("abc-def".isalpha())   # Output: False (hyphen)

# Unicode letters
print("café".isalpha())      # Output: True
print("москва".isalpha())    # Output: True

# Empty string
print("".isalpha())          # Output: False
```

## 14. isascii()
Checks if all characters are ASCII characters.

```python
# All ASCII
print("Hello123".isascii())   # Output: True
print("!@#$%".isascii())      # Output: True
print(" ".isascii())          # Output: True

# Contains non-ASCII characters
print("café".isascii())       # Output: False (é is not ASCII)
print("Hello, 世界".isascii())  # Output: False (Chinese characters)

# Empty string
print("".isascii())           # Output: True
```

## 15. isdecimal()
Checks if all characters are decimal characters (0-9).

```python
# Decimal digits
print("123".isdecimal())      # Output: True
print("0".isdecimal())        # Output: True

# Not decimal
print("12.3".isdecimal())     # Output: False (contains dot)
print("12a".isdecimal())      # Output: False (contains letter)
print("-123".isdecimal())     # Output: False (contains minus)
print(" 123".isdecimal())     # Output: False (contains space)

# Unicode decimal characters
print("123".isdecimal())      # Output: True
print("①②③".isdecimal())      # Output: False (these are numeric but not decimal)

# Empty string
print("".isdecimal())         # Output: False
```

## 16. isdigit()
Checks if all characters are digits (includes superscript digits).

```python
# Regular digits
print("123".isdigit())        # Output: True
print("0".isdigit())          # Output: True

# Superscript digits
print("²³".isdigit())         # Output: True

# Not digits
print("12.3".isdigit())       # Output: False
print("12a".isdigit())        # Output: False
print("-123".isdigit())       # Output: False

# Empty string
print("".isdigit())           # Output: False
```

## 17. isidentifier()
Checks if the string is a valid Python identifier.

```python
# Valid identifiers
print("variable".isidentifier())    # Output: True
print("_private".isidentifier())    # Output: True
print("var123".isidentifier())      # Output: True
print("CamelCase".isidentifier())   # Output: True

# Invalid identifiers
print("123var".isidentifier())      # Output: False (starts with digit)
print("var-name".isidentifier())    # Output: False (contains hyphen)
print("var name".isidentifier())    # Output: False (contains space)
print("".isidentifier())            # Output: False (empty)

# Keywords are valid identifiers but shouldn't be used
print("if".isidentifier())          # Output: True
print("for".isidentifier())         # Output: True
```

## 18. islower()
Checks if all cased characters are lowercase and there's at least one cased character.

```python
# All lowercase
print("hello".islower())      # Output: True
print("hello world".islower()) # Output: True

# Contains uppercase
print("Hello".islower())      # Output: False
print("hello World".islower()) # Output: False

# Only non-cased characters
print("123".islower())        # Output: False
print("!@#".islower())        # Output: False

# Mixed cased and non-cased
print("hello123".islower())   # Output: True
print("Hello123".islower())   # Output: False

# Empty string
print("".islower())           # Output: False
```

## 19. isnumeric()
Checks if all characters are numeric (includes digits, superscripts, subscripts, etc.).

```python
# Regular digits
print("123".isnumeric())      # Output: True

# Unicode numeric characters
print("²³".isnumeric())       # Output: True
print("½".isnumeric())        # Output: True
print("Ⅴ".isnumeric())        # Output: True (Roman numeral)

# Not numeric
print("12.3".isnumeric())     # Output: False
print("12a".isnumeric())      # Output: False
print("-123".isnumeric())     # Output: False

# Empty string
print("".isnumeric())         # Output: False
```

## 20. isprintable()
Checks if all characters are printable or the string is empty.

```python
# Printable characters
print("Hello World!".isprintable())  # Output: True
print("123".isprintable())           # Output: True
print("".isprintable())              # Output: True

# Non-printable characters
print("Hello\nWorld".isprintable())  # Output: False (contains newline)
print("Hello\tWorld".isprintable())  # Output: False (contains tab)
print("Hello\x00World".isprintable()) # Output: False (contains null character)
```

## 21. isspace()
Checks if all characters are whitespace characters and there's at least one character.

```python
# Whitespace characters
print(" ".isspace())          # Output: True (space)
print("\t".isspace())         # Output: True (tab)
print("\n".isspace())         # Output: True (newline)
print("   ".isspace())        # Output: True (multiple spaces)
print(" \t\n".isspace())      # Output: True (mixed whitespace)

# Not whitespace
print("".isspace())           # Output: False (empty)
print("hello".isspace())      # Output: False
print(" hello ".isspace())    # Output: False (contains non-whitespace)
```

## 22. istitle()
Checks if string is in title case (first letter of each word is uppercase, rest lowercase).

```python
# Title case
print("Hello World".istitle())       # Output: True
print("The Quick Brown Fox".istitle()) # Output: True

# Not title case
print("hello world".istitle())       # Output: False
print("HELLO WORLD".istitle())       # Output: False
print("Hello WORLD".istitle())       # Output: False
print("hello World".istitle())       # Output: False

# Special cases
print("Don'T".istitle())             # Output: True (apostrophe breaks word)
print("123Abc".istitle())            # Output: True
print("".istitle())                  # Output: False
```

## 23. isupper()
Checks if all cased characters are uppercase and there's at least one cased character.

```python
# All uppercase
print("HELLO".isupper())      # Output: True
print("HELLO WORLD".isupper()) # Output: True

# Contains lowercase
print("Hello".isupper())      # Output: False
print("HELLO world".isupper()) # Output: False

# Only non-cased characters
print("123".isupper())        # Output: False
print("!@#".isupper())        # Output: False

# Mixed cased and non-cased
print("HELLO123".isupper())   # Output: True
print("hello123".isupper())   # Output: False

# Empty string
print("".isupper())           # Output: False
```

## 24. join()
Joins elements of an iterable with the string as separator.

```python
separator = "-"

# List of strings
words = ["apple", "banana", "cherry"]
print(separator.join(words))  # Output: "apple-banana-cherry"

# Different separators
print(", ".join(words))       # Output: "apple, banana, cherry"
print("".join(words))         # Output: "applebananacherry"
print(" | ".join(words))      # Output: "apple | banana | cherry"

# Tuple
fruits = ("apple", "banana", "cherry")
print("-".join(fruits))       # Output: "apple-banana-cherry"

# String (each character becomes an element)
print("-".join("hello"))      # Output: "h-e-l-l-o"

# List with non-strings (will raise TypeError)
try:
    numbers = [1, 2, 3]
    print("-".join(numbers))
except TypeError:
    print("Cannot join non-string elements")

# Convert to strings first
numbers = [1, 2, 3]
print("-".join(map(str, numbers)))  # Output: "1-2-3"
```

## 25. ljust()
Left-justifies the string in a field of specified width.

```python
text = "Python"

# Basic left justification with spaces
print(text.ljust(10))         # Output: "Python    "
print(f"'{text.ljust(10)}'")  # Output: "'Python    '"

# With custom fill character
print(text.ljust(10, '*'))    # Output: "Python****"
print(text.ljust(10, '-'))    # Output: "Python----"

# Width less than string length
print(text.ljust(3))          # Output: "Python" (unchanged)

# Different widths
print(text.ljust(8, '.'))     # Output: "Python.."
print(text.ljust(12, '0'))    # Output: "Python000000"
```

## 26. lower()
Converts all cased characters to lowercase.

```python
# Basic conversion
text = "HELLO WORLD"
print(text.lower())           # Output: "hello world"

# Mixed case
text2 = "Hello World"
print(text2.lower())          # Output: "hello world"

# Already lowercase
text3 = "hello world"
print(text3.lower())          # Output: "hello world"

# With numbers and symbols
text4 = "Hello123!@#"
print(text4.lower())          # Output: "hello123!@#"

# Unicode characters
text5 = "CAFÉ"
print(text5.lower())          # Output: "café"
```

## 27. lstrip()
Removes leading whitespace or specified characters.

```python
text = "   Hello World   "

# Remove leading whitespace (default)
print(f"'{text.lstrip()}'")   # Output: "'Hello World   '"

# Remove specific characters
text2 = "xxxHello Worldxxx"
print(text2.lstrip('x'))      # Output: "Hello Worldxxx"

# Remove multiple characters
text3 = "abcHello Worldcba"
print(text3.lstrip('abc'))    # Output: "Hello Worldcba"

# Order doesn't matter in character set
print(text3.lstrip('bac'))    # Output: "Hello Worldcba"

# No leading characters to remove
text4 = "Hello World"
print(text4.lstrip('x'))      # Output: "Hello World"
```

## 28. maketrans()
Static method that returns a translation table for use with translate().

```python
# Character to character mapping
table = str.maketrans('aeiou', '12345')
text = "hello world"
print(text.translate(table))  # Output: "h2ll4 w4rld"

# With deletion parameter
table2 = str.maketrans('aeiou', '12345', 'xyz')
text2 = "hello world xyz"
print(text2.translate(table2))  # Output: "h2ll4 w4rld "

# Dictionary mapping
mapping = {'a': '1', 'e': '2', 'i': '3', 'o': '4', 'u': '5'}
table3 = str.maketrans(mapping)
print(text.translate(table3))  # Output: "h2ll4 w4rld"

# Unicode mapping
table4 = str.maketrans('àáâãäå', 'aaaaaa')
text4 = "café naïve"
print(text4.translate(table4))  # Output: "cafe naive" (if these characters were present)
```

## 29. partition()
Splits string into three parts: before separator, separator, after separator.

```python
text = "hello-world-python"

# Basic partition (first occurrence)
result = text.partition('-')
print(result)  # Output: ('hello', '-', 'world-python')

# Unpack the result
before, sep, after = text.partition('-')
print(f"Before: '{before}', Sep: '{sep}', After: '{after}'")

# Separator not found
text2 = "hello world"
result2 = text2.partition('-')
print(result2)  # Output: ('hello world', '', '')

# Empty string
result3 = "".partition('-')
print(result3)  # Output: ('', '', '')

# Separator at the beginning
text3 = "-hello-world"
result4 = text3.partition('-')
print(result4)  # Output: ('', '-', 'hello-world')
```

## 30. removeprefix()
Removes the specified prefix from the beginning of the string (Python 3.9+).

```python
text = "HelloWorld"

# Remove existing prefix
print(text.removeprefix("Hello"))    # Output: "World"

# Prefix doesn't exist
print(text.removeprefix("Hi"))       # Output: "HelloWorld"

# Empty prefix
print(text.removeprefix(""))         # Output: "HelloWorld"

# Partial match (no removal)
print(text.removeprefix("Hell"))     # Output: "oWorld"

# Complete string as prefix
print(text.removeprefix("HelloWorld"))  # Output: ""

# Case sensitive
print(text.removeprefix("hello"))    # Output: "HelloWorld"
```

## 31. removesuffix()
Removes the specified suffix from the end of the string (Python 3.9+).

```python
text = "HelloWorld"

# Remove existing suffix
print(text.removesuffix("World"))    # Output: "Hello"

# Suffix doesn't exist
print(text.removesuffix("Python"))   # Output: "HelloWorld"

# Empty suffix
print(text.removesuffix(""))         # Output: "HelloWorld"

# Partial match (no removal)
print(text.removesuffix("orld"))     # Output: "HelloW"

# Complete string as suffix
print(text.removesuffix("HelloWorld"))  # Output: ""

# Case sensitive
print(text.removesuffix("world"))    # Output: "HelloWorld"
```

## 32. replace()
Replaces occurrences of a substring with another string.

```python
text = "banana"

# Replace all occurrences
print(text.replace('a', 'o'))        # Output: "bonono"

# Replace with count limit
print(text.replace('a', 'o', 1))     # Output: "bonana"
print(text.replace('a', 'o', 2))     # Output: "bonona"

# Replace substring
text2 = "hello world hello"
print(text2.replace('hello', 'hi'))  # Output: "hi world hi"
print(text2.replace('hello', 'hi', 1))  # Output: "hi world hello"

# Replace with longer string
print(text.replace('a', 'XYZ'))      # Output: "bXYZnXYZnXYZ"

# Replace with empty string (removal)
print(text.replace('a', ''))         # Output: "bnn"

# Substring not found
print(text.replace('x', 'y'))        # Output: "banana"
```

## 33. rfind()
Finds the highest index of substring. Returns -1 if not found.

```python
text = "banana"

# Find last occurrence
print(text.rfind('a'))       # Output: 5 (last 'a')
print(text.rfind('an'))      # Output: 3 (last 'an')
print(text.rfind('na'))      # Output: 4 (last 'na')

# Not found
print(text.rfind('x'))       # Output: -1

# With start parameter
print(text.rfind('a', 2))    # Output: 5 (search from index 2 to end)
print(text.rfind('a', 4))    # Output: 5 (search from index 4 to end)

# With start and end parameters
print(text.rfind('a', 1, 4)) # Output: 3 (search in "ana")
print(text.rfind('a', 0, 3)) # Output: 1 (search in "ban")
```

## 34. rindex()
Like rfind() but raises ValueError if substring is not found.

```python
text = "banana"

# Find last occurrence
print(text.rindex('a'))      # Output: 5
print(text.rindex('an'))     # Output: 3

# With start parameter
print(text.rindex('a', 2))   # Output: 5

# Raises ValueError if not found
try:
    print(text.rindex('x'))
except ValueError as e:
    print(f"Error: {e}")  # Output: "Error: substring not found"
```

## 35. rjust()
Right-justifies the string in a field of specified width.

```python
text = "Python"

# Basic right justification with spaces
print(f"'{text.rjust(10)}'")  # Output: "'    Python'"

# With custom fill character
print(text.rjust(10, '*'))    # Output: "****Python"
print(text.rjust(10, '-'))    # Output: "----Python"

# Width less than string length
print(text.rjust(3))          # Output: "Python" (unchanged)

# Different widths
print(text.rjust(8, '.'))     # Output: "..Python"
print(text.rjust(12, '0'))    # Output: "000000Python"
```

## 36. rpartition()
Like partition() but splits at the last occurrence of separator.

```python
text = "hello-world-python"

# Partition at last occurrence
result = text.rpartition('-')
print(result)  # Output: ('hello-world', '-', 'python')

# Unpack the result
before, sep, after = text.rpartition('-')
print(f"Before: '{before}', Sep: '{sep}', After: '{after}'")

# Separator not found
text2 = "hello world"
result2 = text2.rpartition('-')
print(result2)  # Output: ('', '', 'hello world')

# Separator at the end
text3 = "hello-world-"
result3 = text3.rpartition('-')
print(result3)  # Output: ('hello-world', '-', '')
```

## 37. rsplit()
Splits string from the right at specified separator.

```python
text = "apple,banana,cherry,date"

# Split all occurrences
print(text.rsplit(','))       # Output: ['apple', 'banana', 'cherry', 'date']

# Limit splits from right
print(text.rsplit(',', 1))    # Output: ['apple,banana,cherry', 'date']
print(text.rsplit(',', 2))    # Output: ['apple,banana', 'cherry', 'date']

# Default separator (whitespace)
text2 = "hello world python"
print(text2.rsplit())         # Output: ['hello', 'world', 'python']
print(text2.rsplit(None, 1))  # Output: ['hello world', 'python']

# Multiple consecutive separators
text3 = "a,,b,c"
print(text3.rsplit(','))      # Output: ['a', '', 'b', 'c']
print(text3.rsplit(',', 1))   # Output: ['a,,b', 'c']
```

## 38. rstrip()
Removes trailing whitespace or specified characters.

```python
text = "   Hello World   "

# Remove trailing whitespace (default)
print(f"'{text.rstrip()}'")   # Output: "'   Hello World'"

# Remove specific characters
text2 = "xxxHello Worldxxx"
print(text2.rstrip('x'))      # Output: "xxxHello World"

# Remove multiple characters
text3 = "abcHello Worldcba"
print(text3.rstrip('abc'))    # Output: "abcHello World"

# Order doesn't matter in character set
print(text3.rstrip('bac'))    # Output: "abcHello World"

# No trailing characters to remove
text4 = "Hello World"
print(text4.rstrip('x'))      # Output: "Hello World"
```

## 39. split()
Splits string at specified separator.

```python
text = "apple,banana,cherry"

# Basic split
print(text.split(','))        # Output: ['apple', 'banana', 'cherry']

# Limit splits
print(text.split(',', 1))     # Output: ['apple', 'banana,cherry']
print(text.split(',', 2))     # Output: ['apple', 'banana', 'cherry']

# Default separator (any whitespace)
text2 = "hello   world\tpython\ncode"
print(text2.split())          # Output: ['hello', 'world', 'python', 'code']

# Split with maxsplit on whitespace
text3 = "one two three four"
print(text3.split(None, 2))   # Output: ['one', 'two', 'three four']

# Empty parts
text4 = "a,,b,c"
print(text4.