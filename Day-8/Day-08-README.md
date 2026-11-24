# Day 8 – Python Logic Building Practice

**Focus:** Two pointers, equilibrium index, three pointers, dictionary-based frequency counting, and removing duplicates from arrays.

This README contains 6 practice problems with Python solutions and key logic notes.

---

## Q1. Reverse an Array In Place

**Problem:** Reverse the elements of an array by swapping values from the beginning and end. Do not use `reverse()` or slicing.

**Input:**
```python
numbers = [10, 20, 30, 40, 50]
```

**Output:**
```python
[50, 40, 30, 20, 10]
```

**Solution:**
```python
def reverse_array_in_place(arr):
    left = 0
    right = len(arr) - 1

    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1

    return arr


numbers = [10, 20, 30, 40, 50]
print(reverse_array_in_place(numbers))
```

**Key idea:** Use two pointers. `left` starts at the first index and `right` starts at the last index. Swap those elements, then move `left` forward and `right` backward. Stop when the pointers meet or cross. The original list is modified.

---

## Q2. Find the Equilibrium Index

**Problem:** Find an index where the sum of the elements before it equals the sum of the elements after it. The element at the candidate index is excluded from both sums. Return `-1` if no equilibrium index exists.

**Input:**
```python
numbers = [-7, 1, 5, 2, -4, 3, 0]
```

**Output:**
```text
3
```

**Solution:**
```python
def equilibrium_index(numbers):
    for i in range(len(numbers)):
        left_sum = 0
        right_sum = 0

        # Calculate the sum before index i
        for j in range(i):
            left_sum += numbers[j]

        # Calculate the sum after index i
        for j in range(i + 1, len(numbers)):
            right_sum += numbers[j]

        if left_sum == right_sum:
            return i

    return -1


numbers = [-7, 1, 5, 2, -4, 3, 0]
print(equilibrium_index(numbers))
```

**Key idea:** Test every index as a possible equilibrium index. `range(i)` visits indexes to the left. `range(i + 1, len(numbers))` visits indexes to the right. The current element is not included in either sum. This beginner-friendly nested-loop solution takes O(n²) time.

---

## Q3. Sort an Array of 0s, 1s, and 2s

**Problem:** Sort an array containing only `0`, `1`, and `2` without using `sort()` or `sorted()`.

**Input:**
```python
numbers = [2, 0, 1, 2, 1, 0, 1]
```

**Output:**
```python
[0, 0, 1, 1, 1, 2, 2]
```

**Solution – Dutch National Flag Algorithm:**
```python
def sort_colors(arr):
    low = 0
    mid = 0
    high = len(arr) - 1

    while mid <= high:
        if arr[mid] == 0:
            arr[low], arr[mid] = arr[mid], arr[low]
            low += 1
            mid += 1

        elif arr[mid] == 1:
            mid += 1

        else:  # arr[mid] == 2
            arr[mid], arr[high] = arr[high], arr[mid]
            high -= 1

    return arr


numbers = [2, 0, 1, 2, 1, 0, 1]
print(sort_colors(numbers))
```

**Key idea:** Use three pointers. `low` marks where the next `0` belongs, `mid` examines the current value, and `high` marks where the next `2` belongs. For `0`, swap with `low` and move both `low` and `mid`. For `1`, move `mid`. For `2`, swap with `high` and move only `high`; do not move `mid` because the value swapped in from the right has not been checked yet. This algorithm takes O(n) time and O(1) extra space.

---

## Q4. Find Repeating and Non-Repeating Elements

**Problem:** Find all values that appear more than once and all values that appear exactly once.

**Input:**
```python
numbers = [1, 2, 3, 2, 4, 5, 1, 6]
```

**Output:**
```text
Repeating: [1, 2]
Non-repeating: [3, 4, 5, 6]
```

**Solution – Dictionary Frequency Counting:**
```python
def find_repeating(numbers):
    frequency = {}

    for value in numbers:
        if value not in frequency:
            frequency[value] = 1
        else:
            frequency[value] += 1

    repeating = []
    non_repeating = []

    for key, count in frequency.items():
        if count > 1:
            repeating.append(key)
        else:
            non_repeating.append(key)

    return repeating, non_repeating


numbers = [1, 2, 3, 2, 4, 5, 1, 6]
repeating, non_repeating = find_repeating(numbers)

print("Repeating:", repeating)
print("Non-repeating:", non_repeating)
```

**Key idea:** The first loop builds a dictionary where each number is a key and its occurrence count is the value. The second loop separates keys with counts greater than 1 from keys with a count of 1. Avoid naming a variable `dict`, because `dict` is a Python built-in type.

---

## Q5. Remove Duplicates from an Unsorted Array

**Problem:** Remove duplicate values while keeping the first occurrence and preserving the original order.

**Input:**
```python
numbers = [1, 2, 3, 2, 4, 5, 1, 6]
```

**Output:**
```python
[1, 2, 3, 4, 5, 6]
```

**Solution:**
```python
def remove_duplicates(numbers):
    unique = []

    for value in numbers:
        if value not in unique:
            unique.append(value)

    return unique


numbers = [1, 2, 3, 2, 4, 5, 1, 6]
print(remove_duplicates(numbers))
```

**Key idea:** Visit each value in the original list. Add it to `unique` only if it is not already present. This preserves the order of first occurrences. The membership check makes the worst-case time complexity O(n²).

---

## Q6. Remove Duplicates from a Sorted Array

**Problem:** Remove duplicate values from a sorted array using two pointers. Keep the unique values in their original sorted order.

**Input:**
```python
numbers = [1, 1, 2, 2, 3, 4, 4, 5]
```

**Output:**
```python
[1, 2, 3, 4, 5]
```

**Solution – Two Pointers:**
```python
def remove_duplicates_sorted(numbers):
    if not numbers:
        return []

    slow = 0
    fast = 1

    while fast < len(numbers):
        if numbers[slow] != numbers[fast]:
            slow += 1
            numbers[slow] = numbers[fast]

        fast += 1

    return numbers[:slow + 1]


numbers = [1, 1, 2, 2, 3, 4, 4, 5]
print(remove_duplicates_sorted(numbers))
```

**Key idea:** This method relies on the array already being sorted, so duplicates are next to each other. `slow` marks the position of the last unique value. `fast` scans the remaining values. When a new value is found, move `slow` forward and copy that value into its position. Finally, return the portion of the list containing the unique values. The scan takes O(n) time and uses O(1) auxiliary space; the returned slice creates a list containing the result.

---

## Day 8 – Concepts Practised

- Two Pointers for reversing an array in place
- Equilibrium index using left and right sums
- Nested loops and index ranges
- Dutch National Flag algorithm with three pointers
- Dictionary-based frequency counting
- Separating repeating and non-repeating elements
- Removing duplicates from an unsorted array
- Two Pointers for removing duplicates from a sorted array
- Swapping, updating pointer positions, and handling loop conditions

**Day 8 progress: 6 questions covered.**
