# 🐍 Python Logic Building -- Day 01

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Day](https://img.shields.io/badge/Day-01-success)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## About This Practice

Day 1 of my Python Logic Building journey focuses on strengthening
programming fundamentals and developing independent problem-solving
skills.

For each problem, I follow this process:

1.  Understand the problem.
2.  Identify the input and expected output.
3.  Develop the logic step by step.
4.  Write the Python code.
5.  Perform a dry run.
6.  Test with different inputs.
7.  Review mistakes and improve the solution.

------------------------------------------------------------------------

# Day 1 -- 10 Coding Problems

## 1. Check Whether a Number Is Even or Odd

**Problem:** Check whether a given number is even or odd.

### Code

``` python
n = int(input("Enter a number: "))

if n % 2 == 0:
    print("Even number")
else:
    print("Odd number")
```

### Logic

-   Accept an integer from the user.
-   Use the modulus operator `%` to find the remainder after division by
    2.
-   If the remainder is `0`, the number is even.
-   Otherwise, the number is odd.

**Example:** `7 % 2 = 1`, so 7 is odd. `8 % 2 = 0`, so 8 is even.

### Important concepts

  Concept     Explanation
  ----------- ----------------------------------------
  `input()`   Accepts user input as a string
  `int()`     Converts a value into an integer
  `%`         Returns the remainder
  `if-else`   Chooses which block of code to execute

**Remember** - `n % 2 == 0` identifies an even number. - `n % 2 != 0`
identifies an odd number. - Zero is even.

------------------------------------------------------------------------

## 2. Find the Largest of Three Numbers

**Problem:** Find the largest among three numbers.

### Code

``` python
a, b, c = map(int, input("Enter three numbers: ").split())

if a > b and a > c:
    print(a, "is largest")
elif b > c:
    print(b, "is largest")
else:
    print(c, "is largest")
```

### Logic

1.  Read three space-separated numbers.
2.  Check whether `a` is greater than both `b` and `c`.
3.  If not, compare `b` with `c`.
4.  Otherwise, `c` is the largest.

**Example:** Input `25 70 45` produces `70 is largest`.

### Understanding `map()` and `split()`

``` python
a, b, c = map(int, input().split())
```

-   `input()` reads the entered text.
-   `split()` separates values at whitespace.
-   `map(int, ...)` converts each separated value to an integer.
-   The three converted values are unpacked into `a`, `b`, and `c`.

### Important concepts

  Concept     Explanation
  ----------- --------------------------------------------------------
  `split()`   Separates input into parts
  `map()`     Applies a conversion function to each part
  `and`       Requires both conditions to be true
  `elif`      Checks another condition if the previous one was false

**Remember** - Use `and` when both comparisons must be true. - `elif`
lets you check another condition. - This simplified comparison assumes
you only need to print one largest value; it also handles ties by
printing one of the tied maximum values.

------------------------------------------------------------------------

## 3. Find the Sum of Digits

**Problem:** Calculate the sum of all digits in a number.

### Code

``` python
n = int(input("Enter a number: "))
total = 0

while n > 0:
    digit = n % 10
    total += digit
    n = n // 10

print("Sum of digits:", total)
```

### Logic

For the number `1234`, extract the last digit, add it to `total`, and
remove that digit. Repeat until the number becomes zero.

### Dry run

  -----------------------------------------------------------------------
  Iteration       `n` before       `n % 10`  `total` after      `n // 10`
                                                  addition 
  ----------- -------------- -------------- -------------- --------------
  1                     1234              4              4            123

  2                      123              3              7             12

  3                       12              2              9              1

  4                        1              1             10              0
  -----------------------------------------------------------------------

**Output:** `Sum of digits: 10`

### Important concepts

-   `n % 10` extracts the last digit.
-   `n // 10` removes the last digit.
-   `total += digit` adds the extracted digit to the running total.
-   `while` repeats as long as its condition is true.

**Remember** - `% 10` extracts a digit from the right. - `// 10` removes
the rightmost digit. - Initialize an accumulator such as `total` to
`0`. - This version assumes a non-negative input. For negative numbers,
use `abs(n)` first.

------------------------------------------------------------------------

## 4. Reverse a Number

**Problem:** Reverse the digits of a given number.

### Code

``` python
n = int(input("Enter a number: "))
reverse = 0

while n > 0:
    digit = n % 10
    reverse = reverse * 10 + digit
    n = n // 10

print("Reversed number:", reverse)
```

### Logic

For `1234`, extract digits from right to left and build a new number.

### Dry run

  Iteration     Extracted digit   Previous `reverse`   New `reverse`
  ----------- ----------------- -------------------- ---------------
  1                           4                    0               4
  2                           3                    4              43
  3                           2                   43             432
  4                           1                  432            4321

**Output:** `Reversed number: 4321`

### Most important formula

``` python
reverse = reverse * 10 + digit
```

For example, if `reverse = 43` and `digit = 2`:

-   `43 * 10 = 430`
-   `430 + 2 = 432`

Multiplying by 10 shifts the existing number one decimal place to the
left. Adding the new digit places it at the end.

**Remember** - `% 10` extracts the last digit. - `// 10` removes the
last digit. - `reverse * 10 + digit` builds the reversed number. -
Initialize `reverse = 0`. - This version assumes a non-negative input.

------------------------------------------------------------------------

## 5. Find the Smallest Number in a List

**Problem:** Find the minimum value in a list.

### Code

``` python
numbers = [45, 12, 89, 5, 34]

smallest = numbers[0]

for i in numbers:
    if i < smallest:
        smallest = i

print("Smallest number:", smallest)
```

### Logic

1.  Assume the first element is the smallest.
2.  Visit each element in the list.
3.  If the current element is smaller than `smallest`, update
    `smallest`.
4.  Print the result after checking every element.

### Dry run

    Current element   Previous smallest Comparison           Updated smallest
  ----------------- ------------------- ------------------ ------------------
                 45                  45 45 \< 45 → False                   45
                 12                  45 12 \< 45 → True                    12
                 89                  12 89 \< 12 → False                   12
                  5                  12 5 \< 12 → True                      5
                 34                   5 34 \< 5 → False                     5

**Output:** `Smallest number: 5`

### Important concepts

-   `numbers[0]` accesses the first element.
-   A `for` loop visits each element.
-   `<` checks whether one value is smaller than another.
-   Updating `smallest` keeps track of the best value found so far.

**Remember** - Initialize with the first element when the list is
non-empty. - Use `<` to find the minimum. - Update the variable whenever
a smaller value appears.

------------------------------------------------------------------------

## 6. Find the Largest Number in a List

**Problem:** Find the maximum value in a list.

### Code

``` python
numbers = [45, 12, 89, 5, 34]

largest = numbers[0]

for i in numbers:
    if i > largest:
        largest = i

print("Largest number:", largest)
```

### Logic

1.  Assume the first element is the largest.
2.  Visit every element.
3.  If the current element is greater than `largest`, update it.
4.  Print the largest value after the loop.

### Dry run

    Current element   Previous largest Comparison           Updated largest
  ----------------- ------------------ ------------------ -----------------
                 45                 45 45 \> 45 → False                  45
                 12                 45 12 \> 45 → False                  45
                 89                 45 89 \> 45 → True                   89
                  5                 89 5 \> 89 → False                   89
                 34                 89 34 \> 89 → False                  89

**Output:** `Largest number: 89`

**Remember** - Initialize with the first element when the list is
non-empty. - Use `>` to find the maximum. - Update the variable only
when a bigger value appears.

------------------------------------------------------------------------

## 7. Count Even and Odd Numbers in a List

**Problem:** Count how many even and odd numbers are present in a list.

### Code

``` python
numbers = [12, 7, 9, 20, 15, 8, 11, 4]

even_count = 0
odd_count = 0

for i in numbers:
    if i % 2 == 0:
        even_count += 1
    else:
        odd_count += 1

print("Even count:", even_count)
print("Odd count:", odd_count)
```

### Logic

-   Start two counters at zero.
-   Visit each number.
-   If `i % 2 == 0`, increase `even_count`.
-   Otherwise, increase `odd_count`.

### Dry run

    Number Type     Even count   Odd count
  -------- ------ ------------ -----------
        12 Even              1           0
         7 Odd               1           1
         9 Odd               1           2
        20 Even              2           2
        15 Odd               2           3
         8 Even              3           3
        11 Odd               3           4
         4 Even              4           4

**Output:**

``` text
Even count: 4
Odd count: 4
```

### Counter variable

A counter tracks how many times an event occurs.

``` python
count += 1
```

This is equivalent to:

``` python
count = count + 1
```

**Remember** - Initialize counters with `0`. - Use `% 2 == 0` to
identify even numbers. - Use `else` for odd numbers. - Increase the
appropriate counter by one.

------------------------------------------------------------------------

## 8. Find the Second Largest Distinct Number in a List

**Problem:** Find the second-largest distinct value without sorting the
list.

### Code

``` python
numbers = [45, 12, 89, 5, 34, 67]

largest = float('-inf')
second_largest = float('-inf')

for i in numbers:
    if i > largest:
        second_largest = largest
        largest = i

    elif i > second_largest and i != largest:
        second_largest = i

print("Second largest:", second_largest)
```

### Logic

We maintain two variables:

-   `largest` stores the largest value found so far.
-   `second_largest` stores the second-largest distinct value found so
    far.

**Case 1: A new largest value appears**

``` python
if i > largest:
    second_largest = largest
    largest = i
```

The previous largest value moves into second place.

**Case 2: The current value is between the largest and second largest**

``` python
elif i > second_largest and i != largest:
    second_largest = i
```

Update only the second-largest value.

### Dry run

Input: `[45, 12, 89, 5, 34, 67]`

    Current number   Largest   Second largest
  ---------------- --------- ----------------
                45        45               -∞
                12        45               12
                89        89               45
                 5        89               45
                34        89               45
                67        89               67

**Output:** `Second largest: 67`

### Understanding `float('-inf')`

Negative infinity is smaller than every ordinary numeric value. It is a
useful starting value when searching for a maximum, including when all
list values are negative.

**Remember** - Maintain two variables. - When a new largest appears,
move the old largest into second place. - Otherwise, check whether the
current number can become second largest. - `i != largest` prevents the
largest value from being counted twice. - This solution finds the
second-largest **distinct** value. It requires at least two distinct
values.

------------------------------------------------------------------------

## 9. Find the Second Smallest Distinct Number in a List

**Problem:** Find the second-smallest distinct value without sorting the
list.

### Code

``` python
numbers = [45, 12, 89, 5, 34, 67]

smallest = float('inf')
second_smallest = float('inf')

for i in numbers:
    if i < smallest:
        second_smallest = smallest
        smallest = i

    elif i < second_smallest and i != smallest:
        second_smallest = i

print("Second smallest:", second_smallest)
```

### Logic

We maintain two variables:

-   `smallest` stores the smallest value found so far.
-   `second_smallest` stores the second-smallest distinct value found so
    far.

**Case 1: A new smallest value appears**

``` python
if i < smallest:
    second_smallest = smallest
    smallest = i
```

The previous smallest value moves into second place.

**Case 2: The current value is between the smallest and second
smallest**

``` python
elif i < second_smallest and i != smallest:
    second_smallest = i
```

Update only the second-smallest value.

### Dry run

Input: `[45, 12, 89, 5, 34, 67]`

    Current number   Smallest   Second smallest
  ---------------- ---------- -----------------
                45         45                 ∞
                12         12                45
                89         12                45
                 5          5                12
                34          5                12
                67          5                12

**Output:** `Second smallest: 12`

### Understanding `float('inf')`

Positive infinity is greater than every ordinary numeric value. It is
useful as an initial value when searching for a minimum.

**Remember** - Use `float('inf')` for minimum-value initialization. -
Use `<` to find smaller values. - When a new smallest appears, move the
previous smallest into second place. - `i != smallest` ensures that the
second value is distinct. - This solution requires at least two distinct
values.

------------------------------------------------------------------------

## 10. Remove Duplicates from a List

**Problem:** Remove repeated elements while preserving the original
order.

### Code

``` python
numbers = [10, 20, 10, 30, 40, 20, 50]

unique_numbers = []

for i in numbers:
    if i not in unique_numbers:
        unique_numbers.append(i)

print("List without duplicates:", unique_numbers)
```

### Logic

1.  Create an empty list called `unique_numbers`.
2.  Visit each element in the original list.
3.  Check whether the current element is already in `unique_numbers`.
4.  If it is not present, add it using `append()`.
5.  If it is already present, skip it.

### Dry run

    Current element Already present?   Action   Updated unique list
  ----------------- ------------------ -------- ------------------------
                 10 No                 Add      `[10]`
                 20 No                 Add      `[10, 20]`
                 10 Yes                Skip     `[10, 20]`
                 30 No                 Add      `[10, 20, 30]`
                 40 No                 Add      `[10, 20, 30, 40]`
                 20 Yes                Skip     `[10, 20, 30, 40]`
                 50 No                 Add      `[10, 20, 30, 40, 50]`

**Output:**

``` python
[10, 20, 30, 40, 50]
```

### Important concepts

**`not in`** checks whether an element does not exist in a collection.

``` python
if i not in unique_numbers:
```

**`append()`** adds an element to the end of a list.

``` python
unique_numbers.append(i)
```

**Remember** - Create a new empty list. - Use `not in` to check for
duplicates. - Use `append()` to add unique elements. - This approach
preserves the original order.

------------------------------------------------------------------------

# Important Python Concepts -- Day 1 Revision

## 1. Operators

  Operator   Meaning               Example      Result
  ---------- --------------------- ------------ --------
  `%`        Modulus (remainder)   `15 % 10`    `5`
  `//`       Floor division        `15 // 10`   `1`
  `/`        True division         `15 / 10`    `1.5`
  `*`        Multiplication        `5 * 10`     `50`
  `==`       Equal to              `5 == 5`     `True`
  `>`        Greater than          `8 > 5`      `True`
  `<`        Less than             `3 < 5`      `True`

## 2. Loops and Built-in Functions

  Concept     Purpose
  ----------- -----------------------------------
  `for`       Iterates over a sequence or range
  `while`     Repeats while a condition is true
  `range()`   Generates a sequence of integers
  `len()`     Returns the number of items
  `input()`   Reads user input
  `int()`     Converts a value to an integer
  `map()`     Applies a function to each item
  `split()`   Splits a string into parts

## 3. List Operations

  Operation        Purpose
  ---------------- ------------------------------------------
  `numbers[0]`     Accesses the first element
  `append()`       Adds an element to the end
  `in`             Checks whether an element exists
  `not in`         Checks whether an element does not exist
  `len(numbers)`   Returns the number of elements

## 4. Useful Initialization Patterns

  Problem           Initialization
  ----------------- ----------------------------------
  Largest number    `largest = float('-inf')`
  Second largest    `second_largest = float('-inf')`
  Smallest number   `smallest = float('inf')`
  Second smallest   `second_smallest = float('inf')`
  Sum accumulator   `total = 0`
  Counter           `count = 0`
  Reversed number   `reverse = 0`

------------------------------------------------------------------------

# Logic-Building Patterns to Remember

### Pattern 1: Extract the Last Digit

``` python
digit = n % 10
```

### Pattern 2: Remove the Last Digit

``` python
n = n // 10
```

### Pattern 3: Reverse a Number

``` python
reverse = reverse * 10 + digit
```

### Pattern 4: Find the Maximum

``` python
if i > largest:
    largest = i
```

### Pattern 5: Find the Minimum

``` python
if i < smallest:
    smallest = i
```

### Pattern 6: Count Elements

``` python
count = 0

for i in numbers:
    if condition:
        count += 1
```

### Pattern 7: Remove Duplicates

``` python
if i not in unique_numbers:
    unique_numbers.append(i)
```

### Pattern 8: Update the Second Largest

``` python
if i > largest:
    second_largest = largest
    largest = i
```

### Pattern 9: Update the Second Smallest

``` python
if i < smallest:
    second_smallest = smallest
    smallest = i
```

------------------------------------------------------------------------

# Additional Practice

After completing the 10 core problems, I also practised these
extensions:

  -----------------------------------------------------------------------
  No.                     Problem                 Concepts
  ----------------------- ----------------------- -----------------------
  1                       Find the Third Largest  Multiple variables,
                          Number                  conditional logic

  2                       Count the Frequency of  Nested loops, counters,
                          Each Element            list indexing
  -----------------------------------------------------------------------

These problems extend the same fundamentals and help build confidence
with list-based logic.

------------------------------------------------------------------------

# Day 1 -- Learning Outcomes

By completing these exercises, I practised:

-   Number manipulation.
-   Conditional statements.
-   `for` and `while` loops.
-   List creation and traversal.
-   Finding minimum and maximum values.
-   Maintaining multiple variables.
-   Counter-based problems.
-   Removing duplicate elements.
-   Understanding algorithms through dry runs.
-   Developing problem-solving logic independently.

## My Learning Goal

I want to become confident in developing programming logic independently
instead of memorizing solutions.

**Day 01 -- Status: Completed ✅**

**Next: Day 02 -- Intermediate Python Logic Building**
