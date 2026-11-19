# Day 5 – Python Functions

Today, I practised writing reusable Python functions and solving problems using parameters, arguments, `return`, loops, conditions, strings, and dictionaries.

## Topics covered

- Creating and calling functions
- Parameters and arguments
- Returning values using `return`
- Using conditions and loops inside functions
- Handling strings and lists
- Using dictionaries to count frequencies

---

## 1. Create a Function to Display a Welcome Message

**Problem:** Create a function that displays a welcome message.

```python
def greet():
    print("Welcome to Python Learning")
    print("Happy Coding!")

greet()
```

**Output:**
```text
Welcome to Python Learning
Happy Coding!
```

**Explanation:** `def` is used to define a function. The function runs when we call it using `greet()`.

## 2. Add Two Numbers Using a Function

**Problem:** Create a function that accepts two numbers and returns their sum.

```python
def add(a, b):
    return a + b

result = add(15, 25)
print(result)
```

**Output:**
```text
40
```

**Explanation:** `a` and `b` are parameters. The values `15` and `25` are arguments. `return` sends the result back to the place where the function was called.

## 3. Check Even or Odd Using a Function

**Problem:** Create a function that checks whether a number is even or odd.

```python
def check(number):
    if number % 2 == 0:
        return "Even"
    else:
        return "Odd"

number = int(input("Enter a number: "))
result = check(number)
print(result)
```

**Example output:**
```text
Enter a number: 7
Odd
```

**Explanation:** If a number gives remainder `0` when divided by `2`, it is even. Otherwise, it is odd.

## 4. Find the Largest of Three Numbers Using a Function

**Problem:** Create a function that accepts three numbers and returns the largest.

```python
def find_largest(a, b, c):
    if a >= b and a >= c:
        return a
    elif b >= a and b >= c:
        return b
    else:
        return c

numbers = []
for i in range(3):
    number = int(input(f"Enter number {i + 1}: "))
    numbers.append(number)

a, b, c = numbers
result = find_largest(a, b, c)
print("Largest number:", result)
```

**Example output:**
```text
Enter number 1: 10
Enter number 2: 25
Enter number 3: 15
Largest number: 25
```

**Explanation:** The loop collects three numbers and stores them in a list. Then `a, b, c = numbers` assigns each list element to a variable. The function compares the three values and returns the largest.

## 5. Find the Factorial of a Number Using a Function

**Problem:** Create a function that returns the factorial of a number.

```python
def factorial(n):
    if n < 0:
        return None
    elif n == 0 or n == 1:
        return 1
    else:
        fact = 1
        for i in range(2, n + 1):
            fact = fact * i
        return fact

n = int(input("Enter a number: "))
result = factorial(n)

if result is None:
    print("Factorial is not defined for negative numbers")
else:
    print(f"Factorial of {n} is {result}")
```

**Example output:**
```text
Enter a number: 5
Factorial of 5 is 120
```

**Explanation:** Factorial means multiplying all positive integers from `1` to `n`. For example, `5! = 5 × 4 × 3 × 2 × 1 = 120`. The factorial of `0` and `1` is `1`. Negative integers do not have a factorial in this context, so the function returns `None`.

## 6. Check Whether a Number Is Prime Using a Function

**Problem:** Create a function that checks whether a number is prime.

```python
def check_prime(n):
    if n < 2:
        return False

    for i in range(2, n):
        if n % i == 0:
            return False

    return True

n = int(input("Enter a number: "))
result = check_prime(n)

if result:
    print(f"{n} is a prime number")
else:
    print(f"{n} is not a prime number")
```

**Example output:**
```text
Enter a number: 7
7 is a prime number
```

**Explanation:** A prime number is greater than `1` and has exactly two factors: `1` and itself. The loop checks whether any number from `2` to `n - 1` divides `n` exactly. If one does, the number is not prime.

## 7. Check Whether a String Is a Palindrome Using a Function

**Problem:** Create a function that checks whether a string reads the same forward and backward. This version ignores uppercase and lowercase differences.

```python
def palindrome(text):
    text = text.lower()
    reverse = ""

    for i in text:
        reverse = i + reverse

    if text == reverse:
        return True
    return False

text = input("Enter a string: ")
result = palindrome(text)

if result:
    print("Palindrome")
else:
    print("Not a palindrome")
```

**Example output:**
```text
Enter a string: Madam
Palindrome
```

**Explanation:** `reverse = i + reverse` adds each character to the beginning of the new string. At the end, the original text and reversed text are compared. `lower()` makes the comparison case-insensitive.

## 8. Count Vowels in a String Using a Function

**Problem:** Create a function that counts the vowels in a string.

```python
def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0

    for i in text:
        if i in vowels:
            count += 1

    return count

text = input("Enter a string: ")
result = count_vowels(text)
print(f"Count of vowels in {text} is {result}")
```

**Example output:**
```text
Enter a string: programming
Count of vowels in programming is 3
```

**Explanation:** The loop checks each character. When a character is present in the `vowels` string, the count increases by one. The `return` statement is outside the loop so the function returns the final count after checking every character.

## 9. Find the Second Largest Distinct Element Using a Function

**Problem:** Create a function that returns the second-largest distinct number in a list.

```python
def find_second_largest(numbers):
    largest = float('-inf')
    sec_max = float('-inf')

    for i in numbers:
        if i > largest:
            sec_max = largest
            largest = i
        elif i > sec_max and i != largest:
            sec_max = i

    if sec_max == float('-inf'):
        return None

    return sec_max

numbers = [10, 20, 40, 30, 50]
result = find_second_largest(numbers)

if result is None:
    print("A second-largest distinct element does not exist")
else:
    print("Second largest number:", result)
```

**Output:**
```text
Second largest number: 40
```

**Explanation:**

- `largest` stores the largest number found so far.
- `sec_max` stores the second-largest distinct number found so far.
- When a new largest number appears, the previous largest becomes the second largest.
- Otherwise, if the current number is greater than `sec_max` and is not equal to `largest`, it becomes the new second largest.
- `float('-inf')` starts both variables at negative infinity, so the logic also works when all list values are negative.
- If there is no second distinct value, the function returns `None`.

## 10. Find the Frequency of Each Element Using a Function

**Problem:** Create a function that counts how many times each number appears in a list.

```python
def frequency_count(numbers):
    frequency = {}

    for i in numbers:
        if i in frequency:
            frequency[i] += 1
        else:
            frequency[i] = 1

    return frequency

numbers = [1, 2, 2, 3, 3, 3, 4]
result = frequency_count(numbers)
print("Frequency count:", result)
```

**Output:**
```text
Frequency count: {1: 1, 2: 2, 3: 3, 4: 1}
```

**Explanation:** The dictionary stores each number as a key and its frequency as the value.

- `frequency[i] = 1` sets the count to `1` when the number appears for the first time.
- `frequency[i] += 1` is the same as `frequency[i] = frequency[i] + 1`. It increases the existing value for that key by one.
- The key remains the same; its value is updated.

---

## Important Concepts I Learned

### 1. `print()` vs `return`

- `print()` displays something on the screen.
- `return` sends a value back from a function so it can be stored or used elsewhere.

### 2. Parameters vs Arguments

- Parameters are the variable names written inside the function definition.
- Arguments are the actual values passed when calling the function.

### 3. Function Indentation

Indentation decides which statements belong to a function, loop, or condition. For example, a `return` placed inside a loop may stop the function too early. Place it outside the loop when the full loop must finish first.

### 4. Dictionary Frequency Pattern

```python
if item in frequency:
    frequency[item] += 1
else:
    frequency[item] = 1
```

This pattern counts repeated elements efficiently using a dictionary.

---

## Day 5 Summary

Today I completed 10 practice problems using Python functions. I practised how to define and call functions, pass arguments, return results, use loops and conditions inside functions, process strings and lists, and count elements using dictionaries.

**Practice completed: 10 problems**
