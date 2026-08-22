<div align="center">

# Fundamentals of Python — First Programs
### Arewa DataScience Academy · Python Fundamentals

**Based on:** *Fundamentals of Python: First Programs* (3rd ed.) — Kenneth A. Lambert

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Beginner Friendly](https://img.shields.io/badge/Level-Beginner-brightgreen.svg)](#prerequisites)
[![Next Step: ML Course](https://img.shields.io/badge/Next%20Step-Intro%20to%20ML-8A2BE2.svg)](#whats-next--from-python-to-machine-learning)

</div>

---

> **This is the on-ramp to the Introduction to Machine Learning course.**
> Completing these 8 sessions satisfies the *"some Python experience (loops, functions, lists)"* prerequisite for the ML summer school. Start here if you're new to programming.

---

## Table of Contents

- [About This Course](#about-this-course)
- [Key Features](#key-features)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
- [Weekly Schedule](#weekly-schedule)
- [Lab Notebooks](#lab-notebooks)
- [Getting Started](#getting-started)
- [What's Next](#whats-next--from-python-to-machine-learning)
- [Recommended Resources](#recommended-resources)
- [Contributing](#contributing)
- [License](#license)

---

## About This Course

This is an **8-session introduction to programming with Python**, designed for people who have never written code before. Each session is **1 hour** — a short, focused walk-through of one core idea followed by hands-on practice.

The course is deliberately scoped to the Python language itself: variables, data types, decisions, loops, strings, collections, and functions. We skip broader computer-science survey topics (GUIs, networking, complexity analysis) so beginners leave fluent in writing small, correct programs.

This is the **foundation course of the Arewa DataScience Academy pathway**: finish here, and you're ready to move directly into the Introduction to Machine Learning course with the Python skills it assumes.

---

## Key Features

- **8 focused sessions** — one core idea per hour, no filler
- **8 lab notebooks** — Guided → Fill-in-the-Blank → Challenge structure
- **Consistent pedagogy** — every lab follows the same three-part format for predictable pacing
- **Pure standard-library Python** — no external packages to install or break
- **Textbook-aligned** — every session maps to a chapter of Lambert's *First Programs* (3rd ed.)
- **A clear next step** — flows directly into the Introduction to Machine Learning course

---

## Prerequisites

| Skill | Level Required |
|---|---|
| Programming | None — this is the starting point |
| Computer use | Comfortable installing software and using a web browser |
| Math | Basic arithmetic; no algebra required |
| Hardware | Any laptop, or just a browser (for Google Colab) |

No prior coding, command-line, or math background is assumed. If you can use a web browser, you can take this course.

---

## Setup and Installation

### 2026 Cohort: Getting Started Guide

This cohort's setup is a single, self-contained guide: **[Getting Started with VS Code for Data Science](getting-started-vscode.md)**. It replaces the separate per-topic guides used by earlier cohorts with one walkthrough covering Windows, macOS, and Linux side by side.

Work through it before Session 1. By the end of it, you are expected to be able to:

- Navigate VS Code — the Activity Bar, the integrated terminal, and the Command Palette
- Use basic command line operations (`pwd`, `ls`, `cd`, `mkdir`, and safely deleting files/folders) without hesitation
- Install and use **uv** to manage Python versions and project dependencies
- Create, activate, and deactivate a Python virtual environment, and explain why projects need one
- Install Git, configure your identity, and create/push a repository to GitHub
- Write and preview basic **Markdown** — headings, lists, links, tables, and code blocks — for READMEs and notebook cells
- Build, run, and push a small end-to-end Python project (script **and** notebook) using the tools above

| Section | Link |
| --- | --- |
| Full guide | [getting-started-vscode.md](getting-started-vscode.md) |
| Installing VS Code | [§3](getting-started-vscode.md#3-installing-vs-code) |
| Basic command line operations | [§6](getting-started-vscode.md#6-basic-command-line-operations) |
| Installing uv & Python | [§7–8](getting-started-vscode.md#7-installing-uv) |
| Virtual environments with uv | [§9](getting-started-vscode.md#9-creating-a-virtual-environment-with-uv) |
| Git & GitHub | [§10–11](getting-started-vscode.md#10-installing-git) |
| Introduction to Markdown | [§12](getting-started-vscode.md#12-introduction-to-markdown) |
| Setup checklist | [§19](getting-started-vscode.md#19-setup-checklist) |

### Previous Cohort References

The Arewa DataScience Fellowship's original setup guides remain available for reference — useful if you want a second explanation of a topic, or recordings to watch alongside this year's written guide.

| Title | Resource | Recording |
| --- | --- | --- |
| Initial Setup | [macOS](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/macOS.md) · [Windows](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/WINDOWS.md) · [Linux](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/LINUX.md#set-up-instructions-for-linux) | [Recording 1](https://www.youtube.com/watch?v=bRW5r7TK6KM) |
| VS Code for Python | [Fellowship Guide](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/vscode.md) | [Recording 1](https://www.youtube.com/watch?v=pmUkRRqtpEY) · [Recording 2](https://youtu.be/CjIhMiXsoqw) |
| Basic Command Line Operations | [Command Line](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/commandline.md) | [Recording 1](https://youtu.be/VgiP2-pHF3Y) |
| Setup Git and GitHub | [Git / GitHub](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/github.md) | [Recording 1](https://www.youtube.com/watch?v=FN4J5wHK898) · [Recording 2](https://youtu.be/KR_f0ARgzpc) |
| Python Virtual Environments | [Virtual Environment](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/python-venv.md) | [Recording 1](https://youtu.be/iszkG8QSPng) |
| Introduction to Markdown | [Markdown](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/markdown.md) | [Recording 1](https://www.youtube.com/watch?v=oNwEag0eqwE) |
| Google Colab | Coming soon | [Recording 1](https://youtu.be/3P5PgSzHPmI) |

---

## Weekly Schedule

**Format:** 1 hour per session · short lecture + hands-on lab · 8 sessions total

> Each session is paced for true beginners. Loops get a session and a half, and functions span two sessions — that's where first-timers actually get stuck, so we slow down there on purpose.

| # | Topic | Slides | Lab | Recording | Key Concepts | Reading (Lambert) | Instructor |
|:---:|---|:---:|:---:|:---:|---|:---:|:---:|
| 1 | First Programs & the Shell | TBA | TBA | TBA | The edit–run–debug loop, `print`, `input`, variables, comments | Ch. 1, §2.1–2.2 | TBA |
| 2 | Data Types & Expressions | TBA | TBA | TBA | `int` / `float` / `str`, arithmetic, precedence, type conversion, f-strings | Ch. 2 | TBA |
| 3 | Making Decisions | TBA | TBA | TBA | Booleans, comparison & logical operators, `if` / `elif` / `else` | Ch. 3 (selection) | TBA |
| 4 | Repetition with Loops | TBA | TBA | TBA | `while`, `for`, `range`, accumulator & sentinel patterns | Ch. 3 (loops) | TBA |
| 5 | Loop Patterns & Nested Logic | TBA | TBA | TBA | Nested loops, combining loops with conditions, input validation, debugging | Ch. 3 (cont.) | TBA |
| 6 | Strings & Lists | TBA | TBA | TBA | Indexing, slicing, string methods, list operations, iteration | Ch. 4, §5.1 | TBA |
| 7 | Dictionaries & First Functions | TBA | TBA | TBA | Key/value lookup, dict methods, defining functions, parameters, `return` | Ch. 5, §6.1 | TBA |
| 8 | Functions in Depth & Capstone | TBA | TBA | TBA | Scope, multiple parameters, decomposition, end-to-end capstone program | Ch. 6 | TBA |

*Slide decks, lab notebooks, and session recordings will be linked here as each session is delivered.*

---

## Lab Notebooks

Every lab follows the same structure to make pacing predictable:

| Section | Duration | Description |
|---|:---:|---|
| **Part A — Guided** | ~15 min | Pre-filled code — run cells and observe outputs carefully |
| **Part B — Fill in the Blank** | ~25 min | Skeleton code with placeholders to complete |
| **Part C — Challenge** | ~15 min | Open-ended extension problems for fast finishers |

All notebooks will run on **Google Colab** — no local setup required. Colab links for each lab will be added here as they are published.

| Lab | Topic |
|:---:|---|
| 01 | First Programs & Variables |
| 02 | Numbers, Strings & Expressions |
| 03 | Branching: `if` / `elif` / `else` |
| 04 | Loops: `while` & `for` |
| 05 | Nested Loops & Validation |
| 06 | Strings & Lists |
| 07 | Dictionaries & Functions |
| 08 | Functions & Capstone Project |

---

## Getting Started

### Option 1: Google Colab (recommended for beginners)

No setup needed. Once lab notebooks are published, open them directly in your browser via Colab — nothing to install.

### Option 2: Local Setup

```bash
# Clone the repository
git clone https://github.com/arewadataScience/ArewaDS-Introduction-to-Python-2026.git
cd ArewaDS-Introduction-to-Python-2026

# (Optional) create a virtual environment
python -m venv py-env
source py-env/bin/activate       # macOS/Linux
py-env\Scripts\activate          # Windows

# Install Jupyter to run the lab notebooks locally
pip install -r requirements.txt

# Launch the labs
jupyter notebook labs/
```

**`requirements.txt`:**
```
jupyter
```

> The course itself uses only Python's standard library — there are no data-science packages to install. Jupyter is needed only if you want to run the lab notebooks on your own machine instead of in Colab.

---

## What's Next — From Python to Machine Learning

This course is **Stage 1** of the Arewa DataScience pathway. Once you can comfortably write loops, functions, and small programs from scratch, you're ready for what comes next:

| Stage | Course | You'll learn |
|:---:|---|---|
| **1** | **Fundamentals of Python** *(this course)* | Variables, loops, strings, collections, functions |
| **2** | **Introduction to Machine Learning** | scikit-learn, model building, evaluation, the full ML landscape |

The ML course assumes you can read and write Python at the level this course produces — finishing the capstone in Session 8 is your green light to enroll.

---

## Recommended Resources

### Primary Textbook
- **Fundamentals of Python: First Programs** (3rd ed.) — Kenneth A. Lambert (Cengage Learning). Every session in this course maps to a chapter of this book.

### Supplementary Reading (free online)
- [Think Python — Allen B. Downey](https://greenteapress.com/wp/think-python-2e/)
- [Automate the Boring Stuff with Python — Al Sweigart](https://automatetheboringstuff.com/)
- [The Official Python Tutorial](https://docs.python.org/3/tutorial/)

### Practice
- [Exercism — Python Track](https://exercism.org/tracks/python) *(free, mentored)*
- [HackerRank — Python](https://www.hackerrank.com/domains/python)
- [Codewars](https://www.codewars.com/) — bite-sized practice problems

---

## Contributing

Found a typo in a notebook? Have a clearer challenge problem? Pull requests are welcome.

1. Fork the repository
2. Create a feature branch (`git checkout -b fix/lab-03-typo`)
3. Commit your changes
4. Open a pull request

---

## License

This course material is released under the [MIT License](LICENSE). The slides and exercises are based on content from *Fundamentals of Python: First Programs* by Kenneth A. Lambert (Cengage Learning) — please respect the original work's copyright when sharing.

---

<div align="center">

Arewa DataScience Academy

</div>
