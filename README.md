<div align="center">

# 🐍 Fundamentals of Python — First Programs
### Arewa DataScience Academy · Python Fundamentals

**Based on:** *Fundamentals of Python: First Programs* (3rd ed.) — Kenneth A. Lambert
**Instructor:** Dr. [Your Name]
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Beginner Friendly](https://img.shields.io/badge/Level-Beginner-brightgreen.svg)](#prerequisites)
[![Next Step: ML Course](https://img.shields.io/badge/Next%20Step-Intro%20to%20ML-8A2BE2.svg)](#whats-next--from-python-to-machine-learning)

</div>

---

> 🎯 **This is the on-ramp to the [Introduction to Machine Learning](#) course.**
> Completing these 8 sessions satisfies the *"some Python experience (loops, functions, lists)"* prerequisite for the ML summer school. Start here if you're new to programming.

---

## Table of Contents

- [About This Course](#about-this-course)
- [Key Features](#key-features)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
- [Weekly Schedule](#weekly-schedule)
- [Lab Notebooks](#lab-notebooks)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
- [What's Next](#whats-next--from-python-to-machine-learning)
- [Recommended Resources](#recommended-resources)
- [Contributing](#contributing)
- [License](#license)

---

## About This Course

This is an **8-session introduction to programming with Python**, designed for people who have *never written code before*. Each session is **1 hour** — a short, focused walk-through of one core idea followed by hands-on practice.

The course is deliberately scoped to **the Python language itself** — variables, data types, decisions, loops, strings, collections, and functions. We skip the broader computer-science survey topics (GUIs, networking, complexity analysis) so that beginners leave fluent in writing small, correct programs.

It is the **foundation course of the Arewa DataScience Academy pathway**: finish here, and you're ready to move straight into the Introduction to Machine Learning course with the Python skills it assumes.

---

## Key Features

- 📚 **8 focused sessions** — one core idea per hour, no filler
- 💻 **8 lab notebooks** — Guided → Fill-in-the-blank → Challenge structure
- 🧪 **Consistent pedagogy** — every lab has the same 3-part format for predictable pacing
- 🐍 **Pure standard-library Python** — no external packages to install or break
- 📖 **Textbook-aligned** — every session maps to chapters of Lambert's *First Programs* (3rd ed.)
- 🪜 **A clear next step** — flows directly into the [Intro to Machine Learning](#) course

---

## Prerequisites

| Skill | Level Required |
|---|---|
| Programming | **None** — this is the starting point |
| Computer use | Comfortable installing software and using a web browser |
| Math | Basic arithmetic; no algebra required |
| Hardware | Any laptop, or just a browser (for Google Colab) |

No prior coding, command-line, or math background is assumed. If you can use a web browser, you can take this course.

---

## Setup and Installation

These guides walk you through the tools you'll use throughout the Arewa DataScience pathway — installing Python, the command line, Git/GitHub, virtual environments, VSCode, Markdown, and Google Colab. They are shared with the rest of the fellowship, so you set them up once here and reuse them in the ML course.

| Title | Resource | Recording |
| --- | --- | --- |
| Initial Setup | [macOS](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/macOS.md) \| [Windows](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/WINDOWS.md) \| [Linux](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/LINUX.md#set-up-instructions-for-linux) | [Tutorial](https://www.youtube.com/watch?v=bRW5r7TK6KM) |
| Basic Command Line Operations | [Command Line](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/commandline.md) | [Recording](https://youtu.be/VgiP2-pHF3Y) |
| Setup Git and GitHub | [Git / GitHub](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/github.md) | [Recording](https://www.youtube.com/watch?v=FN4J5wHK898) |
| Python Virtual Environments | [Virtual Environment](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/python-venv.md) | [Recording](https://youtu.be/iszkG8QSPng) |
| VSCode for Python | [VSCode Setup](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/vscode.md) | [Recording](https://www.youtube.com/watch?v=pmUkRRqtpEY) |
| Introduction to Markdown | [Markdown](https://github.com/arewadataScience/python-programming-fellowship/blob/main/00_Stage-1-Getting-Started/markdown.md) | [Recording](https://www.youtube.com/watch?v=oNwEag0eqwE) |
| Google Colab | [Google Colab](#) | [Recording](https://youtu.be/3P5PgSzHPmI) |

---

## Weekly Schedule

**Format:** 1 hour/session · short lecture + hands-on lab · 8 sessions

> ⏱️ Each session is paced for true beginners. Loops get a session and a half, and functions span two sessions — that's where first-timers actually get stuck, so we slow down there on purpose.

| # | Topic | Slides | Lab | Recording | Key Concepts | Reading (Lambert) |
|:---:|---|:---:|:---:|:---:|---|:---:|
| 1 | First Programs & the Shell | [📊 Slides](#) | [💻 Lab 01](#) | [🎥 Recording](#) | The edit–run–debug loop, \`print\`, \`input\`, variables, comments | Ch. 1, §2.1–2.2 |
| 2 | Data Types & Expressions | [📊 Slides](#) | [💻 Lab 02](#) | [🎥 Recording](#) | \`int\` / \`float\` / \`str\`, arithmetic, precedence, type conversion, f-strings | Ch. 2 |
| 3 | Making Decisions | [📊 Slides](#) | [💻 Lab 03](#) | [🎥 Recording](#) | Booleans, comparison & logical operators, \`if\` / \`elif\` / \`else\` | Ch. 3 (selection) |
| 4 | Repetition with Loops | [📊 Slides](#) | [💻 Lab 04](#) | [🎥 Recording](#) | \`while\`, \`for\`, \`range\`, accumulator & sentinel patterns | Ch. 3 (loops) |
| 5 | Loop Patterns & Nested Logic | [📊 Slides](#) | [💻 Lab 05](#) | [🎥 Recording](#) | Nested loops, combining loops + conditions, input validation, debugging | Ch. 3 (cont.) |
| 6 | Strings & Lists | [📊 Slides](#) | [💻 Lab 06](#) | [🎥 Recording](#) | Indexing, slicing, string methods, list operations, iteration | Ch. 4, §5.1 |
| 7 | Dictionaries & First Functions | [📊 Slides](#) | [💻 Lab 07](#) | [🎥 Recording](#) | Key/value lookup, dict methods, defining functions, parameters, \`return\` | Ch. 5, §6.1 |
| 8 | Functions in Depth & Capstone | [📊 Slides](#) | [💻 Lab 08](#) | [🎥 Recording](#) | Scope, multiple parameters, decomposition, end-to-end capstone program | Ch. 6 |

---

## Lab Notebooks

Every lab follows the same structure to make pacing predictable:

| Section | Duration | Description |
|---|:---:|---|
| **Part A — Guided** | ~15 min | Pre-filled code — run cells and observe outputs carefully |
| **Part B — Fill in the Blank** | ~25 min | Skeleton code with \`???\` placeholders to complete |
| **Part C — Challenge** | ~15 min | Open-ended extension problems for fast finishers |

All notebooks run on **Google Colab** — no local setup required. Click any badge below to open directly:

| Lab | Topic | Open in Colab |
|:---:|---|:---:|
| 01 | First Programs & Variables | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 02 | Numbers, Strings & Expressions | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 03 | Branching: \`if\` / \`elif\` / \`else\` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 04 | Loops: \`while\` & \`for\` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 05 | Nested Loops & Validation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 06 | Strings & Lists | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 07 | Dictionaries & Functions | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |
| 08 | Functions & Capstone Project | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) |

---

## Getting Started

### Option 1: Google Colab (Recommended for beginners)

No setup needed. Click any **"Open in Colab"** badge above and start typing code in your browser. Nothing to install.

### Option 2: Local Setup

\`\`\`bash
# Clone the repository
git clone https://github.com/arewadataScience/python-programming-fellowship.git
cd python-programming-fellowship

# (Optional) create a virtual environment
python -m venv py-env
source py-env/bin/activate       # macOS/Linux
py-env\Scripts\activate          # Windows

# Install Jupyter to run the lab notebooks locally
pip install -r requirements.txt

# Launch the labs
jupyter notebook labs/
\`\`\`

**\`requirements.txt\`:**
\`\`\`
jupyter
\`\`\`

> 💡 The course itself uses **only Python's standard library** — there are no data-science packages to install. Jupyter is needed only if you want to run the lab notebooks on your own machine instead of in Colab.

---

## What's Next — From Python to Machine Learning

This course is **Stage 1** of the Arewa DataScience pathway. Once you can comfortably write loops, functions, and small programs from scratch, you're ready for what comes next:

| Stage | Course | You'll learn |
|:---:|---|---|
| **1** | 🐍 **Fundamentals of Python** *(this course)* | Variables, loops, strings, collections, functions |
| **2** | 🤖 [**Introduction to Machine Learning**](#) | scikit-learn, model building, evaluation, the full ML landscape |

The ML course assumes you can read and write Python at the level this course produces — so finishing the capstone in Session 8 is your green light to enroll.

---

## Recommended Resources

### Primary Textbook
- 📘 **Fundamentals of Python: First Programs (3rd ed.) — Kenneth A. Lambert** (Cengage Learning)
  Every session in this course maps to a chapter of this book.

### Supplementary Reading (free online)
- 📗 [Think Python — Allen B. Downey](https://greenteapress.com/wp/think-python-2e/)
- 📙 [Automate the Boring Stuff with Python — Al Sweigart](https://automatetheboringstuff.com/)
- 📕 [The Official Python Tutorial](https://docs.python.org/3/tutorial/)

### Practice
- 🏋️ [Exercism — Python Track](https://exercism.org/tracks/python) *(free, mentored)*
- 💡 [HackerRank — Python](https://www.hackerrank.com/domains/python)
- ⚔️ [Codewars](https://www.codewars.com/) — bite-sized practice problems

---

## Contributing

Found a typo in a notebook? Have a clearer challenge problem? Pull requests are welcome.

1. Fork the repository
2. Create a feature branch (\`git checkout -b fix/lab-03-typo\`)
3. Commit your changes
4. Open a pull request

---

## License

This course material is released under the [MIT License](LICENSE). The slides and exercises are based on content from *Fundamentals of Python: First Programs* by Kenneth A. Lambert (Cengage Learning) — please respect the original work's copyright when sharing.

---

<div align="center">

Made with ❤️ by Arewa DataScience Academy

</div>
