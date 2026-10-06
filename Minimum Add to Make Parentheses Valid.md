# LeetCode 921 - Minimum Add to Make Parentheses Valid

## Problem

Given a string `s` containing `(` and `)`, return the minimum number of parentheses that must be inserted to make the string valid.

Example:
Input: `s = "())"`
Output: `1`

## Algorithm

- `open` = number of unmatched `(`
- `answer` = number of `(` needed for unmatched `)`

For every character:
- If `(` → `open++`
- If `)`:
  - If `open > 0` → `open--`
  - Else → `answer++`

At the end, remaining `open` needs the same number of `)`.

Final Answer = `answer + open`

## Java Solution
```java
class Solution {
    public int minAddToMakeValid(String s) {
        int open = 0;
        int answer = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                open++;
            } else {
                if (open > 0) {
                    open--;
                } else {
                    answer++;
                }
            }
        }

        return answer + open;
    }
}
```
## Dry Run

For `s = "())"`:

`(` → open = 1  
`)` → open = 0  
`)` → answer = 1

Final:

answer + open = 1 + 0 = 1

## Complexity

- Time: O(n)
- Space: O(1)

## Key Idea

`(` → open++

`)` → if open > 0 → open--
      else → answer++

Final Answer = answer + open
