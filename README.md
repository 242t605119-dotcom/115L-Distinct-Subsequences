# LeetCode 115 - Distinct Subsequences

## Problem

Given two strings `s` and `t`, return the number of distinct subsequences of `s` which equals `t`.

A subsequence is formed by deleting some characters from a string without changing the order of the remaining characters.

## Example 1

### Input

```text
s = "rabbbit"
t = "rabbit"
```

### Output

```text
3
```

### Explanation

There are three different ways to remove one `b` from `"rabbbit"` to obtain `"rabbit"`.

## Example 2

### Input

```text
s = "babgbag"
t = "bag"
```

### Output

```text
5
```

There are five distinct subsequences of `s` that form `"bag"`.

## Approach

This problem can be solved using **Dynamic Programming (DP)**.

Let `dp[i][j]` represent the number of ways to form the first `j` characters of `t` using the first `i` characters of `s`.

For every character:

* If the characters are different, the current character of `s` cannot be used.
* If they are equal, there are two choices:

  * Use the current character.
  * Skip the current character.

Therefore, when the characters match:

```text
dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
```

When they do not match:

```text
dp[i][j] = dp[i-1][j]
```

An optimized one-dimensional DP array can be used to reduce memory usage.

## Algorithm

1. Create a DP array of size `len(t) + 1`.
2. Set `dp[0] = 1` because an empty string can be formed in one way.
3. Traverse the characters of `s`.
4. Traverse `t` backwards.
5. If the characters match, add the previous DP value to the current value.
6. The final `dp[len(t)]` gives the number of distinct subsequences.

## Complexity

* **Time Complexity:** `O(m × n)`
* **Space Complexity:** `O(n)`

Where `m` is the length of `s` and `n` is the length of `t`.

## LeetCode Details

**Problem Number:** 115
**Problem Name:** Distinct Subsequences
**Difficulty:** Hard
**Topics:** String, Dynamic Programming

## Language

Python 3

## File

`solution.py`

## Author

T.Nandhini
