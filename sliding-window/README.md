# Sliding Window Problems

This folder is a short progression of sliding-window practice problems for students.
The goal is to recognize which kind of window a prompt is asking for, then implement
the missing function in each scaffold without jumping straight to brute force.

These exercises move from:

1. Fixed-size windows on arrays
2. Variable-size windows on positive integers
3. Variable-size windows with frequency maps
4. Minimum-window style substring coverage

## How To Use This Folder

Each file already contains:

- the problem statement
- an unimplemented function
- one example case
- extra edge and tricky test cases

Suggested workflow:

1. Read the problem below before opening the file.
2. Open the matching scaffold and implement the missing function.
3. Run the file once to view the prompt example:

```bash
python 1-best-k-day-step-streak.py
```

4. Run the tests after you implement the function:

```bash
python 1-best-k-day-step-streak.py --test
```

Replace the filename with the problem you are solving.

## Before You Start

Ask yourself these questions for each prompt:

- Is the window size fixed, or can it grow and shrink?
- What makes a window valid?
- When the window changes, what information must I update in O(1)?
- Do I need just a sum, or do I need counts/frequencies?
- What should happen on edge cases like empty input, invalid `k`, or impossible targets?

## Problem Order

| # | Problem | File | Main Pattern |
| --- | --- | --- | --- |
| 1 | Best K-Day Step Streak | `1-best-k-day-step-streak.py` | Fixed-size window |
| 2 | Shortest Study Sprint | `2-shortest-study-sprint.py` | Variable-size window |
| 3 | Longest Club Code With Limited Symbols | `3-longest-club-code-with-limited-symbols.py` | Variable-size window + frequency map |
| 4 | Smallest Announcement Clip | `hw-smallest-announcement-clip.py` | Minimum covering window |

## 1. Best K-Day Step Streak

File: `1-best-k-day-step-streak.py`

Implement:

```python
def best_k_day_steps(steps: list[int], k: int) -> int | None:
```

### Your Task

You get daily step counts and an integer `k`. Return the maximum total steps
over any window of exactly `k` consecutive days.

If `k <= 0` or `k` is bigger than the input size, return `None`.

### Example

```text
steps = [4, 2, 7, 1, 8, 3]
k = 3

Output: 16
```

### What To Notice

- The window size never changes.
- You are comparing totals across windows of exactly the same length.
- Invalid `k` values should be handled before any sliding happens.

<details>
<summary>Spoiler hints</summary>

- Start by computing the total of the first full window.
- When you slide right by one step, add the new value entering the window and subtract the value leaving it.
- Keep track of the best total seen so far.
- Watch out for off-by-one mistakes when deciding which element leaves the window.

</details>

## 2. Shortest Study Sprint

File: `2-shortest-study-sprint.py`

Implement:

```python
def shortest_study_sprint(blocks: list[int], target: int) -> int:
```

### Your Task

You get focused minutes per study block and a target. Find the shortest
consecutive block total that is at least the target, or `0` if no such block
exists.

### Example

```text
blocks = [2, 1, 5, 2, 3, 2]
target = 7

Output: 2
```

### What To Notice

- The window size is not fixed.
- Once the current total reaches the target, a smaller valid window might exist inside it.
- The answer is a length, not the sum itself.

<details>
<summary>Spoiler hints</summary>

- Grow the window with a `right` pointer until the running total is large enough.
- Once the window is valid, shrink from the left as much as possible while it stays valid.
- You may need to shrink multiple times after one expansion, so think carefully about `while` versus `if`.
- If no window ever reaches the target, return `0`.

</details>

## 3. Longest Club Code With Limited Symbols

File: `3-longest-club-code-with-limited-symbols.py`

Implement:

```python
def longest_code_with_limited_symbols(code: str, k: int) -> int:
```

### Your Task

Given a string and `k`, find the longest contiguous section with at most `k`
distinct symbols.

### Example

```text
code = "AAHBBCCB"
k = 2

Output: 5
```

### What To Notice

- This is still a sliding window, but a sum is not enough anymore.
- You need to know how many times each character appears in the current window.
- The window is valid only when it contains at most `k` distinct symbols.

<details>
<summary>Spoiler hints</summary>

- Use a dictionary to track character frequencies inside the current window.
- Expanding the window may make it invalid; if that happens, move `left` until it becomes valid again.
- Remove a character from your frequency map when its count drops to zero.
- Update the best length only when the current window is valid.

</details>

## 4. Smallest Announcement Clip

File: `hw-smallest-announcement-clip.py`

Implement:

```python
def smallest_announcement_clip(announcement: str, required: list[str]) -> str:
```

### Your Task

Given a string and a required list, find the shortest consecutive substring
containing all required characters at least once. Return an empty string if it
is impossible.

### Example

```text
announcement = "xbacbabca"
required = ["a", "b", "c"]

Output: "bac"
```

### What To Notice

- This problem is about the smallest valid window, not the longest.
- Order does not matter, but coverage does.
- Characters not in the required list may still appear inside the best answer.

<details>
<summary>Spoiler hints</summary>

- Track which required characters are currently covered by the window.
- A set is helpful for quick membership checks, but you still need counts for the current window.
- Once every required character is present, try shrinking from the left to make the window as small as possible.
- Record the best answer before you shrink past validity.

</details>

## Common Pitfalls Across These Problems

- Recomputing every window from scratch instead of updating state incrementally
- Using `if` when repeated shrinking really needs `while`
- Forgetting to handle invalid or impossible cases
- Updating the answer while the window is still invalid
- Losing track of duplicates by using a set when counts are actually required

## Final Reminder

Try to identify the window rule before writing code:

- Fixed-size window: add one thing, remove one thing
- Variable-size window: expand until valid, then shrink carefully
- Frequency-map window: validity depends on counts, not just membership

If you can explain why the window becomes valid and why it becomes invalid, you
are usually very close to the implementation.
