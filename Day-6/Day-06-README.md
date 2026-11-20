# Day 6 – Python Logic Building Practice

**Focus:** Lists, loops, indexing, strings, dictionaries, functions, and step-by-step problem solving.

Day 6 contains 10 mixed practice problems. The solutions below are reference implementations. Questions 1–9 were discussed during practice; Question 10 is included as a reference because its independent attempt is still pending.

---

## Q1. Count Positive, Negative, and Zero Numbers

**Problem:** Count how many numbers in a list are positive, negative, and zero.

**Input**
```python
numbers = [10, -5, 0, 8, -2, 0]
```

**Expected output**
```text
Positive Count: 2
Negative Count: 2
Zero count: 2
```

**Solution**
```python
def count_numbers(numbers):
    positive_count = 0
    negative_count = 0
    zero_count = 0

    for i in numbers:
        if i > 0:
            positive_count += 1
        elif i < 0:
            negative_count += 1
        else:
            zero_count += 1

    return positive_count, negative_count, zero_count


numbers = [10, -5, 0, 8, -2, 0]
positive_count, negative_count, zero_count = count_numbers(numbers)

print("Positive Count:", positive_count)
print("Negative Count:", negative_count)
print("Zero count:", zero_count)
```

**Key concepts:** Counters, `if/elif/else`, functions, and returning multiple values. Python returns the three values as a tuple, which can be unpacked into three variables.

---

## Q2. Check Whether a List Is Sorted

**Problem:** Check whether a list is in ascending order without using `sort()` or `sorted()`.

**Input**
```python
numbers = [1, 2, 2, 5, 8]
```

**Expected output**
```text
List is sorted in ascending order
```

**Solution**
```python
def is_sorted(numbers):
    for i in range(len(numbers) - 1):
        if numbers[i] > numbers[i + 1]:
            return False

    return True


numbers = [1, 2, 2, 5, 8]
result = is_sorted(numbers)

if result:
    print("List is sorted in ascending order")
else:
    print("List is not sorted in ascending order")
```

**How it works:** Compare each element with the next one. If the current element is greater than the next element, ascending order is broken, so return `False`. If the loop finishes without finding a problem, return `True`.

`range(len(numbers) - 1)` is used because the code accesses `numbers[i + 1]`. The final element has no next element to compare with. An empty or one-element list returns `True` because there is no out-of-order pair.

**Key concepts:** Indexing, adjacent-element comparison, early return, and boolean results.

---

## Q3. Find the Third Largest Distinct Element

**Problem:** Find the third-largest *distinct* value. Repeated values should be counted only once.

**Input**
```python
numbers = [10, 40, 20, 50, 30, 50]
```

**Expected output**
```text
Third Largest Distinct number: 30
```

**Solution**
```python
def third_largest(numbers):
    largest = float('-inf')
    second_largest = float('-inf')
    third_largest_value = float('-inf')

    for i in numbers:
        if i > largest:
            third_largest_value = second_largest
            second_largest = largest
            largest = i
        elif i != largest and i > second_largest:
            third_largest_value = second_largest
            second_largest = i
        elif i != largest and i != second_largest and i > third_largest_value:
            third_largest_value = i

    if third_largest_value == float('-inf'):
        return None

    return third_largest_value


numbers = [10, 40, 20, 50, 30, 50]
result = third_largest(numbers)
print("Third Largest Distinct number:", result)
```

**How it works:** Keep track of the largest, second-largest, and third-largest distinct values. When a new largest value is found, shift the previous largest values down one position. When a value fits between the current largest values, update the appropriate position.

`float('-inf')` is a starting value smaller than ordinary numbers, so the solution also works when the list contains negative numbers. The function returns `None` when fewer than three distinct values are available.

**Key concepts:** Tracking multiple maximum values, distinct values, `elif`, and sentinel values.

---

## Q4. Remove All Occurrences of a Given Element

**Problem:** Remove every occurrence of `target` and return the remaining elements.

**Input**
```python
numbers = [1, 2, 3, 2, 4, 2]
target = 2
```

**Expected output**
```python
[1, 3, 4]
```

**Solution**
```python
def remove_element(numbers, target):
    result = []

    for i in numbers:
        if i != target:
            result.append(i)

    return result


numbers = [1, 2, 3, 2, 4, 2]
target = 2
result = remove_element(numbers, target)
print(result)
```

**How it works:** Create a new empty list. Keep an element only when it is not equal to the target. This avoids changing a list while iterating over it, which can cause elements to be skipped.

**Key concepts:** Filtering, `append()`, conditions, and avoiding modification during iteration.

---

## Q5. Merge Two Lists Alternately

**Problem:** Take one element from the first list, then one from the second list, repeating until both lists are processed.

**Input**
```python
list1 = [1, 3, 5]
list2 = [2, 4, 6]
```

**Expected output**
```python
[1, 2, 3, 4, 5, 6]
```

**Solution**
```python
def merge_lists(list1, list2):
    result = []

    for i in range(max(len(list1), len(list2))):
        if i < len(list1):
            result.append(list1[i])
        if i < len(list2):
            result.append(list2[i])

    return result


list1 = [1, 3, 5]
list2 = [2, 4, 6]
result = merge_lists(list1, list2)
print(result)
```

**How it works:** Use the same index to take an item from each list. The length checks also make the function work when the lists have different lengths; any remaining items are added in their original order.

**Key concepts:** Indexing, `range()`, `len()`, and building a result list. This is different from sorting: the elements are interleaved, not ordered by value.

---

## Q6. Count Uppercase, Lowercase, Digits, Spaces, and Special Characters

**Problem:** Count each character category in a string.

**Input**
```python
text = "Python 3.12 Is Fun!"
```

**Expected output**
```text
Uppercase: 3
Lowercase: 8
Digits: 3
Spaces: 3
Special characters: 2
```

**Solution**
```python
def count_characters(text):
    uppercase = 0
    lowercase = 0
    digits = 0
    spaces = 0
    special = 0

    for i in text:
        if i.isupper():
            uppercase += 1
        elif i.islower():
            lowercase += 1
        elif i.isdigit():
            digits += 1
        elif i.isspace():
            spaces += 1
        else:
            special += 1

    return uppercase, lowercase, digits, spaces, special


text = "Python 3.12 Is Fun!"
uppercase, lowercase, digits, spaces, special = count_characters(text)

print("Uppercase:", uppercase)
print("Lowercase:", lowercase)
print("Digits:", digits)
print("Spaces:", spaces)
print("Special characters:", special)
```

**How it works:** Each character is checked using string methods. If it does not match any of the first four categories, it is counted as a special character. In this exercise, punctuation such as `.` and `!` is special.

**Key concepts:** `isupper()`, `islower()`, `isdigit()`, `isspace()`, counters, and multiple return values.

---

## Q7. Reverse Each Word in a Sentence

**Problem:** Reverse the letters in each word while keeping the words in their original order.

**Input**
```python
text = "Python is easy"
```

**Expected output**
```text
nohtyP si ysae
```

**Solution**
```python
def reverse_words(text):
    words = text.split()
    result = []

    for i in words:
        reverse = ""

        for j in i:
            reverse = j + reverse

        result.append(reverse)

    return " ".join(result)


text = "Python is easy"
result = reverse_words(text)
print("Reversed words:", result)
```

**How it works:** `split()` separates the sentence into words. The inner loop builds each reversed word by adding each new character to the beginning. `join()` combines the reversed words with spaces.

**Key concepts:** Nested loops, strings, `split()`, `append()`, and `join()`.

---

## Q8. Check Whether Two Strings Are Rotations

**Problem:** Check whether the second string can be created by rotating the first string.

**Input**
```python
str1 = "abcd"
str2 = "cdab"
```

**Expected output**
```text
Strings are rotations
```

**Solution**
```python
def are_rotations(str1, str2):
    if len(str1) != len(str2):
        return False

    combined = str1 + str1
    return str2 in combined


str1 = "abcd"
str2 = "cdab"

if are_rotations(str1, str2):
    print("Strings are rotations")
else:
    print("Strings are not rotations")
```

**How it works:** First check that both strings have the same length. Then concatenate the first string with itself: `"abcdabcd"`. Every rotation of `"abcd"`, such as `"bcda"`, `"cdab"`, or `"dabc"`, appears inside this combined string.

**Key concepts:** String concatenation, `len()`, membership with `in`, and boolean functions.

---

## Q9. Find the Most Frequent Word in a Sentence

**Problem:** Find the word with the highest frequency in a sentence.

**Input**
```python
text = "python is easy and python is powerful"
```

**Expected output**
```text
python appears 2 times
```

**Solution**
```python
def most_frequent_word(text):
    words = text.split()
    frequency = {}

    for i in words:
        if i in frequency:
            frequency[i] += 1
        else:
            frequency[i] = 1

    max_count = 0
    max_word = ""

    for i in frequency:
        if frequency[i] > max_count:
            max_count = frequency[i]
            max_word = i

    return max_word, max_count


text = "python is easy and python is powerful"
word, count = most_frequent_word(text)
print(word, "appears", count, "times")
```

**How it works:** First build a dictionary in which each word is a key and its count is the value. Then find the key with the largest value. When multiple words share the maximum count, this implementation returns the one encountered first in the sentence.

**Key concepts:** `split()`, dictionaries, frequency counting, and finding a maximum value.

---

## Q10. Group Words Based on Their Length

**Problem:** Create a dictionary where each key is a word length and its value is a list of words having that length.

**Input**
```python
words = ["apple", "bat", "cat", "banana", "dog", "mango"]
```

**Expected output**
```python
{
    5: ["apple", "mango"],
    3: ["bat", "cat", "dog"],
    6: ["banana"]
}
```

**Reference solution**
```python
def group_words(words):
    groups = {}

    for word in words:
        word_length = len(word)

        if word_length not in groups:
            groups[word_length] = []

        groups[word_length].append(word)

    return groups


words = ["apple", "bat", "cat", "banana", "dog", "mango"]
result = group_words(words)
print(result)
```

**How it works:** Calculate each word's length. If that length is not already a dictionary key, create an empty list for it. Then append the word to the list for that length.

**Key concepts:** Dictionaries containing lists, `len()`, membership checks, and grouping data.

**Practice status:** Reference solution provided; independent attempt pending.

---

## Day 6 – Concepts Practised

- Counting values with counters and conditions.
- Comparing adjacent list elements using indexes.
- Tracking the largest, second-largest, and third-largest distinct values.
- Filtering a list without modifying it during iteration.
- Alternating elements from two lists.
- Classifying characters with string methods.
- Reversing each word using nested loops.
- Checking string rotations with concatenation and membership.
- Counting word frequencies with dictionaries.
- Grouping words by length with dictionaries and lists.
- Writing reusable functions and returning results.

**Progress:** 9 questions discussed and practised; Q10 reference solution included, independent attempt pending.
