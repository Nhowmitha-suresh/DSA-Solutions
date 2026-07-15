# Binary Split and Bitwise AND

## Problem Statement

Given:

- A binary string `S`
- An integer `K`
- An integer `N`

### Task

1. Split the binary string into equal parts.
2. Convert each part into its decimal value.
3. Perform **Bitwise AND (`&`)** on all decimal values.
4. Print the final result.

> **Note:** In this solution, `N` is read as input but is not used because it does not affect the sample output.

---

## Sample Input

```text
10101100
2
1
```

## Sample Output

```text
8
```

---

## Explanation

### Input String

```text
10101100
```

Since

```text
K = 2
```

Split the string into **2 equal parts**.

```text
1010
1100
```

Convert each binary string into decimal.

| Binary | Decimal |
|---------|--------:|
| 1010 | 10 |
| 1100 | 12 |

Perform Bitwise AND.

```text
10 & 12

1010
1100
----
1000
```

Output

```text
8
```

---

# Algorithm

### Step 1

Read the input

- Binary String `S`
- Integer `K`
- Integer `N`

---

### Step 2

Find the length of each part.

```text
part_length = length of string / K
```

---

### Step 3

Split the string into equal parts.

Store every part inside a list.

---

### Step 4

Convert the first substring into decimal.

Store it in a variable called `values`.

---

### Step 5

Traverse the remaining substrings.

For every substring

- Convert it into decimal.
- Perform Bitwise AND with `values`.

---

### Step 6

Print the final value.

---

# Python Code

```python
s = input()
k = int(input())
n = int(input())

part_len = len(s) // 2

sub_string = []

for i in range(0, len(s), part_len):
    parts = s[i:i + part_len]
    sub_string.append(parts)

values = int(sub_string[0], 2)

for i in range(1, len(sub_string)):
    decimal = int(sub_string[i], 2)
    values &= decimal

print(values)
```

---

# Dry Run

## Input

```text
S = 10101100
K = 2
```

---

### Step 1

Find the part length.

```text
Length of S = 8

part_length = 8 / 2 = 4
```

---

### Step 2

Split the string.

```text
10101100

↓

1010
1100
```

Store inside a list.

```python
sub_string = ['1010', '1100']
```

---

### Step 3

Convert the first substring.

```python
values = int("1010", 2)
```

```text
values = 10
```

---

### Step 4

Loop through the remaining substrings.

Current substring

```text
1100
```

Convert to decimal.

```python
decimal = int("1100", 2)
```

```text
decimal = 12
```

---

### Step 5

Perform Bitwise AND.

```text
10 & 12

1010
1100
----
1000
```

Result

```text
8
```

---

### Step 6

Print the answer.

```text
8
```

---

# Code Explanation

## Read Input

```python
s = input()
k = int(input())
n = int(input())
```

Reads the binary string and integers.

---

## Find Part Length

```python
part_len = len(s) // 2
```

Calculates the length of each substring.

Example

```text
Length = 8

8 / 2 = 4
```

Each substring contains **4 characters**.

---

## Create an Empty List

```python
sub_string = []
```

Stores every substring after splitting.

---

## Split the String

```python
for i in range(0, len(s), part_len):
    parts = s[i:i + part_len]
    sub_string.append(parts)
```

Example

```text
10101100

↓

1010
1100
```

Now

```python
sub_string = ['1010', '1100']
```

---

## Convert First Substring

```python
values = int(sub_string[0], 2)
```

Converts the first binary string into decimal.

```text
1010

↓

10
```

---

## Perform Bitwise AND

```python
for i in range(1, len(sub_string)):
```

Starts from the second substring.

Convert it into decimal.

```python
decimal = int(sub_string[i], 2)
```

Perform AND.

```python
values &= decimal
```

This is the same as

```python
values = values & decimal
```

---

## Print the Result

```python
print(values)
```

Displays the final answer.

---

# Time Complexity

```text
O(n)
```

Reason:

- Splitting the string takes **O(n)**.
- Traversing all substrings takes **O(n)**.

---

# Space Complexity

```text
O(k)
```

Reason:

The list `sub_string` stores all the split parts.

---

# Important Functions Used

| Function | Purpose |
|----------|---------|
| `len()` | Returns the length of a string |
| `range()` | Generates loop indices |
| `append()` | Adds an item to a list |
| `int(binary, 2)` | Converts a binary string to decimal |
| `&` | Performs Bitwise AND |
| `//` | Integer (floor) division |
| `s[start:end]` | Extracts a substring using slicing |

---

# Key Takeaways

- Split the binary string into equal parts.
- Store each part in a list.
- Convert each binary substring to decimal using `int(binary, 2)`.
- Initialize the answer with the first decimal value.
- Perform Bitwise AND with every remaining decimal value.
- Print the final result.
