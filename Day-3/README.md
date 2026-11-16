# Day 3 – Python Logic Building Practice

Welcome to Day 3 of my Python Logic Building Practice!

Today's practice focuses on **strings, loops, conditions, lists, and problem-solving techniques**. The goal is to understand each problem, build the logic step by step, and practise writing Python code independently.

## Topics Covered

- String iteration and indexing
- Reversing strings and palindrome checking
- Counting vowels, consonants, and character frequency
- Finding non-repeating and most frequent characters
- Removing duplicate characters
- Splitting sentences and finding the longest word
- Combining and sorting lists
- String rotation and slicing
- Maximum-frequency tracking and handling ties

---

## 1. Reverse a String

**Problem:** Reverse a string without using slicing (`[::-1]`).

**Input:**
```python
text = "python"
```

**Code:**
```python
text = "python"
reverse = ""

for i in text:
    reverse = i + reverse

print(reverse)
```

**Output:**
```text
nohtyp
```

**Understanding:**
- `reverse` starts as an empty string.
- The `for` loop reads one character at a time.
- `i + reverse` adds the current character to the beginning of the result.
- `reverse + i` would add the character to the end.

---

## 2. Check Whether a String Is a Palindrome

**Problem:** Check whether a word reads the same forward and backward.

**Input:**
```python
text = "madam"
```

**Code:**
```python
text = "madam"
reverse = ""

for char in text:
    reverse = char + reverse

if text == reverse:
    print("Palindrome")
else:
    print("Not a palindrome")
```

**Output:**
```text
Palindrome
```

**Understanding:**
- Reverse the word using a `for` loop.
- Compare the original word with the reversed word.
- If both are equal, the word is a palindrome.
- Otherwise, it is not a palindrome.

More examples: `"level"` and `"radar"` are palindromes; `"hello"` is not.

This example checks exact characters. Uppercase and lowercase letters are treated as different characters.

---

## 3. Count Vowels and Consonants

**Problem:** Count vowels and consonants. Handle uppercase and lowercase letters, and do not count spaces, digits, or punctuation.

**Input:**
```python
text = "PrOGrAmMing"
```

**Code:**
```python
text = "PrOGrAmMing"

vowels = 0
consonants = 0

for i in text:
    if i.lower() in "aeiou":
        vowels += 1
    elif i.isalpha():
        consonants += 1

print("Vowels:", vowels)
print("Consonants:", consonants)
```

**Output:**
```text
Vowels: 3
Consonants: 8
```

**Understanding:**
- `i.lower()` converts the current character to lowercase for checking.
- `i.lower() in "aeiou"` checks whether it is a vowel.
- `i.isalpha()` checks whether it is an alphabet letter.
- The `elif` prevents spaces, numbers, and special characters from being counted as consonants.

Useful methods:
- `.lower()` converts text to lowercase.
- `.upper()` converts text to uppercase.
- `.isalpha()` checks whether a character is an alphabet letter.

---

## 4. Character Frequency

**Problem:** Count how many times each unique character appears in a string.

**Input:**
```python
text = "banana"
```

**Code:**
```python
text = "banana"

unique = []

for i in text:
    if i not in unique:
        unique.append(i)

for i in unique:
    count = 0

    for j in text:
        if i == j:
            count += 1

    print(i, "appears", count, "times")
```

**Output:**
```text
b appears 1 times
a appears 3 times
n appears 2 times
```

**Understanding:**
- `unique` stores each character only once.
- The outer loop selects one unique character.
- `count = 0` is inside the outer loop so the count resets for each character.
- The inner loop checks the entire original string.
- When the characters match, `count` increases by 1.

**Note:** Converting a string into a list with `list(text)` is optional. A `for` loop can iterate directly over a string.

---

## 5. Find the First Non-Repeating Character

**Problem:** Find the first character that appears exactly once in a string.

**Input:**
```python
text = "swiss"
```

**Code:**
```python
text = "swiss"

unique = []

for i in text:
    if i not in unique:
        unique.append(i)

for i in unique:
    count = 0

    for j in text:
        if i == j:
            count += 1

    if count == 1:
        print("First non-repeating character:", i)
        break
```

**Output:**
```text
First non-repeating character: w
```

**Understanding:**
- First, create a list of unique characters in their original order.
- The outer loop selects each unique character.
- The inner loop counts how many times that character appears in the original string.
- If `count == 1`, that character is the first non-repeating character.
- `break` stops the outer loop after finding the first answer.

For `"swiss"`, `s` appears 3 times, while `w` appears once. The program prints `w` and stops.

**Important:** Complete the inner loop before checking `count == 1`. Otherwise, the count may still be incomplete.

---

## 6. Remove Duplicate Characters

**Problem:** Remove repeated characters while keeping the first occurrence and preserving the original order.

**Input:**
```python
text = "programming"
```

**Code using a list:**
```python
text = "programming"

unique = []

for i in text:
    if i not in unique:
        unique.append(i)

result = "".join(unique)

print("Unique characters are:", result)
```

**Output:**
```text
Unique characters are: progamin
```

**Alternative using a string:**
```python
text = "programming"
result = ""

for i in text:
    if i not in result:
        result = result + i

print("Unique characters are:", result)
```

**Understanding:**
- Check whether the current character is already in the result.
- Add it only when it is not present.
- `"".join(unique)` combines the list characters into one string.
- The empty string `""` means no separator is added between characters.

**Remember:** `append()` adds an item to a list, while `join()` combines string elements into a string.

---

## 7. Find the Longest Word in a Sentence

**Problem:** Find the longest word in a sentence. When multiple words share the maximum length, return the first one.

**Input:**
```python
sentence = "Python programming is interesting"
```

**Code:**
```python
sentence = "Python programming is interesting"

words = sentence.split()
longest_word = ""

for i in words:
    if len(i) > len(longest_word):
        longest_word = i

print("Longest word is:", longest_word)
```

**Output:**
```text
Longest word is: programming
```

**Understanding:**
- `.split()` converts the sentence into a list of words.
- The `for` loop checks each word.
- `len(i)` gives the length of the current word.
- `len(longest_word)` gives the length of the longest word found so far.
- If the current word is longer, update `longest_word`.

In this example, both `"programming"` and `"interesting"` have 11 characters. The condition uses `>` rather than `>=`, so the first longest word is kept.

**Remember:**
- `len(words)` gives the number of words in the list.
- `len(i)` gives the number of characters in the current word.

---

## 8. Merge Two Sorted Lists

**Problem:** Combine two sorted lists into one sorted list.

**Input:**
```python
A = [1, 3, 5, 7]
B = [2, 4, 6, 8]
```

**Code:**
```python
A = [1, 3, 5, 7]
B = [2, 4, 6, 8]

c = A + B
c.sort()

print(c)
```

**Output:**
```text
[1, 2, 3, 4, 5, 6, 7, 8]
```

**Understanding:**
- `A + B` combines the two lists.
- `.sort()` arranges the combined list in ascending order.
- `.sort()` changes the list itself.

**Useful distinction:**
- `c.sort()` sorts the list in place.
- `sorted(c)` returns a new sorted list and leaves `c` unchanged.

---

## 9. Rotate a String by K Positions

**Problem:** Rotate a string to the right by `k` positions.

**Input:**
```python
text = "python"
k = 2
```

**Code using a list:**
```python
text = "python"
k = 2

characters = list(text)

for i in range(k):
    char = characters.pop()
    characters.insert(0, char)

result = "".join(characters)

print(result)
```

**Output:**
```text
onpyth
```

**Understanding:**
- `list(text)` converts the string into a list of characters.
- `pop()` removes and returns the last character.
- `insert(0, char)` places that character at the beginning.
- The loop repeats this operation `k` times.
- `"".join(characters)` converts the list back into a string.

**Slicing alternative:**
```python
text = "python"
k = 2

result = text[-k:] + text[:-k]

print(result)
```

Output:
```text
onpyth
```

**Understanding slicing:**
- `text[-k:]` takes the last `k` characters.
- `text[:-k]` takes everything before those last `k` characters.
- Joining them gives a right rotation.

For a non-empty string, `k = k % len(text)` can be used first when `k` may be larger than the string length. Handle an empty string before using modulo.

---

## 10. Find the Most Frequent Character

**Problem:** Find the character that appears the highest number of times. If multiple characters have the same highest frequency, return the first one encountered in the original string.

**Input:**
```python
text = "mississippi"
```

**Code:**
```python
text = "mississippi"

unique = []

for i in text:
    if i not in unique:
        unique.append(i)

max_count = 0
max_char = ""

for i in unique:
    count = 0

    for j in text:
        if i == j:
            count += 1

    if count > max_count:
        max_count = count
        max_char = i

print("Most frequent character is:", max_char)
print("Frequency:", max_count)
```

**Output:**
```text
Most frequent character is: i
Frequency: 4
```

**Understanding:**
- `unique` stores each character once, in the order it first appears.
- `count` temporarily counts the current character.
- `max_count` stores the highest frequency found so far.
- `max_char` stores the character with that highest frequency.
- If the current `count` is greater than `max_count`, update both maximum variables.
- The print statements are outside the loop so the final answer is printed only once.

### What happens when there is a tie?

In `"mississippi"`:
- `i` appears 4 times.
- `s` appears 4 times.

The condition uses `>`:
```python
if count > max_count:
```

When `s` is checked, `count` is 4 and `max_count` is already 4. Since `4 > 4` is false, the program keeps `i`, the first character with the maximum frequency.

### To find all characters tied for the highest frequency

```python
text = "mississippi"

unique = []

for i in text:
    if i not in unique:
        unique.append(i)

max_count = 0
max_chars = []

for i in unique:
    count = 0

    for j in text:
        if i == j:
            count += 1

    if count > max_count:
        max_count = count
        max_chars = [i]
    elif count == max_count:
        max_chars.append(i)

print("Most frequent characters:", max_chars)
print("Frequency:", max_count)
```

**Output:**
```text
Most frequent characters: ['i', 's']
Frequency: 4
```

**Remember:**
- `>` keeps the first character when there is a tie.
- `>=` replaces the previous character and keeps the last tied character.
- `elif count == max_count` can collect every character tied for the maximum.

---

## Important Python Concepts Practised

| Concept | Purpose |
|---|---|
| `for` loop | Iterates through characters, words, and lists |
| `if` / `else` / `elif` | Checks conditions and makes decisions |
| `+` with strings | Joins strings together |
| `list()` | Converts an iterable such as a string into a list |
| `append()` | Adds an element to the end of a list |
| `pop()` | Removes and returns an element |
| `insert()` | Inserts an element at a specified index |
| `join()` | Combines string elements into one string |
| `split()` | Splits a sentence into words |
| `len()` | Returns the length of a string or list |
| `sort()` | Sorts a list in place |
| `lower()` | Converts a string to lowercase |
| `isalpha()` | Checks whether a character is an alphabet letter |
| `break` | Stops the loop in which it is used |
| `>` and `>=` | Compare values; their difference matters when handling ties |

## Day 3 Key Learnings

1. A string can be iterated over directly; converting it to a list is optional.
2. `char + result` adds a character to the beginning, while `result + char` adds it to the end.
3. A palindrome can be checked by comparing the original string with its reversed version.
4. Reset a frequency counter inside the outer loop when counting different characters separately.
5. Count all occurrences before checking whether a character is non-repeating.
6. Use `break` after finding the first character that meets a condition.
7. Use `split()` to separate a sentence into words.
8. Compare `len(current_word)` with `len(longest_word)` to track the longest word.
9. Use `pop()` and `insert()` to rotate a list of characters.
10. Use a maximum tracker to find the most frequent character, and decide how ties should be handled.

---

**Day 3 completed – Python coding logic practice.**

*I will continue practising, reviewing my solutions, and adding new learning notes as I progress.*
