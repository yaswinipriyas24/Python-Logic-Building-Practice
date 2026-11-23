# Day 7 – Python Logic Building Practice

**Focus:** Nested lists, matrix operations, sliding window, dictionaries, anagrams, and stacks.

This README contains 10 practice problems with Python solutions and key logic notes.

---

## Q1. Flatten a Nested List

**Problem:** Convert a list of lists into one flat list.

**Input:**
```python
numbers = [[1, 2], [3, 4], [5, 6]]
```

**Output:**
```python
[1, 2, 3, 4, 5, 6]
```

**Solution:**
```python
def flatten_list(numbers):
    result = []

    for inner_list in numbers:
        for value in inner_list:
            result.append(value)

    return result


numbers = [[1, 2], [3, 4], [5, 6]]
print(flatten_list(numbers))
```

**Key idea:** The outer loop selects each inner list. The inner loop visits each value in that list and appends it to `result`.

---

## Q2. Find the Sum of Each Inner List

**Problem:** Calculate the sum of every inner list separately.

**Input:**
```python
numbers = [[1, 2], [3, 4], [5, 6]]
```

**Output:**
```python
[3, 7, 11]
```

**Solution:**
```python
def inner_sum(numbers):
    result = []

    for inner_list in numbers:
        total = 0
        for value in inner_list:
            total += value
        result.append(total)

    return result


numbers = [[1, 2], [3, 4], [5, 6]]
print(inner_sum(numbers))
```

**Key idea:** Reset `total = 0` inside the outer loop so each inner list gets its own sum. Use `total` rather than `sum` as a variable name because `sum()` is a Python built-in function.

---

## Q3. Find the Largest Element in Each Inner List

**Problem:** Find the maximum value in every inner list.

**Input:**
```python
numbers = [[10, 20, 5], [30, 15, 25], [8, 12, 6]]
```

**Output:**
```python
[20, 30, 12]
```

**Solution:**
```python
def largest_in_nested_list(numbers):
    result = []

    for inner_list in numbers:
        if not inner_list:
            continue  # Skip an empty inner list

        largest = inner_list[0]

        for value in inner_list:
            if value > largest:
                largest = value

        result.append(largest)

    return result


numbers = [[10, 20, 5], [30, 15, 25], [8, 12, 6]]
print(largest_in_nested_list(numbers))
```

**Key idea:** Start with the first value as the current largest. Compare every value in that inner list and update `largest` when a bigger value is found. Then append the answer before moving to the next inner list.

---

## Q4. Find the Sum of Each Row and Column in a Matrix

**Problem:** Calculate every row sum and every column sum.

**Input:**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

**Output:**
```text
Row sums: [6, 15, 24]
Column sums: [12, 15, 18]
```

**Solution:**
```python
def sum_matrix(matrix):
    if not matrix or not matrix[0]:
        return [], []

    row_sums = []
    column_sums = []

    # Calculate row sums
    for row in matrix:
        total = 0
        for value in row:
            total += value
        row_sums.append(total)

    # Calculate column sums
    for col in range(len(matrix[0])):
        total = 0
        for row in range(len(matrix)):
            total += matrix[row][col]
        column_sums.append(total)

    return row_sums, column_sums


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

row_sums, column_sums = sum_matrix(matrix)
print("Row sums:", row_sums)
print("Column sums:", column_sums)
```

**Key idea:** `len(matrix)` gives the number of rows. `len(matrix[0])` gives the number of columns (assuming a rectangular matrix). For a row value use `matrix[row][col]`; for column totals, keep `col` fixed while moving through each row.

---

## Q5. Transpose a Matrix

**Problem:** Convert rows into columns and columns into rows.

**Input:**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]
```

**Output:**
```python
[[1, 4], [2, 5], [3, 6]]
```

**Solution:**
```python
def transpose(matrix):
    if not matrix:
        return []

    result = []

    for col in range(len(matrix[0])):
        new_row = []
        for row in range(len(matrix)):
            new_row.append(matrix[row][col])
        result.append(new_row)

    return result


matrix = [
    [1, 2, 3],
    [4, 5, 6]
]
print(transpose(matrix))
```

**Key idea:** The outer loop selects a column from the original matrix. The inner loop collects that column's values into `new_row`. Append the completed row to `result`. The temporary list is important; appending every value directly to `result` would produce a flat list.

---

## Q6. Find the Main Diagonal Sum of a Matrix

**Problem:** Add the elements on the main diagonal of a square matrix.

**Input:**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

**Output:**
```text
Diagonal Sum: 15
```

**Solution:**
```python
def diagonal_sum(matrix):
    total = 0

    for i in range(len(matrix)):
        total += matrix[i][i]

    return total


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print("Diagonal Sum:", diagonal_sum(matrix))
```

**Key idea:** The main diagonal uses the same row and column index: `matrix[0][0]`, `matrix[1][1]`, `matrix[2][2]`. This solution assumes a square matrix.

---

## Q7. Find Common Elements in Three Lists

**Problem:** Find the values present in all three lists.

**Input:**
```python
A = [1, 2, 3, 4, 5]
B = [2, 3, 5, 6]
C = [3, 5, 7, 8]
```

**Output:**
```python
[3, 5]
```

**Solution:**
```python
def common_elements(list1, list2, list3):
    result = []

    for value in list1:
        if value in list2 and value in list3 and value not in result:
            result.append(value)

    return result


A = [1, 2, 3, 4, 5]
B = [2, 3, 5, 6]
C = [3, 5, 7, 8]
print(common_elements(A, B, C))
```

**Key idea:** Check whether each value from the first list is also present in the second and third lists. `value not in result` prevents duplicate answers. A nested-loop approach also works, but this membership-check version is simpler.

---

## Q8. Longest Substring Without Repeating Characters

**Problem:** Find the length of the longest continuous substring that has no repeated characters.

**Input:**
```python
text = "abcabcbb"
```

**Output:**
```text
Longest substring length: 3
```

The substring `"abc"` has three unique characters.

**Solution – Sliding Window:**
```python
def longest_substring(text):
    char_set = set()
    left = 0
    max_length = 0

    for right in range(len(text)):
        while text[right] in char_set:
            char_set.remove(text[left])
            left += 1

        char_set.add(text[right])

        current_length = right - left + 1
        max_length = max(max_length, current_length)

    return max_length


text = "abcabcbb"
print("Longest substring length:", longest_substring(text))
```

**Key idea:** `right` expands the window one character at a time. If the new character is already in `char_set`, move `left` forward and remove characters until the duplicate is gone. Add the new character, calculate the window length, and update the maximum.

**Important formula:** `right - left + 1` counts both endpoint positions. For example, if `left = 2` and `right = 5`, the window length is `5 - 2 + 1 = 4`.

---

## Q9. Group Anagrams Together

**Problem:** Group words that contain the same characters, even when their character order differs.

**Input:**
```python
words = ["eat", "tea", "tan", "ate", "nat", "bat"]
```

**Output:**
```python
[["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]
```

**Solution:**
```python
def group_anagrams(words):
    groups = {}

    for word in words:
        key = "".join(sorted(word))

        if key in groups:
            groups[key].append(word)
        else:
            groups[key] = [word]

    return list(groups.values())


words = ["eat", "tea", "tan", "ate", "nat", "bat"]
print(group_anagrams(words))
```

**Key idea:** `sorted(word)` sorts a word's characters. `"".join(...)` turns that character list into a string key. Anagrams produce the same key. If the key exists, append the word to its group; otherwise, create a new group with `[word]`. `list(groups.values())` returns only the grouped lists.

---

## Q10. Check Whether Parentheses Are Balanced

**Problem:** Check whether `()`, `{}`, and `[]` are correctly matched and nested.

**Examples:**
```python
"{[()]}"  # Balanced
"{[(])}"  # Not Balanced
"((())"   # Not Balanced
```

**Solution – Stack:**
```python
def is_balanced(text):
    stack = []
    pairs = {
        ')': '(',
        '}': '{',
        ']': '['
    }

    for char in text:
        if char in "({[":
            stack.append(char)

        elif char in ")}]":
            if not stack:
                return False

            if stack[-1] == pairs[char]:
                stack.pop()
            else:
                return False

    return len(stack) == 0


text = "{[()]}"
if is_balanced(text):
    print("Balanced")
else:
    print("Not Balanced")
```

**Key idea:** A stack follows LIFO (Last In, First Out). Push opening brackets using `append()`. For a closing bracket, check the latest opening bracket using `stack[-1]`. If it matches, remove it using `pop()`. If there is no opening bracket or it does not match, return `False`. At the end, the stack must be empty.

---

## Day 7 – Concepts Practised

- Nested lists and nested `for` loops
- Resetting counters for each inner list
- Indexing in a 2D matrix: `matrix[row][col]`
- `len(matrix)` (row count) vs. `len(matrix[0])` (column count)
- Row sums, column sums, transpose, and diagonal sum
- List membership and avoiding duplicate results
- Sliding Window with two pointers and a set
- The window-length formula: `right - left + 1`
- Dictionaries as grouping keys for anagrams
- `sorted()`, `"".join()`, dictionary values, and lists
- Stack operations: `append()`, `pop()`, and `stack[-1]`

**Day 7 progress: 10 questions covered.**
