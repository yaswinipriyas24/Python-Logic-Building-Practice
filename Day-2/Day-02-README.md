# Day 2 – Python Coding Practice

This README contains my Day 2 Python coding practice. The focus is on building problem-solving skills using lists, loops, conditions, sets, and basic logic.

## Topics Covered
- Lists and list methods
- `for` loops and `while` loops
- `if`, `else`, and nested conditions
- Membership operators: `in` and `not in`
- Counters and temporary variables
- Sets and duplicate removal
- Nested loops
- List rotation
- Finding minimum and maximum values

---

## 1. Move Zeros to the End

**Problem:** Move all zeros to the end while keeping the order of non-zero elements unchanged.

**Input:** `[0, 1, 0, 3, 12, 0, 5]`

```python
numbers = [0, 1, 0, 3, 12, 0, 5]

result = []
zero_count = 0

for i in numbers:
    if i == 0:
        zero_count += 1
    else:
        result.append(i)

for i in range(zero_count):
    result.append(0)

print(result)
```

**Output:** `[1, 3, 12, 5, 0, 0, 0]`

**Understanding:**
- The first loop adds non-zero values to `result`.
- `zero_count` counts the zeros.
- The second loop adds the zeros at the end.
- A separate list avoids modifying the list while iterating over it.

---

## 2. Frequency Count

**Problem:** Count how many times each unique element appears.

**Input:** `[10, 20, 10, 30, 20, 10]`

```python
numbers = [10, 20, 10, 30, 20, 10]

unique = []

for i in numbers:
    if i not in unique:
        unique.append(i)

for i in unique:
    count = 0

    for j in numbers:
        if i == j:
            count += 1

    print(i, "appears", count, "times")
```

**Output:**
```text
10 appears 3 times
20 appears 2 times
30 appears 1 times
```

**Understanding:**
- `unique` stores each value once.
- The outer loop selects a unique value.
- `count = 0` resets the counter for each value.
- The inner loop checks every element in the original list.
- When values match, `count` increases by 1.

---

## 3. Find the Missing Number

**Problem:** Find the one missing number in a sequence that should contain all numbers from `1` to `n`.

**Input:** `[1, 2, 3, 5, 6]`

```python
numbers = [1, 2, 3, 5, 6]

n = len(numbers) + 1
expected_sum = n * (n + 1) // 2
actual_sum = sum(numbers)

missing = expected_sum - actual_sum

print(missing)
```

**Output:** `4`

**Understanding:**
- `len(numbers) + 1` gives the expected number of elements.
- `n * (n + 1) // 2` calculates the sum from `1` to `n`.
- `sum(numbers)` calculates the current sum.
- The difference is the missing number.

**Alternative: Find a gap in a sorted list**

```python
numbers = [1, 2, 3, 5, 6, 7]

for i in range(len(numbers) - 1):
    if numbers[i + 1] - numbers[i] > 1:
        missing = numbers[i] + 1
        print(missing)
```

**Output:** `4`

This alternative assumes the list is sorted and finds the first missing value between neighbouring elements.

---

## 4. Find Duplicate Elements

**Problem:** Find values that appear more than once. Print each duplicate only once.

**Input:** `[10, 20, 30, 10, 40, 20, 50, 30]`

```python
numbers = [10, 20, 30, 10, 40, 20, 50, 30]

unique = []
duplicates = []

for i in numbers:
    if i in unique:
        if i not in duplicates:
            duplicates.append(i)
    else:
        unique.append(i)

print(duplicates)
```

**Output:** `[10, 20, 30]`

**Understanding:**
- `unique` stores values seen for the first time.
- If a value is already in `unique`, it has appeared before.
- Add it to `duplicates` only if it is not already there.

---

## 5. Find Common Elements in Two Lists

**Problem:** Find elements present in both lists.

```python
A = [10, 20, 30, 40, 50]
B = [30, 40, 50, 60, 70]

common = []

for i in A:
    for j in B:
        if i == j and i not in common:
            common.append(i)

print(common)
```

**Output:** `[30, 40, 50]`

**Understanding:**
- The outer loop selects an element from `A`.
- The inner loop compares it with every element in `B`.
- If they match, add the value to `common`.
- `i not in common` prevents duplicate output.

**Simpler alternative using `in`:**

```python
common = []

for i in A:
    if i in B and i not in common:
        common.append(i)

print(common)
```

---

## 6. Find Pairs With a Given Sum

**Problem:** Find pairs whose sum equals the target. Print each pair only once.

**Input:** `numbers = [2, 4, 3, 5, 7, 8, 1]`, `target = 9`

```python
numbers = [2, 4, 3, 5, 7, 8, 1]
target = 9

for i in range(len(numbers)):
    for j in range(i + 1, len(numbers)):
        if numbers[i] + numbers[j] == target:
            print(numbers[i], numbers[j])
```

**Output:**
```text
2 7
4 5
8 1
```

**Understanding:**
- `range(len(numbers))` gives the list indexes.
- The outer loop selects the first element.
- `range(i + 1, len(numbers))` starts after the current index.
- This avoids comparing an element with itself and avoids reversed duplicate pairs.
- If the pair's sum equals `target`, print it.

---

## 7. Rotate a List by K Positions

### Right Rotation

Move the last element to the beginning, repeating the operation `k` times.

```python
numbers = [10, 20, 30, 40, 50]
k = 2

for i in range(k):
    last = numbers.pop()
    numbers.insert(0, last)

print(numbers)
```

**Output:** `[40, 50, 10, 20, 30]`

- `pop()` removes and returns the last element.
- `insert(0, last)` inserts it at the beginning.

### Left Rotation

Move the first element to the end, repeating the operation `k` times.

```python
numbers = [10, 20, 30, 40, 50]
k = 2

for i in range(k):
    first = numbers.pop(0)
    numbers.append(first)

print(numbers)
```

**Output:** `[30, 40, 50, 10, 20]`

- `pop(0)` removes and returns the first element.
- `append(first)` adds it to the end.

For a non-empty list, `k = k % len(numbers)` can avoid unnecessary rotations when `k` is larger than the list length.

---

## 8. Maximum Difference

**Problem:** Find the largest value minus the smallest value.

```python
numbers = [2, 7, 1, 15, 3, 10]

smallest = numbers[0]
largest = numbers[0]

for i in numbers:
    if i < smallest:
        smallest = i

    if i > largest:
        largest = i

maximum_difference = largest - smallest

print(maximum_difference)
```

**Output:** `14`

**Understanding:**
- Start by treating the first element as both the smallest and largest.
- Update `smallest` when a smaller value is found.
- Update `largest` when a larger value is found.
- Subtract the smallest from the largest.

This version does not require the larger value to appear after the smaller value.

---

## 9. Move Negative Numbers to the Beginning

**Problem:** Move negative values to the beginning. Keep the relative order of negative and non-negative values.

```python
numbers = [10, -5, 0, -8, 30, -2, 15]

negative = []
non_negative = []

for i in numbers:
    if i < 0:
        negative.append(i)
    else:
        non_negative.append(i)

result = negative + non_negative

print(result)
```

**Output:** `[-5, -8, -2, 10, 0, 30, 15]`

**Understanding:**
- If `i < 0`, add the value to `negative`.
- Otherwise, add it to `non_negative`.
- Zero is not negative, so it goes into `non_negative`.
- `negative + non_negative` joins the two lists.

---

## 10. Longest Consecutive Sequence

**Problem:** Find the length of the longest sequence of consecutive numbers. The numbers do not need to be next to each other in the original list.

**Input:** `[100, 4, 200, 1, 3, 2]`

```python
numbers = [100, 4, 200, 1, 3, 2]

number_set = set(numbers)

longest = 0

for i in number_set:
    if i - 1 not in number_set:
        current = i
        count = 0

        while current in number_set:
            count += 1
            current += 1

        if count > longest:
            longest = count

print("Longest consecutive sequence length:", longest)
```

**Output:**
```text
Longest consecutive sequence length: 4
```

The longest sequence is `[1, 2, 3, 4]`.

### Why convert the list into a set?

```python
number_set = set(numbers)
```

- A set stores unique values, so duplicates are removed.
- Checking whether a value exists using `in` is generally faster with a set than with a list.
- Sets do not support indexing and do not guarantee the same order as a list.

### The `for` loop – Find a starting number

```python
for i in number_set:
    if i - 1 not in number_set:
```

- The `for` loop checks each value in the set.
- `i - 1 not in number_set` checks whether the previous number is missing.
- If the previous number is missing, `i` is the start of a consecutive sequence.

For example, when `i = 1`, the previous number is `0`. Since `0` is not in the set, `1` is a starting number.

### The `while` loop – Count consecutive numbers

```python
current = i
count = 0

while current in number_set:
    count += 1
    current += 1
```

- `current` starts at the sequence's starting number.
- `count` is temporary; it counts the current sequence.
- The loop continues while `current` exists in the set.
- `count += 1` increases the count.
- `current += 1` moves to the next number.

For the sequence starting at `1`:

| `current` | Present in set? | `count` |
|---:|---|---:|
| 1 | Yes | 1 |
| 2 | Yes | 2 |
| 3 | Yes | 3 |
| 4 | Yes | 4 |
| 5 | No – stop | 4 |

### Difference between `count` and `longest`

- `count` is temporary. It counts the current consecutive sequence.
- `longest` stores the highest sequence length found so far.

```python
if count > longest:
    longest = count
```

If the current sequence is longer than the previous longest sequence, update `longest`.

### Difference between the two loops

| `for` loop | `while` loop |
|---|---|
| Checks each number in the set. | Checks consecutive numbers from a starting point. |
| Helps find a sequence's starting number. | Counts the length of that sequence. |
| Iterates through the collection. | Continues while its condition is true. |

---

## Important Python Concepts Practised

| Concept | Purpose |
|---|---|
| `append()` | Adds an element to the end of a list. |
| `insert()` | Adds an element at a specified index. |
| `pop()` | Removes and returns an element. |
| `len()` | Returns the number of elements. |
| `sum()` | Calculates the sum of values. |
| `range()` | Generates numbers, often used for loop indexes. |
| `in` | Checks whether an element exists in a collection. |
| `not in` | Checks whether an element does not exist in a collection. |
| `set()` | Creates a set and removes duplicate values. |
| `while` | Repeats a block while a condition is true. |

## Day 2 Key Learnings

1. Use a separate list when rearranging elements without modifying the list being iterated over.
2. Reset a counter inside the loop when counting a new item.
3. Use nested loops to compare elements from two collections.
4. Use `i + 1` as the inner-loop starting index to avoid repeated pairs.
5. Understand the difference between left rotation and right rotation.
6. Use `if` and `else` to separate negative and non-negative numbers.
7. Use a set for unique values and frequent membership checks.
8. Understand the difference between a temporary counter (`count`) and a maximum tracker (`longest`).

---

**Day 2 completed – Python coding logic practice.**
