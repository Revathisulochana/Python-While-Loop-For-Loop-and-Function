# Python Assignment 3 – While Loop, For Loop, and Function

This assignment covers **`while` loops with control statements** (`continue`, `break`, `while...else`), **`for` loops with `range()`**, and **functions**, through three mini-projects: a number guessing game, a multiplication table generator, and a BMI calculator.

---

## Table of Contents

1. [Task 1: While Loop & Control Statements — Number Guessing Game](#task-1-while-loop--control-statements--number-guessing-game)
2. [Task 2: For Loop — Multiplication Table Generator](#task-2-for-loop--multiplication-table-generator)
3. [Task 3: Function — BMI Calculator](#task-3-function--bmi-calculator)

---

## Task 1: While Loop & Control Statements — Number Guessing Game

### 1. Set Up the Game

Generate a random number between 1 and 10 that the user has to guess.

```python
import random
secret_number = random.randint(1, 10)
print(secret_number)
```
**Output**
```
7
```

### 2. Prompt the User

```python
attempts = 3
print(attempts)
```
**Output**
```
3
```

### 3. Implement the Guessing Logic

First pass — loop until a valid guess is entered:

```python
while attempts > 0:
    guess = int(input("Guess the number (between 1 and 10): "))

    if guess < 1 or guess > 10:
        print("Your guess is out of range. Please guess a number between 1 and 10.")
        continue

    break
```
**Output**
```
Guess the number (between 1 and 10): 11
Your guess is out of range. Please guess a number between 1 and 10.
Guess the number (between 1 and 10): 6
```

### Full Feedback Logic (out of range / too high / too low / correct)

```python
attempts = 3
while attempts > 0:
    guess = int(input("Guess the number (between 1 and 10): "))

    if guess < 1 or guess > 10:
        print("Your guess is out of range. Please guess a number between 1 and 10.")
        continue

    attempts = attempts - 1

    if guess == secret_number:
        print("Congratulations! You guessed the correct number.")
        break
    elif guess > secret_number:
        print("Too high. Try again.")
    else:
        print("Too low. Try again.")
```

> **Note:** the original notebook cell had inconsistent indentation (the `if`/`attempts = attempts - 1` lines sat outside the `while` block, and `break` was indented one level too deep), which would raise an `IndentationError` if run as-is. The version above is the corrected, working form that matches the printed output.

**Output**
```
Guess the number (between 1 and 10): 9
Too high. Try again.
Guess the number (between 1 and 10): 4
Too low. Try again.
Guess the number (between 1 and 10): 7
Congratulations! You guessed the correct number.
```

### 4. Control Statements — `continue`, `break`, and `while`/`for`...`else`

Final version using a `for` loop with an `else` clause, so "Better luck next time!" prints only if the loop finishes without a correct guess:

```python
secret_number = 7
attempts = 5

for attempt in range(attempts):

    guess = int(input("Enter your guess (1-10): "))

    # Use continue if the guess is out of range
    if guess < 1 or guess > 10:
        print("Your guess is out of range! Please enter a number between 1 and 10.")
        continue

    # Use break if the guess is correct
    if guess == secret_number:
        print("Congratulations! You guessed the correct number.")
        break

    print("Wrong guess! Try again.")

else:
    print("Better luck next time!")
```

**Output**
```
Enter your guess (1-10): 2
Wrong guess! Try again.
Enter your guess (1-10): 15
Your guess is out of range! Please enter a number between 1 and 10.
Enter your guess (1-10): 5
Wrong guess! Try again.
Enter your guess (1-10): 3
Wrong guess! Try again.
Enter your guess (1-10): 7
Congratulations! You guessed the correct number.
```

**Key idea:** the `else` block on a `for` (or `while`) loop only runs if the loop completes normally — i.e., it is **not** reached if the loop exits via `break`. That's why "Better luck next time!" never prints here: the loop ends with `break` once the guess is correct.

---

## Task 2: For Loop — Multiplication Table Generator

**Problem Statement:** generate and print a multiplication table (1 to 10) for a user-given number, using a `for` loop and `range()`.

### 1. Prompt for Input

```python
number = int(input("Enter the number for which you want the multiplication table: "))
for i in range(1, 11):
    print(i)
```
**Output**
```
Enter the number for which you want the multiplication table: 5
1
2
3
4
5
6
7
8
9
10
```

### 2. Generate the Multiplication Table

```python
for i in range(1, 11):
    result = number * i
    print(result)
```
**Output**
```
5
10
15
20
25
30
35
40
45
50
```

### 3. Display the Multiplication Table (formatted)

```python
for i in range(1, 11):
    result = number * i
    print(number, "x", i, "=", result)
```
**Output**
```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```

---

## Task 3: Function — BMI Calculator

**Problem Statement:** calculate Body Mass Index (BMI).
**Formula:** `BMI = weight (kg) / [height (m)]²`

```python
def calculate_bmi(weight, height):
    bmi = weight / (height ** 2)
    return bmi

weight = float(input("Enter your weight in kg: "))
height = float(input("Enter your height in meters: "))
bmi = calculate_bmi(weight, height)

print(bmi)
```

**Output**
```
Enter your weight in kg: 95
Enter your height in meters: 1.60
37.10937499999999
```

> **Tip:** to make the output more readable, round it: `print(round(bmi, 2))` → `37.11`.

---

## Concepts Covered

- **`while` loops:** condition-controlled repetition, decrementing a counter (`attempts`)
- **Control statements:** `continue` (skip to next iteration), `break` (exit loop early), `else` on a loop (runs only if the loop completes without `break`)
- **`for` loops & `range()`:** iterating a fixed number of times, building a sequence of calculated values
- **Functions:** defining a function with parameters (`def calculate_bmi(weight, height)`), returning a value with `return`
- **Type casting:** `int(input(...))` and `float(input(...))` to convert user input from strings to numbers

## How to Run

```bash
python assignment3.py
```

Requires Python 3.x. No external libraries needed (`random` is part of the standard library).
