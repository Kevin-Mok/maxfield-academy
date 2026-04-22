# Maxfield Problem Practice

This repo is a small Python practice set for working through sliding-window interview problems one file at a time. It is useful when you want a fast loop: read a prompt, implement the target function in place, run the example output, and then run the built-in tests to check whether your answer holds up on edge cases.

## Tech Stack And Why Chosen

- Python 3: keeps the practice loop lightweight and easy to run on any machine with no install step beyond Python.
- Single-file problem scaffolds: each exercise includes the prompt, function stub, examples, and tests together so you can focus on solving instead of wiring up tooling.
- `argparse`: gives each problem a tiny CLI with a consistent `--test` flag.
- `unittest`: provides a built-in way to verify answers without external dependencies.

## Repo Layout

All practice problems currently live in `sliding-window/`.

| File | Topic | Function to implement |
| --- | --- | --- |
| `sliding-window/1-best-k-day-step-streak.py` | fixed-size maximum sum window | `best_k_day_steps` |
| `sliding-window/2-shortest-study-sprint.py` | shortest window meeting a target sum | `shortest_study_sprint` |
| `sliding-window/3-longest-club-code-with-limited-symbols.py` | longest substring with at most `k` distinct values | `longest_code_with_limited_symbols` |
| `sliding-window/hw-smallest-announcement-clip.py` | minimum window substring | `smallest_announcement_clip` |

Each file follows the same pattern:

1. Read the `PROBLEM_STATEMENT`.
2. Implement the stub function near the top of the file.
3. Use the example runner to sanity-check your thinking.
4. Run the full test suite in that file.

## Getting Started

You only need Python 3 for this repo. There are no external packages or setup scripts right now.

```bash
python3 --version
```

If that command works, you can start practicing immediately.

## How To Practice

Pick one file and solve only the target function. You do not need to create a separate test file or runner.

Example workflow:

```bash
python3 sliding-window/1-best-k-day-step-streak.py
```

Running a file without flags prints:

- the problem statement
- one example case
- the expected answer
- your current actual answer

Before you implement the function, the scaffold will show a "not implemented" message. That is expected.

## How To Test Answers

When you want to check your solution against the built-in cases, run the same file with `--test`:

```bash
python3 sliding-window/1-best-k-day-step-streak.py --test
```

To test a different problem, replace the filename with any other scaffold in `sliding-window/`.

What `--test` does:

- runs the `GeneratedTests` suite inside that file
- checks the example, edge, and tricky cases
- fails immediately if the function is still unimplemented
- fails if your implementation raises an unexpected exception

What passing means:

- your current implementation matches every case bundled into that file

What failing means:

- either the function is not implemented yet
- or your logic missed one of the covered scenarios

## Suggested Solve Loop

Use this loop for any problem in the repo:

1. Run the file once with no flags to read the prompt and example.
2. Implement the target function.
3. Re-run the file with no flags to see whether the example now matches.
4. Run the file with `--test`.
5. If a test fails, read the failing case name and adjust your logic.

## Notes

- There is no combined test runner yet; tests are per problem file.
- The only documented flag right now is `--test`.
- If you want more practice, add another standalone scaffold that follows the same shape as the existing files.
