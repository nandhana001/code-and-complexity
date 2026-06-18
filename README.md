# code-and-complexity
 Two solutions with different time complexities.From brute force to optimal solutions 
 # LeetCode 20. Valid Parentheses

## Approach 1: Using String Replacement

### Idea
Repeatedly remove valid pairs `"()"`, `"{}"`, and `"[]"` until no more replacements are possible.

### Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        while "()" in s or "{}" in s or "[]" in s:
            s = s.replace("()", "")
            s = s.replace("{}", "")
            s = s.replace("[]", "")
        return s == ""
```

### Complexity Analysis
- Time Complexity: O(n²)
- Space Complexity: O(n)

---

## Approach 2: Using Stack

### Idea
A closing bracket must match the most recent unmatched opening bracket, which naturally suggests a stack.

### Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        pairs = {
            ')': '(',
            '}': '{',
            ']': '['
        }

        for ch in s:
            if ch in pairs:
                if not stack or stack.pop() != pairs[ch]:
                    return False
            else:
                stack.append(ch)

        return not stack
```

### Complexity Analysis
- Time Complexity: O(n)
- Space Complexity: O(n)

---

## Comparison

| Approach | Time Complexity | Space Complexity |
|------------|----------------|-----------------|
| String Replacement | O(n²) | O(n) |
| Stack | O(n) | O(n) |

## Takeaway

The string replacement approach is intuitive but inefficient because the string is traversed multiple times. The stack-based solution is optimal and is the preferred approach for this problem.
