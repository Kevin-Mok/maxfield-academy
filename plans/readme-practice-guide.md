# README Practice Guide Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a root README that teaches someone how to use this repo to practice sliding-window problems and test their own answers.

**Architecture:** Keep the repo structure unchanged and document the existing workflow exposed by each standalone Python scaffold. Ground every README claim in the actual file layout and verified CLI behavior, especially the default example mode and the `--test` unittest path.

**Tech Stack:** Markdown, Python 3, `argparse`, `unittest`

---

### Task 1: Inspect the existing practice scaffolds

**Files:**
- Modify: `plans/readme-practice-guide.md`
- Read: `sliding-window/1-best-k-day-step-streak.py`
- Read: `sliding-window/2-shortest-study-sprint.py`
- Read: `sliding-window/3-longest-club-code-with-limited-symbols.py`
- Read: `sliding-window/hw-smallest-announcement-clip.py`

- [x] **Step 1: Capture the starting git status**

Run: `git status --short`
Expected: current tracked/untracked state is recorded before repo edits

- [x] **Step 2: Read the problem scaffold files**

Run: `sed -n '1,260p' sliding-window/*.py`
Expected: confirm each file contains a problem statement, stub function, example runner, and `--test` mode

- [x] **Step 3: Verify the actual CLI behavior**

Run: `python3 sliding-window/1-best-k-day-step-streak.py --help`
Expected: shows `--test` as the main supported flag

### Task 2: Write the README

**Files:**
- Create: `README.md`
- Modify: `plans/readme-practice-guide.md`

- [x] **Step 1: Draft a user-facing repo overview**

Expected: explain what this repo is, who it helps, and how the practice loop works

- [x] **Step 2: Document the available problem files**

Expected: list each scaffold with its focus area and target function

- [x] **Step 3: Document how to test answers**

Expected: explain the difference between running a file normally and running it with `--test`

### Task 3: Verify README accuracy

**Files:**
- Modify: `plans/readme-practice-guide.md`
- Verify: `README.md`

- [x] **Step 1: Re-run the documented commands**

Run: `python3 sliding-window/1-best-k-day-step-streak.py`
Expected: prints the prompt plus example case and shows the implementation is still needed

- [x] **Step 2: Re-run the documented test path**

Run: `python3 sliding-window/1-best-k-day-step-streak.py --test`
Expected: currently fails because the scaffold is unimplemented, proving the README's testing guidance is honest

- [x] **Step 3: Review repo changes**

Run: `git status --short`
Expected: only `README.md` and `plans/readme-practice-guide.md` appear as new repo changes
