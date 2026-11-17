# Day 4 – Python Logic Building Practice

Day 4 focuses on **Python dictionaries** and using key-value pairs for counting, searching, comparing, and merging data.

## Topics Covered
- Creating and accessing dictionaries
- Adding, updating, and deleting key-value pairs
- Frequency counting for numbers, characters, and words
- Finding the maximum value and its key
- Merging dictionaries
- Checking anagrams
- Finding repeated elements
- Solving Two Sum with a dictionary

---

## 1. Create and Access a Dictionary

**Problem:** Create an employee dictionary and access its values.

```python
employee = {
    "name": "Rahul",
    "age": 25,
    "department": "IT",
    "salary": 30000
}

print(employee["name"])
print(employee["age"])
print(employee["department"])
print(employee["salary"])
```

**Output:**
```text
Rahul
25
IT
30000
```

**Understanding:** A dictionary stores key-value pairs. `"name"` is a key, and `"Rahul"` is its value. Use `employee["name"]` to access the value. Iterating directly with `for key in employee` visits the keys.

---

## 2. Add, Update, and Delete Dictionary Elements

**Problem:** Add a product, update a price, and delete a product.

```python
products = {
    "laptop": 50000,
    "mobile": 20000,
    "tablet": 15000
}

products["keyboard"] = 2000  # Add
products["mobile"] = 25000   # Update
del products["tablet"]       # Delete

print(products)
```

**Output:**
```python
{'laptop': 50000, 'mobile': 25000, 'keyboard': 2000}
```

**Understanding:**
- `products["keyboard"] = 2000` adds a new key-value pair.
- Assigning to an existing key updates its value.
- `del products["tablet"]` removes the key and its value.

---

## 3. Frequency Count Using a Dictionary

**Problem:** Count how many times each number appears in a list.

```python
numbers = [10, 20, 10, 30, 20, 10]
frequency = {}

for i in numbers:
    if i in frequency:
        frequency[i] += 1
    else:
        frequency[i] = 1

print(frequency)
```

**Output:**
```python
{10: 3, 20: 2, 30: 1}
```

**Understanding:**
- `frequency` starts as an empty dictionary.
- `if i in frequency` checks whether the number is already a key.
- If it exists, increase its count.
- Otherwise, add it with an initial count of `1`.

**Remember this reusable pattern:**
```python
if key in frequency:
    frequency[key] += 1
else:
    frequency[key] = 1
```

---

## 4. Character Frequency Using a Dictionary

**Problem:** Count how many times each character appears in a string.

```python
text = "banana"
frequency = {}

for i in text:
    if i in frequency:
        frequency[i] += 1
    else:
        frequency[i] = 1

print(frequency)
```

**Output:**
```python
{'b': 1, 'a': 3, 'n': 2}
```

**Understanding:** A string can be iterated over directly. Each character becomes a dictionary key; repeated characters increase the count. Converting the string with `list(text)` is optional.

**Note:** Dictionary keys are case-sensitive. `"A"` and `"a"` are different keys. Use `text.lower()` first for case-insensitive counting.

---

## 5. Word Frequency in a Sentence

**Problem:** Count how many times each word appears.

```python
sentence = "python is easy and python is interesting"
words = sentence.split()
frequency = {}

for i in words:
    if i in frequency:
        frequency[i] += 1
    else:
        frequency[i] = 1

print(frequency)
```

**Output:**
```python
{'python': 2, 'is': 2, 'easy': 1, 'and': 1, 'interesting': 1}
```

**Understanding:**
- `.split()` separates the sentence into a list of words.
- The frequency-counting pattern is the same as Q3 and Q4.
- The input changes, but the dictionary logic stays the same.

---

## 6. Find the Key With the Maximum Value

**Problem:** Find the student who scored the highest marks.

```python
marks = {
    "A": 85,
    "B": 92,
    "C": 78,
    "D": 95
}

max_marks = 0
top_student = ""

for i in marks:
    if marks[i] > max_marks:
        max_marks = marks[i]
        top_student = i

print("Top student name:", top_student)
print("Highest marks scored:", max_marks)
```

**Output:**
```text
Top student name: D
Highest marks scored: 95
```

**Understanding:**
- `for i in marks` iterates over the dictionary's keys.
- `i` is the current key (student name).
- `marks[i]` retrieves the value (marks).
- `max_marks` stores the largest value found so far.
- `top_student` stores the key associated with that value.
- When an `if` condition is false, Python skips that `if` block and continues to the next key.

**Useful dictionary iteration patterns:**
```python
for key in marks:
    print(key)                 # Keys

for value in marks.values():
    print(value)               # Values

for key, value in marks.items():
    print(key, value)          # Both keys and values
```

With `>`, the first student encountered is kept if there is a tie for the highest marks.

---

## 7. Merge Two Dictionaries

**Problem:** Merge two dictionaries. If a key appears in both, add the values.

```python
dict1 = {"a": 10, "b": 20}
dict2 = {"b": 30, "c": 40}
result = {}

# Process keys from the first dictionary
for i in dict1:
    if i in dict2:
        result[i] = dict1[i] + dict2[i]
    else:
        result[i] = dict1[i]

# Add keys that appear only in the second dictionary
for i in dict2:
    if i not in dict1:
        result[i] = dict2[i]

print(result)
```

**Output:**
```python
{'a': 10, 'b': 50, 'c': 40}
```

**Understanding:**
- The first loop visits keys in `dict1`.
- If a key also exists in `dict2`, add the two values.
- Otherwise, copy the value from `dict1`.
- The second loop adds keys found only in `dict2`.
- Here, `"b"` becomes `20 + 30 = 50`.

---

## 8. Check Whether Two Strings Are Anagrams

**Problem:** Check whether two strings contain the same characters with the same frequencies, regardless of character order.

```python
str1 = "listen"
str2 = "silent"

freq1 = {}
freq2 = {}

# Count characters in the first string
for i in str1:
    if i in freq1:
        freq1[i] += 1
    else:
        freq1[i] = 1

# Count characters in the second string
for i in str2:
    if i in freq2:
        freq2[i] += 1
    else:
        freq2[i] = 1

if freq1 == freq2:
    print("Anagram")
else:
    print("Not anagram")
```

**Output:**
```text
Anagram
```

**Understanding:**
- Build a frequency dictionary for each string.
- `freq1 == freq2` compares the complete dictionaries: their keys and corresponding counts.
- The order of keys does not matter.
- `freq1[i] == freq2[i]` would compare only one character's frequency, not the complete dictionaries.

This solution is case-sensitive and includes spaces as characters. Normalize the strings first when a case-insensitive comparison is needed.

---

## 9. Find the First Repeated Element

**Problem:** Find the first number that appears more than once while scanning from left to right.

```python
numbers = [10, 20, 30, 40, 20, 50, 10]
seen = {}

for i in numbers:
    if i in seen:
        print(i, "is the first repeating element")
        break
    else:
        seen[i] = True
```

**Output:**
```text
20 is the first repeating element
```

**Understanding:**
- `seen` remembers numbers that have already been visited.
- `if i in seen` checks whether the current number is already a dictionary key.
- If it exists, this is the first repeated number.
- `break` stops the loop.
- Otherwise, `seen[i] = True` records that the number has been seen. `True` is simply a marker value.

**Dry run:**

| Current number | Already in `seen`? | Action |
|---:|---|---|
| 10 | No | Store 10 |
| 20 | No | Store 20 |
| 30 | No | Store 30 |
| 40 | No | Store 40 |
| 20 | Yes | Print 20 and stop |

---

## 10. Two Sum Using a Dictionary

**Problem:** Find two numbers whose sum equals the target. Use a dictionary to remember previously visited numbers instead of comparing every pair with nested loops.

### Find the first matching pair

```python
numbers = [2, 7, 11, 15]
target = 9
seen = {}

for i in numbers:
    needed = target - i

    if needed in seen:
        print("Pair found:", needed, i)
        break

    seen[i] = True
```

**Output:**
```text
Pair found: 2 7
```

**Understanding:**
- `seen` stores numbers already visited.
- `needed = target - i` calculates the number required to reach the target.
- `if needed in seen` checks whether that required number has already appeared.
- If it has, print the pair and stop.
- Otherwise, store the current number in `seen`.
- Store the current number after checking `needed`, so it is not matched with itself.

### Find all matching pairs

If the list contains more than one valid pair, remove `break` so the loop continues.

```python
numbers = [2, 7, 11, 15, 5, 4]
target = 9
seen = {}

for i in numbers:
    needed = target - i

    if needed in seen:
        print("Pair found:", needed, i)

    seen[i] = True
```

**Output:**
```text
Pair found: 2 7
Pair found: 5 4
```

**Remember:**
- With `break`, the loop stops after the first pair.
- Without `break`, it continues checking the remaining numbers and can find more pairs.

---

## Important Python Dictionary Concepts Practised

| Concept | Purpose |
|---|---|
| `{}` | Creates an empty dictionary |
| `dictionary[key]` | Accesses the value for a key |
| `key in dictionary` | Checks whether a key exists |
| `dictionary[key] = value` | Adds a key or updates its value |
| `del dictionary[key]` | Deletes a key-value pair |
| `dictionary.keys()` | Returns the dictionary's keys |
| `dictionary.values()` | Returns the dictionary's values |
| `dictionary.items()` | Provides key-value pairs |
| `dictionary.get(key)` | Gets a value for a key safely |
| `for key in dictionary` | Iterates over dictionary keys |
| `frequency[key] += 1` | Increases an existing frequency count |
| `break` | Stops a loop when a condition is met |

## Day 4 Key Learnings

1. A dictionary stores information as key-value pairs.
2. Iterating directly over a dictionary gives its keys.
3. Use `dictionary[key]` to access the corresponding value.
4. Use `.values()` to iterate over values and `.items()` to access keys and values together.
5. The same frequency-counting pattern works for numbers, characters, and words.
6. Use a maximum tracker to remember the highest value and its associated key.
7. When merging dictionaries, check for shared keys before deciding whether to add or copy a value.
8. Compare complete frequency dictionaries to check whether two strings are anagrams.
9. Use a dictionary to remember previously visited elements when searching for repeated values.
10. In Two Sum, calculate the needed number and check whether it has already been seen.

---

**Day 4 completed – Python dictionary logic practice.**

*I will continue practising, reviewing my solutions, and adding new learning notes as I progress.*
