# Getting Started with VS Code for Data Science

### A step-by-step setup guide for Windows, macOS, and Linux

**Arewa Data Science Academy**

This guide takes you from a fresh computer to a working data science environment. It assumes no prior programming experience. If you come from chemistry, biology, or any other background where the laboratory is a physical space rather than a screen, this guide is written for you.

Work through the sections in order. Do not skip ahead, because each step depends on the one before it. Set aside about two hours for the whole process, and make sure you have a stable internet connection before you begin.

Wherever a step differs by operating system, you will see three tabs of instructions — **Windows**, **macOS**, and **Linux**. Follow only the one that matches your machine, and ignore the other two.

---

## Table of contents

1. [What we are building and why](#1-what-we-are-building-and-why)
2. [Before you begin](#2-before-you-begin)
3. [Installing VS Code](#3-installing-vs-code)
4. [A tour of the VS Code window](#4-a-tour-of-the-vs-code-window)
5. [The integrated terminal](#5-the-integrated-terminal)
6. [Basic command line operations](#6-basic-command-line-operations)
7. [Installing uv](#7-installing-uv)
8. [Installing Python with uv](#8-installing-python-with-uv)
9. [Creating a virtual environment with uv](#9-creating-a-virtual-environment-with-uv)
10. [Introduction to Markdown](#10-introduction-to-markdown)
11. [VS Code extensions for data science](#11-vs-code-extensions-for-data-science)
12. [Installing Git](#12-installing-git)
13. [Setting up GitHub](#13-setting-up-github)
14. [GitHub in VS Code: managing GitHub files](#14-github-in-vs-code-managing-github-files)
15. [VS Code and AI](#15-vs-code-and-ai)
16. [Your first project, end to end](#16-your-first-project-end-to-end)
17. [Pushing your project to GitHub](#17-pushing-your-project-to-github)
18. [Optional: conda and when you might need it](#18-optional-conda-and-when-you-might-need-it)
19. [Troubleshooting](#19-troubleshooting)
20. [Command reference card](#20-command-reference-card)
21. [Setup checklist](#21-setup-checklist)

---

## 1. What we are building and **why**

### 1.1 What is VS Code?

Visual Studio Code (usually shortened to VS Code) is a free text editor made by Microsoft, available for Windows, macOS, and Linux. Calling it a text editor undersells it. Think of it as a laboratory bench: a single surface where you keep your code, your data, your notes, your version history, and your command line, all within reach and all visible at once.

You could write Python in a plain text editor and run it from a separate window. Thousands of people did exactly that for years. VS Code simply removes the friction, so that you spend your attention on the analysis rather than on the mechanics of moving between windows.

### 1.2 Why not just use Jupyter in the browser, or Google Colab?

Both are good tools and you will use them. Colab in particular is excellent for quick experiments and for sharing work. However, they have limits that become painful quite quickly:

- Colab sessions expire, and your files disappear with them unless you take care.
- Notebooks alone do not scale to a real project with multiple files, reusable functions, and a data folder.
- Neither teaches you version control, which is how research code is actually managed and shared.
- Neither works offline, which matters when connectivity is unreliable.

VS Code runs on your own machine, keeps your work permanently, handles notebooks perfectly well, and prepares you for how professional and research teams actually operate.

### 1.3 What we will install

| Tool | What it does | Why you need it |
|---|---|---|
| **VS Code** | The editor | Where you will write and run everything |
| **uv** | Python and package manager | Installs Python, installs libraries, keeps projects separate |
| **Python** | The language | The language of most data science work |
| **Git** | Version control | Tracks every change you make and lets you undo mistakes |
| **GitHub** | Online home for code | Backup, collaboration, and your public portfolio |
| **Extensions** | Add-ons for VS Code | Notebooks, autocompletion, data viewing, error highlighting |

### 1.4 A note on the two managers you will hear about

You may have heard of Anaconda or conda. They are widely used in scientific computing and there is nothing wrong with them. On this course we will use **uv** instead, because it is dramatically faster, much smaller to download, installs Python for you, and produces reproducible projects with far less ceremony. Section 18 explains the cases where conda is still the better choice.

Do not install both and mix them in the same project. Pick one per project.

> **Want to go deeper?** Read [VS Code's own "Why VS Code" page](https://code.visualstudio.com/docs/editor/whyvscode) and the [uv documentation](https://docs.astral.sh/uv/) for the reasoning behind these tool choices. If you're curious, spend ten minutes after this session comparing uv's own pitch against conda's — it's a good exercise in reading two tools' documentation critically rather than taking either one's word for it.

---

## 2. Before you begin

### 2.1 Identify your operating system

You need to know which of the three you are using, because several steps ahead branch by OS.

- **Windows:** press `Windows key + R`, type `winver`, and press Enter. You need **Windows 10 (version 1809 or later) or Windows 11**.
- **macOS:** click the Apple menu, then **About This Mac**. You need **macOS 12 (Monterey) or later**. Note whether your Mac has an **Apple Silicon** chip (M1, M2, M3, M4) or an **Intel** chip — it is listed under "Chip" or "Processor".
- **Linux:** run `lsb_release -a` or `cat /etc/os-release` in a terminal. Any recent Ubuntu, Debian, Fedora, or similar distribution released in the last few years will work. This guide uses Ubuntu/Debian commands (`apt`); Fedora and Arch users should substitute their own package manager (`dnf`, `pacman`) where noted.

### 2.2 Check whether your machine is 64-bit

Almost every machine made in the last decade is 64-bit, and Apple Silicon Macs are a separate case handled automatically by their installers.

- **Windows:** open **Settings**, then **System**, then **About**. Look at **System type**. If it says ARM, note this down, because you will need the ARM64 downloads rather than the x64 ones at every step.
- **macOS:** the chip you identified in 2.1 already tells you this. Apple Silicon and Intel both get 64-bit builds; the installer picks the right one automatically on modern downloads.
- **Linux:** run `uname -m`. `x86_64` means standard 64-bit; `aarch64` means ARM64.

### 2.3 Free disk space

You need roughly **5 GB free**. Data science libraries are large.

- **Windows:** check your C drive in **File Explorer** under **This PC**.
- **macOS:** Apple menu, **About This Mac**, **Storage**.
- **Linux:** run `df -h ~` in a terminal.

### 2.4 Create a folder for your work

This step is small but it will save you many hours of confusion later.

Create a folder at:

| OS | Path |
|---|---|
| Windows | `C:\Users\YourName\projects` |
| macOS | `/Users/YourName/projects` |
| Linux | `/home/YourName/projects` |

Replace `YourName` with your username. On macOS and Linux, this path is more commonly written using the `~` shortcut for your home folder: `~/projects`.

> **Important.** Do not put your code inside a folder that is continuously synced by a cloud service — **OneDrive**, **iCloud Drive**, **Dropbox**, or **Google Drive** are the common offenders, along with **Desktop** and **Documents** when those are set to sync. These services synchronise files continuously, and they will fight with Python and Git over the thousands of small files a project creates. Symptoms include files that mysteriously vanish, environments that break overnight, and Git repositories that corrupt themselves. Keep your `projects` folder outside any synced location.

Also avoid spaces, accents, and special characters in folder and file names. `heart-disease-analysis` is a good name. `My Project (final) 2!` will cause trouble on every operating system.

> **Want to go deeper?** [GitHub's guidance on ignoring files](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) explains why certain folders should never be tracked by Git, which connects to the cloud-sync warning above. If interested, explore how your OS actually handles the special characters this section warns against — a small rabbit hole, but a useful one.

---

## 3. Installing VS Code

### Windows

1. Go to **https://code.visualstudio.com/download** and click the blue **Windows** button. This downloads the *User Installer* for x64, which is what you want. It does not require administrator rights, which matters if you are using a shared or university machine.
2. The file will be named something like `VSCodeUserSetup-x64-1.xx.x.exe` and will appear in your **Downloads** folder. Double-click it and work through the screens:
   1. **Licence agreement.** Select *I accept the agreement*, then **Next**.
   2. **Destination location.** Leave the default, then **Next**.
   3. **Start menu folder.** Leave the default, then **Next**.
   4. **Additional tasks.** This screen matters. Tick all of the following:
      - ☑ Create a desktop icon
      - ☑ Add "Open with Code" action to Windows Explorer file context menu
      - ☑ Add "Open with Code" action to Windows Explorer directory context menu
      - ☑ Register Code as an editor for supported file types
      - ☑ **Add to PATH** (this one is essential, and is normally ticked already)
   5. **Install**, then **Finish**.

The two "Open with Code" options mean you can right-click any folder in File Explorer and open it directly in VS Code. **Add to PATH** means you can type `code .` in any terminal to open the current folder in VS Code. If you miss this option, see section 19.4 for the fix.

### macOS

1. Go to **https://code.visualstudio.com/download** and click the **macOS** button matching your chip (Apple Silicon or Intel — see section 2.2).
2. Open the downloaded `.zip` file, which unpacks to `Visual Studio Code.app`. Drag it into your **Applications** folder.
3. Open it from **Applications** (or Spotlight, `Cmd + Space` then type "Visual Studio Code"). The first time, macOS will ask you to confirm you want to open an app downloaded from the internet — click **Open**.
4. Enable the `code` terminal command: inside VS Code, open the Command Palette (`Cmd + Shift + P`), type `Shell Command: Install 'code' command in PATH`, and run it.

### Linux

1. Go to **https://code.visualstudio.com/download** and download the `.deb` package (Debian/Ubuntu) or `.rpm` package (Fedora/RHEL), matching your architecture from section 2.2.
2. Install it:

   ```bash
   # Debian/Ubuntu
   sudo apt install ./code_*.deb

   # Fedora/RHEL
   sudo rpm -i code-*.rpm
   ```

3. The `code` command is added to your PATH automatically by these packages.

### First launch (all platforms)

VS Code opens on a Welcome tab. You will be asked to choose a colour theme. Pick whichever you find comfortable, and do not agonise over it — you can change it at any time with `Ctrl + K` then `Ctrl + T` (`Cmd + K` then `Cmd + T` on macOS).

You may be prompted to install extra tooling. Ignore all prompts for now. We install extensions deliberately in section 11.

> **A note on keyboard shortcuts.** From here on, this guide writes shortcuts as `Ctrl + X`. On macOS, read every `Ctrl` as `Cmd` unless stated otherwise — this is true for almost all VS Code shortcuts. Where the two platforms genuinely differ, both are given.
>
> **Want to go deeper?** The [VS Code Setup docs](https://code.visualstudio.com/docs/setup/setup-overview) cover platform-specific install details this guide simplifies. If interested, explore VS Code's built-in Settings Sync (Command Palette → "Settings Sync: Turn On") after this session, so your theme and extensions follow you to any machine you log into.

---

## 4. A tour of the VS Code window

Before installing anything else, learn the geography. The window has four regions, and this layout is identical on Windows, macOS, and Linux.

### 4.1 The Activity Bar (far left)

A vertical strip of icons. The five that matter now, from top to bottom:

| Icon | Name | Shortcut | Purpose |
|---|---|---|---|
| Two pages | **Explorer** | `Ctrl/Cmd + Shift + E` | The files in your current folder |
| Magnifying glass | **Search** | `Ctrl/Cmd + Shift + F` | Find text across every file |
| Branching lines | **Source Control** | `Ctrl/Cmd + Shift + G` | Git, covered in section 12 |
| Play with a bug | **Run and Debug** | `Ctrl/Cmd + Shift + D` | Step through code line by line |
| Four squares | **Extensions** | `Ctrl/Cmd + Shift + X` | Install add-ons |

### 4.2 The Side Bar

Whatever the Activity Bar icon you clicked wants to show you. Toggle it away with `Ctrl/Cmd + B` when you want more room.

### 4.3 The Editor

The large central area where files open, in tabs. You can split it into two or three columns by dragging a tab to the side, which is useful when comparing a script against its output.

### 4.4 The Panel (bottom)

Contains **Terminal**, **Problems**, **Output**, and **Debug Console**. Open and close it with ``Ctrl + ` `` (the backtick key, usually just under Escape on the left of the `1` key) on every platform, including macOS.

### 4.5 The Command Palette

The single most useful thing in VS Code. Press:

```
Ctrl/Cmd + Shift + P
```

A search box appears at the top. Everything VS Code can do is in here and can be found by typing part of its name. If you forget a menu location or a shortcut, open the Command Palette and describe what you want. Commit this shortcut to memory.

### 4.6 Opening a folder

VS Code works on **folders**, not loose files. Go to **File**, then **Open Folder** (macOS: **Open...**), and choose your `projects` folder from section 2.4. Everything in the Explorer panel is now relative to that folder, and the terminal will open inside it too.

> **Want to go deeper?** The [VS Code User Interface docs](https://code.visualstudio.com/docs/getstarted/userinterface) go further into every panel than this tour does. If interested, try the interactive [VS Code Tips and Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks) walkthrough after this session — most of it will already feel familiar.

---

## 5. The integrated terminal

### 5.1 What a terminal actually is

A terminal is a text conversation with your computer. You type an instruction, press Enter, and the computer replies in text. It feels primitive at first. It is in fact far more precise than clicking, because an instruction that works can be written down, shared, and repeated exactly — the same reason we write laboratory protocols rather than describing procedures from memory.

Everything in the rest of this guide happens in the terminal.

### 5.2 Opening it

Press ``Ctrl + ` ``, or go to **Terminal**, then **New Terminal**.

A panel opens at the bottom with a prompt waiting for you.

### 5.3 Which shell you are using

A **shell** is the program inside the terminal that actually reads and runs your commands. The default differs by operating system, and this matters because the commands are not always identical.

| OS | Default shell in VS Code | Notes |
|---|---|---|
| **Windows** | **PowerShell** | Use this one. All Windows commands in this guide assume PowerShell. |
| **macOS** | **zsh** | The macOS default since Catalina (2019). All macOS commands in this guide assume zsh. |
| **Linux** | **bash** | The near-universal default. All Linux commands in this guide assume bash. |

Confirm what you have. On Windows, the dropdown on the right of the terminal panel names the current shell; to set the default explicitly, open the Command Palette, type `Terminal: Select Default Profile`, and choose **PowerShell**. On macOS and Linux, type `echo $SHELL` and press Enter — it will print something like `/bin/zsh` or `/bin/bash`.

Avoid **Command Prompt (cmd)** on Windows — it is older and more limited than PowerShell. You may also encounter **Git Bash**, which arrives with Git and uses Linux-style commands; it is useful later but not our default.

> **Want to go deeper?** If you're curious why shells differ at all, [Microsoft's PowerShell overview](https://learn.microsoft.com/en-us/powershell/scripting/overview) and the [Zsh manual](https://zsh.sourceforge.io/Doc/) are worth a skim. Explore this after the session if the "which shell" question interests you — it isn't essential for the course itself.

### 5.4 Terminal habits worth forming now

These apply on every platform:

- The terminal always has a **current folder**. Commands act on that folder. Most beginner errors come from being in the wrong one.
- Press the **Up arrow** to bring back your previous command instead of retyping it.
- Press **Tab** to complete a half-typed file or folder name.
- Press `Ctrl + C` to interrupt a command that is stuck or running too long.
- Clear a cluttered screen: `cls` on PowerShell, `clear` on zsh/bash (or `Ctrl + L` on either).

> **Want to go deeper?** [The Missing Semester of Your CS Education (MIT)](https://missing.csail.mit.edu/2020/course-shell/) is a superb free course on the command line, aimed at exactly this stage. If interested, work through its first lecture after today's session — it goes well beyond what this guide needs but pays off for years.

---

## 6. Basic command line operations

Section 5 introduced the terminal. This section teaches you to actually use one — the small set of commands you will type dozens of times a day for the rest of the course, and that you will lean on again the moment we introduce Git in section 12.

### 6.1 The core idea: you are always "somewhere"

A terminal, like a file manager, has a **current working directory** — the folder your commands act on unless told otherwise. Losing track of where you are is the single most common source of beginner terminal errors ("file not found" when the file is right there — just not in the folder you think you're in).

### 6.2 Where am I? — `pwd`

```powershell
pwd
```

`pwd` stands for *print working directory*. It works identically in PowerShell, zsh, and bash, and prints the full path of your current folder.

### 6.3 What is in here? — `ls`

```powershell
ls
```

Lists the contents of the current folder. Identical on all three shells. Useful variants:

| Command | Effect |
|---|---|
| `ls` | List names |
| `ls -l` (zsh/bash) or `ls -Force` (PowerShell, for hidden files) | Long/detailed listing |
| `ls -a` (zsh/bash) | Include hidden files (those starting with `.`) |

### 6.4 Moving between folders — `cd`

```powershell
cd projects
```

`cd` means *change directory*. It takes you into a subfolder of where you currently are.

To move back up one level:

```powershell
cd ..
```

To jump straight to a specific location, use the full path:

```powershell
# Windows
cd C:\Users\YourName\projects

# macOS/Linux
cd ~/projects
```

To return instantly to your home folder from anywhere:

```powershell
cd ~
```

(On Windows PowerShell, `~` also works and resolves to your user folder.)

If a path contains spaces, wrap it in quotation marks: `cd "C:\My Folder"` or `cd "~/My Folder"`.

### 6.5 Making a new folder — `mkdir`

```powershell
mkdir my-first-project
```

Identical on all three shells. Combine it with `cd` to create and enter in one motion:

```powershell
mkdir my-first-project; cd my-first-project     # PowerShell
mkdir my-first-project && cd my-first-project   # zsh/bash
```

### 6.6 Creating, viewing, and removing files

| Task | PowerShell | zsh / bash |
|---|---|---|
| Create an empty file | `New-Item notes.txt` | `touch notes.txt` |
| Print a file's contents | `cat notes.txt` | `cat notes.txt` |
| Copy a file | `Copy-Item a.txt b.txt` | `cp a.txt b.txt` |
| Rename or move a file | `Move-Item a.txt b.txt` | `mv a.txt b.txt` |
| Delete a file | `Remove-Item notes.txt` | `rm notes.txt` |
| Delete a folder and everything in it | `Remove-Item -Recurse -Force folder` | `rm -rf folder` |

`cat` (short for *concatenate*) exists in PowerShell too and works the same way — it is one of the rare commands shared verbatim across all three shells.

> **A word of caution.** `rm -rf` and `Remove-Item -Recurse -Force` delete permanently — there is no recycle bin, and no undo. Read the command back to yourself before pressing Enter, especially the path. This is the single most common way beginners lose real work from the command line.

### 6.7 Opening the current folder in VS Code

```powershell
code .
```

The full stop means "this folder". This command works only if you enabled the `code` command during installation (section 3).

### 6.8 Checking whether a tool is installed

```powershell
python --version
git --version
uv --version
```

Right now, all three will fail with a message about the command not being recognised or not found. That is expected — we are about to fix it, one tool at a time.

### 6.9 Practice exercise

Before moving on, do this from scratch in your terminal without looking back at the sections above:

1. Confirm your current folder with the "where am I" command.
2. Create a folder called `terminal-practice` inside your `projects` folder.
3. Move into it.
4. Create a file called `hello.txt`.
5. Print its (empty) contents to the screen.
6. Create a subfolder called `drafts`, move into it, then go back up one level.
7. Delete the entire `terminal-practice` folder in one command.
8. Confirm it is gone by listing the contents of `projects`.

If you can do all eight steps without hesitation, you have the terminal fluency this course requires. If you got stuck, repeat it — this is muscle memory, not theory.

> **Want to go deeper?** [ExplainShell](https://explainshell.com/) breaks down any command you paste into it, flag by flag — useful whenever a tutorial shows you a command you don't fully understand. Explore a few of today's commands there if you're interested in what each flag actually does.

---

## 7. Installing uv

**uv** is a Python package and project manager written in Rust. It replaces a long list of older tools, and it does the job between ten and a hundred times faster than the traditional approach. Crucially for us, it also installs Python itself, so it is the only thing you need to install by hand, on every operating system.

### 7.1 Install

In your VS Code terminal, paste the command for your OS exactly and press Enter:

```powershell
# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

```bash
# macOS and Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Reading the Windows line from left to right: run PowerShell with script restrictions bypassed for this one command, download the installation script from astral.sh, and execute it. The macOS/Linux line downloads the same script with `curl` and pipes it straight into `sh` to run.

Installation takes a few seconds and prints a short summary when it finishes.

### 7.2 Restart the terminal

This step is not optional, on any platform. Close the terminal panel by clicking the bin icon, then open a fresh one with ``Ctrl + ` ``. A terminal only reads the system PATH when it starts, so an existing terminal will not find newly installed tools.

### 7.3 Verify

```powershell
uv --version
```

You should see something like `uv 0.9.x`. If you see an error instead, go to section 19.1.

### 7.4 Keeping uv current

```powershell
uv self update
```

Run this every few weeks, on any operating system.

> **Want to go deeper?** The [uv documentation](https://docs.astral.sh/uv/) is unusually readable for a tool's docs — the ["Why uv"](https://docs.astral.sh/uv/#highlights) page explains the design decisions behind it. If interested, read it after this session to understand what uv is actually doing under the hood rather than just trusting it.

---

## 8. Installing Python with uv

### 8.1 Install Python

```powershell
uv python install 3.12
```

Identical command on Windows, macOS, and Linux. uv downloads a self-contained Python 3.12 and stores it where uv can find it. This takes a minute or two on a reasonable connection.

We use 3.12 rather than the newest release because the scientific libraries you will rely on, such as NumPy, pandas, and scikit-learn, are thoroughly tested against it. Being one version behind is a feature, not a compromise.

### 8.2 Check what you now have

```powershell
uv python list
```

This lists the Python versions available to uv, marking those it has installed.

### 8.3 Why we are not downloading Python from python.org, or using the system Python

Installing Python from the website, or relying on the Python that already ships with macOS or Linux, works — and you will see both in many tutorials. Both also have a well-documented tendency to create difficulties for beginners:

- On **Windows**, multiple competing installations, a PATH that points at the wrong one, and the Microsoft Store stub that intercepts the `python` command and does nothing useful.
- On **macOS**, an old system Python (or none at all on recent versions) that Apple never intends for you to install packages into, causing confusing permission errors.
- On **Linux**, a system Python that your operating system itself depends on, where installing packages carelessly can break OS tools.

Letting uv manage Python versions sidesteps all of this, on every platform. If you already have a Python installed some other way, leave it alone — uv will not interfere with it.

### 8.4 A concept you must understand: the virtual environment

This is the single idea that separates people who fight their tools from people who do not, regardless of operating system.

Suppose your first project needs pandas version 1.5, and a project you start next year needs version 2.2. If all libraries live in one shared pile, installing the second version breaks the first project. In a field where reproducing a result months later is the whole point, this is unacceptable.

A **virtual environment** is a private box of libraries belonging to one project and nothing else. Each project gets its own. They never interfere with each other.

With uv, the environment lives in a folder called `.venv` inside your project, and uv creates and maintains it for you automatically. Section 9 walks through building one by hand so you understand exactly what is happening before uv starts doing it silently on your behalf.

> **Want to go deeper?** The [Python Packaging User Guide's section on virtual environments](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments) explains the general concept independent of any one tool. If interested, read it after this session to see how the idea predates uv and is common to nearly every language ecosystem, not just Python's.

---

## 9. Creating a virtual environment with uv

Section 8.4 described *what* a virtual environment is. Here you will build one yourself, by hand, before we let uv manage the process automatically for real projects in section 16. Doing it manually once removes the mystery.

### 9.1 Make a scratch folder

```powershell
cd ~/projects          # macOS/Linux — or cd C:\Users\YourName\projects on Windows
mkdir env-practice
cd env-practice
```

### 9.2 Create the environment

```powershell
uv venv
```

This single command, identical on all three operating systems, creates a `.venv` folder in the current directory containing a private copy of Python and a place to install libraries. Run `ls` (or `ls -a` on zsh/bash to see hidden folders) and you will see `.venv` sitting there.

### 9.3 Activate it

"Activating" an environment tells your terminal *for this session only* to use the Python and libraries inside `.venv` instead of any other Python on your machine.

```powershell
# Windows (PowerShell)
.venv\Scripts\activate
```

```bash
# macOS/Linux (zsh/bash)
source .venv/bin/activate
```

Your prompt changes to show `(env-practice)` (or similar) at the start of the line. That prefix is your constant reminder of which environment is active — get used to glancing at it.

### 9.4 Prove it worked

```powershell
python --version
```

This now succeeds — recall from section 6.8 that it failed before. It succeeds because the active environment's Python is now first in line to answer that command.

### 9.5 Install something into it

```powershell
uv pip install requests
```

This installs the `requests` library *only into this environment*. It does not exist anywhere else on your machine.

### 9.6 Deactivate

```powershell
deactivate
```

Identical command on every platform. Your prompt returns to normal, and `python --version` goes back to failing (or reporting a different, unrelated Python) — the environment's tools are no longer in front.

### 9.7 The shortcut you will actually use

In practice, you will rarely type `uv venv` and activate by hand, because `uv run` (introduced in section 16) creates and uses the right environment automatically, every time, without an activation step at all. Section 9.1–9.6 exists so that when `uv run` does this invisibly later, you know exactly what it is doing on your behalf, and you can diagnose it if something looks wrong.

### 9.8 Practice exercise

1. Delete the `env-practice` folder entirely (section 6.6).
2. Recreate it and build a fresh environment inside it.
3. Activate it, and confirm with `python --version` that it is active.
4. Install the `requests` library into it.
5. Deactivate.
6. Without activating again, try to guess — then check — whether `requests` is available in a brand-new folder with its own new environment. (It should not be. Explain to yourself why, in one sentence, before moving on.)

> **Want to go deeper?** [uv's own guide to projects and environments](https://docs.astral.sh/uv/concepts/projects/) covers exactly what section 9.7 hints at — how `uv run` automates what you just did by hand. If interested, read it after this session, before you rely on that automation for real in section 16.

---

## 10. Introduction to Markdown

### 10.1 What Markdown is, and why a data scientist needs it

**Markdown** is a way of formatting text — headings, bold, lists, links, images, tables, code — using plain, readable symbols instead of a word processor's menus. You have been reading it for the last eleven sections: this entire guide is a Markdown file.

You need it because it is the *lingua franca* of the tools around your code, not the code itself:

- Every **GitHub repository README** is written in it. It's the first thing anyone sees when they land on your project.
- Your **GitHub profile page** (the one at `github.com/your-username`) is a Markdown file too, and it functions as a public data science CV.
- **Jupyter Notebook** text cells (as opposed to code cells) are Markdown, which is how you write explanations, headings, and conclusions alongside your analysis.
- Discussion platforms your team will use — GitHub Issues, Pull Requests, Slack, and many others — all render Markdown.

In short: your code speaks Python, but you explain your code in Markdown. Both are core skills for this course.

### 10.2 The essentials

You need remarkably few symbols to be productive. Type the left-hand column exactly as shown, including blank lines around block elements (headings, lists, images), and it renders as the right-hand column describes.

**Headings** — a `#` at the start of a line, followed by a space:

```markdown
# Biggest heading (usually the document title — use only once)
## Section heading
### Subsection heading
```

**Emphasis:**

```markdown
*italic text* or _italic text_
**bold text**
***bold italic text***
`inline code`, for a filename, command, or variable name
```

**Lists:**

```markdown
- Unordered item
- Another item
  - An indented sub-item (two spaces before the dash)

1. Ordered item
2. Another ordered item
```

**Links and images:**

```markdown
[link text](https://example.com)
![alt text describing the image](path/to/image.png)
```

**Code blocks** — three backticks, optionally followed by a language name for colour highlighting:

````markdown
```python
def greet(name):
    return f"Hello, {name}!"
```
````

**Tables:**

```markdown
| Name  | Language | Level        |
|-------|----------|--------------|
| Amina | Python   | Beginner     |
| Kofi  | R        | Intermediate |
```

**Blockquotes**, for asides or warnings, exactly like the ones you have been reading throughout this guide:

```markdown
> This is a note worth pausing on.
```

**A horizontal rule**, to separate sections, is three or more hyphens on their own line:

```markdown
---
```

### 10.3 Where to write and preview it

- **In VS Code:** open any `.md` file, then press `Ctrl/Cmd + Shift + V` to open a live preview beside the raw text. The **Markdown All in One** extension (section 11) adds table formatting, list auto-continuation, and a table of contents generator.
- **On GitHub:** every `.md` file is rendered automatically when viewed in a repository — you never need to convert it to anything.
- **In a Jupyter Notebook:** change a cell's type to *Markdown* (in VS Code's notebook toolbar, or with the keyboard shortcut `M` when a cell is selected but not being edited), then run the cell with `Shift + Enter` to render it.

### 10.4 A worked example: a project README

Every project you build from section 16 onward should have a `README.md` explaining what it is. Here is a minimal, honest one for a first project:

```markdown
# Iris Species Analysis

A short exploratory analysis of the classic Iris flower dataset,
built while learning Python and pandas.

## What this does

- Loads the Iris dataset
- Summarises petal and sepal measurements by species
- Produces a scatter plot comparing sepal length to petal length

## How to run it

\`\`\`bash
uv run main.py
\`\`\`

## Author

Jane Student — Arewa DataScience Academy, 2026
```

Notice what this README does *not* do: it does not apologise, pad itself with filler, or promise more than the project delivers. A README's job is to let a stranger understand your project in under a minute.

### 10.5 Practice exercise

Create a file called `profile-draft.md` inside your `projects` folder and write a short personal data science profile using at least:

- one heading and one subheading,
- a bulleted list of three skills or tools you are learning,
- one link (to anything — your LinkedIn, a course page, a paper you liked),
- one code block containing a single line of Python, even something as simple as `print("hello, data science")`,
- one table with at least two columns and two rows.

Open it with `Ctrl/Cmd + Shift + V` in VS Code and check that everything renders the way you intended. This is close to a first draft of the profile you will eventually put on GitHub itself.

> **Want to go deeper?** The [GitHub Flavored Markdown Spec](https://github.github.com/gfm/) is the precise reference for the extra features GitHub adds on top of plain Markdown — task lists, tables, and more. If interested, skim it after this session; you don't need to memorise it, just know it exists for when you need an exact answer.

---

## 11. VS Code extensions for data science

### 11.1 Installing from the terminal

Extensions can be installed by clicking through the Extensions panel, but it is faster and far more reproducible to use the terminal. This command is identical on Windows, macOS, and Linux. Paste this block into your VS Code terminal:

```powershell
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension ms-toolsai.jupyter
code --install-extension ms-toolsai.datawrangler
code --install-extension charliermarsh.ruff
code --install-extension eamodio.gitlens
code --install-extension GitHub.vscode-pull-request-github
code --install-extension mechatroner.rainbow-csv
code --install-extension usernamehw.errorlens
code --install-extension yzhang.markdown-all-in-one
code --install-extension tamasfe.even-better-toml
```

Restart VS Code when the installations finish.

### 11.2 What each one does

**Essential**

| Extension | Identifier | What it gives you |
|---|---|---|
| Python | `ms-python.python` | Runs Python, detects environments, provides debugging |
| Pylance | `ms-python.vscode-pylance` | Autocompletion, function signatures, type checking |
| Jupyter | `ms-toolsai.jupyter` | Full notebook support inside VS Code |

**Strongly recommended**

| Extension | Identifier | What it gives you |
|---|---|---|
| Data Wrangler | `ms-toolsai.datawrangler` | Point-and-click inspection and cleaning of dataframes, with the equivalent pandas code generated for you |
| Ruff | `charliermarsh.ruff` | Extremely fast linting and formatting, so your code stays readable |
| GitLens | `eamodio.gitlens` | Shows who changed each line, and when |
| GitHub Pull Requests | `GitHub.vscode-pull-request-github` | Review and manage pull requests without leaving the editor |
| Rainbow CSV | `mechatroner.rainbow-csv` | Colours CSV columns so raw data files are readable |
| Error Lens | `usernamehw.errorlens` | Displays errors inline rather than hiding them in a panel |
| Markdown All in One | `yzhang.markdown-all-in-one` | Preview, table formatting, and shortcuts for the Markdown from section 10 |
| Even Better TOML | `tamasfe.even-better-toml` | Syntax support for `pyproject.toml`, which uv creates |

**A caution.** Extensions are tempting to collect. Each one consumes memory and startup time, and a heavily loaded VS Code becomes sluggish on a modest laptop. Install the list above, use it for a term, and add further extensions only when you have felt the specific need.

### 11.3 A few settings worth changing

Open the Command Palette, type `Preferences: Open User Settings (JSON)`, and add the following inside the outer braces. This file and its contents are identical across operating systems.

```json
{
  "editor.formatOnSave": true,
  "editor.rulers": [88],
  "files.autoSave": "afterDelay",
  "files.trimTrailingWhitespace": true,
  "notebook.output.textLineLimit": 50,
  "python.terminal.activateEnvInCurrentTerminal": true,
  "[python]": {
    "editor.defaultFormatter": "charliermarsh.ruff"
  }
}
```

These format your code on every save, mark the conventional line length, save your work automatically, and keep enormous notebook outputs from swamping the screen.

> **Want to go deeper?** [Ruff's documentation](https://docs.astral.sh/ruff/) explains the specific style rules it enforces, and the [Data Wrangler docs](https://code.visualstudio.com/docs/datascience/data-wrangler) go further into its cleaning features than this list does. If interested, explore both after this session, once you have real data to try them on.

---

## 12. Installing Git

### 12.1 What Git is, and why it is not optional

Git records the state of your project every time you ask it to. Every recorded state can be returned to. This gives you three things:

- **Undo without limit.** If your analysis worked on Tuesday and is broken on Thursday, you can see precisely what changed, and go back.
- **An end to file name chaos.** No more `analysis_final.py`, `analysis_final_v2.py`, `analysis_final_REALLY_FINAL.py`. There is one file, with a complete history behind it.
- **Collaboration.** Two people can work on the same project without overwriting each other's work.

Git is a laboratory notebook for code, and the argument for keeping one is exactly the same, on every operating system.

### 12.2 Download and install

**Windows:** go to **https://git-scm.com/download/win** and choose the **64-bit Git for Windows Setup** installer.

The installer asks many questions. The defaults are sensible, but three screens deserve attention:

1. **Choosing the default editor used by Git.** Select **Use Visual Studio Code as Git's default editor** from the dropdown. The default is Vim, which is a legendary source of panic for beginners who cannot work out how to exit it.
2. **Adjusting the name of the initial branch.** Select **Override the default branch name for new repositories** and leave it as `main`. This matches GitHub.
3. **Adjusting your PATH environment.** Keep the recommended middle option, *Git from the command line and also from 3rd-party software*.

Accept the defaults on every other screen and click through to **Install**.

**macOS:** Git is often already present. Check first by running `git --version` in a fresh terminal — if it is missing, macOS will offer to install the **Xcode Command Line Tools**, which include Git. Accept that prompt. Alternatively, install a newer version with **Homebrew** (`brew install git`) if you already use Homebrew; if you don't yet, don't install it just for this — the Command Line Tools version is fine for this course.

**Linux:**

```bash
# Debian/Ubuntu
sudo apt update && sudo apt install git

# Fedora
sudo dnf install git
```

### 12.3 Restart the terminal and verify

Close and reopen the terminal in VS Code, then run:

```powershell
git --version
```

You should see something like `git version 2.4x.x`.

### 12.4 Tell Git who you are

Git labels every change with an author. Set this once, and it applies to all future projects on this machine. Use the same email address that you will use for GitHub. This step and everything below it is identical across Windows, macOS, and Linux.

```powershell
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"
```

Set two further defaults that avoid common annoyances:

```powershell
git config --global init.defaultBranch main
git config --global core.autocrlf true
```

> `core.autocrlf true` is the recommended setting on **Windows**. On **macOS and Linux**, use `git config --global core.autocrlf input` instead — it handles line-ending differences correctly for your platform.

Confirm your settings:

```powershell
git config --global --list
```

> **Want to go deeper?** The free online book [Pro Git](https://git-scm.com/book/en/v2), especially chapter 1–2, explains what a commit actually is under the hood — more than this guide needs, but it's the standard reference everyone eventually reads. Explore its first two chapters after today's session if you're interested in why Git works the way it does.

---

## 13. Setting up GitHub

### 13.1 Git and GitHub are different things

A frequent point of confusion. **Git** is the program on your computer that tracks changes. **GitHub** is a website that stores copies of Git projects online. Git works perfectly well without GitHub. GitHub without Git would be meaningless.

The relationship is roughly that of a laboratory notebook to the departmental archive.

### 13.2 Create your account

Go to **https://github.com/signup** and register.

Two pieces of advice on the username, because it is difficult to change later and it will appear on your CV:

- Use something professional and close to your real name. `amina-yusuf` or `ayusuf-data` are good. `coolguy2005` is not.
- Keep it short and easy to type.

Verify your email address when the confirmation arrives.

### 13.3 Enable two-factor authentication

GitHub requires this for all accounts. Go to **Settings**, then **Password and authentication**, and follow the prompts. Use an authenticator app on your phone. Save the recovery codes somewhere safe, because if you lose your phone without them, you lose the account.

### 13.4 Apply for the Student Developer Pack

If you have a university email address, go to **https://education.github.com/pack** and apply. It is free, and it includes GitHub Copilot and a long list of other services.

### 13.5 Connecting VS Code to GitHub

On **Windows**, you do not need to configure SSH keys or personal access tokens by hand — Git for Windows installs **Git Credential Manager**, which handles authentication through your browser. On **macOS and Linux**, Git itself will prompt you to authenticate through the browser the first time you push, using the same credential-helper mechanism (macOS uses the built-in Keychain; most Linux setups will open a browser window via Git's credential manager as well).

To sign VS Code in, click the **Accounts** icon at the bottom of the Activity Bar, choose **Sign in with GitHub**, and complete the process in the browser window that opens. This enables settings sync and smooths every later interaction with GitHub.

The first time you push code (section 17), a browser window will open asking you to authorise. Approve it once, and your machine remembers the credentials.

> **Want to go deeper?** [GitHub Skills](https://skills.github.com/) offers free, interactive, hands-on courses directly on GitHub itself. If interested, try the "Introduction to GitHub" course after this session — it reinforces everything in this section with guided practice.

---

## 14. GitHub in VS Code: managing GitHub files

Section 13 created your GitHub account. This section teaches you the actual daily workflow — cloning, forking, staging, committing, branching, pushing, pulling, and opening a pull request — entirely from inside VS Code, with the terminal equivalent alongside every step so you understand what the interface is doing on your behalf. This is the single most important workflow in the course after Python itself: almost every collaborative data science project, published dataset, and open-source library you touch from here on is managed exactly this way.

### 14.1 Three ways a project ends up on your machine

Beginners often blur these together. They are different operations, used in different situations.

| Operation | What it does | When you use it |
|---|---|---|
| **`git init`** | Turns an *existing local folder* into a Git repository, from scratch | Starting a brand-new project of your own (this is what `uv init` did for you in section 16) |
| **`git clone`** | Downloads a *copy of a repository you already have write access to* | Working on your own repository, or one your team added you to |
| **Fork, then clone** | Makes *your own copy of someone else's repository* on GitHub, then downloads that copy | Contributing to a project you do not have write access to — including this course's own repository |

The rest of this section walks through the clone workflow first, because it is simpler, then the fork workflow, which is what you will use to submit coursework or contribute to open-source projects.

### 14.2 Cloning a repository

**From VS Code:**

1. Open the Command Palette (`Ctrl/Cmd + Shift + P`), type `Git: Clone`, and press Enter.
2. Paste the repository's URL — copied from the green **Code** button on its GitHub page — and press Enter.
3. Choose a folder to clone into (your `projects` folder is a sensible default).
4. When VS Code asks whether to open the cloned repository, choose **Open**.

**From the terminal**, the equivalent is:

```bash
git clone https://github.com/some-org/some-repo.git
cd some-repo
code .
```

Both routes produce an identical result: a full copy of the repository, including its entire history, connected to GitHub as a **remote** named `origin`.

### 14.3 Forking a repository

A **fork** is your own personal copy of someone else's repository, living under your own GitHub account. You get full write access to your fork even though you have none on the original. This is how open-source contribution — and how you will submit work back to a shared course repository — actually works.

1. On GitHub, open the repository you want to contribute to and click **Fork** (top right).
2. GitHub creates `your-username/repo-name` under your account. This is your fork.
3. Clone **your fork**, not the original, using the steps in section 14.2.

You now have two remotes to keep straight:

| Remote name | Points to | Purpose |
|---|---|---|
| `origin` | Your fork (`your-username/repo-name`) | Where you push your own commits |
| `upstream` | The original repository | Where you pull updates from, so your fork does not go stale |

Add the second remote once, from the terminal (VS Code has no menu for this step):

```bash
git remote add upstream https://github.com/original-owner/repo-name.git
git remote -v
```

`git remote -v` lists both remotes and confirms the URLs are correct.

To bring your fork up to date with the original repository later:

```bash
git fetch upstream
git merge upstream/main
```

### 14.4 The Source Control panel, properly explained

Open it with `Ctrl/Cmd + Shift + G`, or click the branching-lines icon in the Activity Bar (section 4.1). Four things live here, and matching each to its terminal command removes the mystery:

| In the Source Control panel | Terminal equivalent | Meaning |
|---|---|---|
| A file listed under **Changes** | shown by `git status` | Modified since the last commit, not yet staged |
| Clicking **+** next to a file (staging it) | `git add filename` | Marked to be included in the next commit |
| Typing a message and clicking the **✓ Commit** button | `git commit -m "message"` | Permanently records the staged changes |
| Clicking **Sync Changes** (or the cloud icon with numbers) | `git push` then `git pull` | Uploads your commits, then downloads anyone else's |

The numbers on the Sync Changes button matter: an upward arrow with a number shows commits you have not yet pushed; a downward arrow shows commits on GitHub you do not yet have locally.

### 14.5 The daily cycle, side by side

| Step | VS Code UI | Terminal |
|---|---|---|
| See what changed | Source Control panel, **Changes** list | `git status` |
| Review a specific change | Click the filename to open a diff view | `git diff filename` |
| Stage everything | Hover **Changes**, click **+** | `git add .` |
| Commit | Type a message, click **✓** | `git commit -m "message"` |
| Push | Click **Sync Changes** | `git push` |
| Pull | Click **Sync Changes** | `git pull` |

Neither route is "more correct." The UI is faster for reviewing diffs visually; the terminal is faster once the commands are muscle memory, and it is what you will read in almost every tutorial and Stack Overflow answer. Learn both — you will use the UI most days and the terminal when something needs a command the UI does not expose, such as the `remote add` step in section 14.3.

### 14.6 Working with branches

A **branch** is an independent line of work — a way to try a change without touching the working version until you are ready. Every repository has a default branch, almost always called `main`.

**Creating and switching branches in VS Code:**

1. Click the branch name shown in the bottom-left corner of the status bar (it reads `main` by default).
2. Choose **Create new branch...**, and give it a short, descriptive name — `add-loop-examples`, not `patch1`.
3. VS Code switches you onto the new branch immediately. The status bar updates to show its name.

The terminal equivalent:

```bash
git checkout -b add-loop-examples
```

Make your changes, stage, and commit as usual (section 14.5) — everything you commit now belongs to this branch, not to `main`, until you merge it. When you push a brand-new branch for the first time, VS Code's Source Control panel offers a **Publish Branch** button — the terminal equivalent is:

```bash
git push -u origin add-loop-examples
```

Switch back to `main` at any time by clicking the branch name in the status bar again and selecting `main`.

> **Why bother with branches for a solo learning project?** Because the habit is the point. The moment you work with anyone else — a group project, a research supervisor, an open-source maintainer — commits land on branches first and `main` stays stable and working at all times. Building the habit now, while the stakes are low, means it costs you nothing later.

### 14.7 Handling merge conflicts

A **merge conflict** happens when Git cannot automatically combine two sets of changes to the same lines of the same file — most often because you and a collaborator (or you and your past self, on two different branches) edited the same place differently. This is not an error to fear; it is Git correctly refusing to guess.

When a conflict occurs, VS Code marks the affected file in the Source Control panel and opens it with a built-in **merge editor** showing:

- **Current Change** — what your branch has
- **Incoming Change** — what you are merging in
- Buttons to **Accept Current**, **Accept Incoming**, **Accept Both**, or edit the result by hand

Work through each conflicted section, choose the correct outcome (or write it yourself, combining both), save the file, then stage and commit as normal — the commit itself records the conflict as resolved. If you would rather see the raw markers VS Code is interpreting, they look like this in the file:

```
<<<<<<< HEAD
your version of the line
=======
their version of the line
>>>>>>> incoming-branch-name
```

Delete the marker lines (`<<<<<<<`, `=======`, `>>>>>>>`) and keep only the content you actually want, on every conflict, before committing.

### 14.8 Opening and reviewing a pull request without leaving VS Code

A **pull request** (PR) is a request to merge your branch (or your fork) into someone else's repository, with a place for discussion and review before it happens. This is how you submit coursework to a shared class repository, and how essentially all open-source contribution works.

With the **GitHub Pull Requests** extension installed (section 11), from the fork-and-branch state you built in sections 14.3 and 14.6:

1. Push your branch (section 14.6).
2. Open the **GitHub Pull Requests** icon in the Activity Bar.
3. Click **Create Pull Request**, confirm the base repository/branch (usually the original repository's `main`) and your branch, write a short description of what changed and why, and submit.
4. Reviewers can comment directly on your lines of code; you will see their comments in the same panel and can reply or push follow-up commits to the same branch, which update the PR automatically.

The browser works identically if you prefer it — click **Compare & pull request** on your fork's GitHub page after pushing a branch — but doing it in VS Code means you never lose your place in the editor.

### 14.9 Practice exercise

1. Fork any small public repository (ask your instructor for one, or use this course's repository).
2. Clone your fork (section 14.2), and add the original as `upstream` (section 14.3).
3. Create a new branch with a descriptive name (section 14.6).
4. Make one small, genuine improvement — fix a typo, clarify a sentence, add a missing example.
5. Stage, commit with a clear message, and push the branch.
6. Open a pull request back to the original repository (section 14.8), describing what you changed and why.
7. Whether or not it is merged, you have now completed the exact workflow used to contribute to real open-source projects.

> **Want to go deeper?** [GitHub's own docs on collaborating with pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests) cover review etiquette and conventions this section only touches on. If interested, explore a real open-source project's "good first issue" label after this session — [goodfirstissue.dev](https://goodfirstissue.dev/) curates them across languages.

---

## 15. VS Code and AI

### 15.1 Why this section exists

You are learning Python at a moment when the editor itself can write, explain, and debug code alongside you. That is a genuine change to how programming is practised, and pretending otherwise would leave you unprepared for how research and industry teams already work. This section is not about replacing sections 1–13 — you still need the fundamentals in your own head, because you are the one who has to judge whether an AI's suggestion is correct, and an AI that writes code you cannot read is not actually saving you time. Think of it the way a calculator relates to arithmetic: enormously useful once you understand what it is doing, and a trap if you never learned to do it yourself.

### 15.2 What you can do with AI inside VS Code today

| Capability | What it looks like in practice |
|---|---|
| **Inline code completion** | As you type, grey "ghost text" suggests the rest of the line or the next few lines. Press `Tab` to accept, or keep typing to ignore it. |
| **Chat, side by side with your code** | A chat panel that can see your open files and answer questions such as "why does this loop never terminate?" or "what does `.groupby()` do here?" |
| **Explain a block of code** | Select a confusing block, right-click, and ask for a plain-language explanation — genuinely useful when reading someone else's script, or your own from three months ago. |
| **Explain an error message** | Paste a traceback into chat and ask what it means and where to look. This is often faster than searching, and it teaches you to read tracebacks yourself over time. |
| **Generate a first draft** | Describe a function in a comment or a chat prompt ("a function that removes rows with missing values and returns a summary of how many were dropped") and get a starting implementation to read, test, and correct. |
| **Agent / multi-file edit mode** | Newer tools can plan and carry out a change across several files at once — for example, "add a docstring to every function in this file" — showing you a diff to review before anything is applied. |
| **Generate tests and docstrings** | Point an assistant at a function and ask for test cases or a docstring, then check both by hand. |
| **Terminal help** | Ask "what is the command to undo my last Git commit without losing the changes?" instead of guessing at flags. |

### 15.3 Recommended tools and extensions

| Tool | Type | Notes |
|---|---|---|
| **GitHub Copilot** (`GitHub.copilot` + `GitHub.copilot-chat`) | Inline completion + chat | The most widely used option, built directly into VS Code. **Free for verified students** through the GitHub Student Developer Pack (section 13.4) — apply for that before paying for anything. |
| **Claude Code** | Terminal-native AI agent, with a VS Code companion extension | Strong at reasoning through multi-step tasks, explaining unfamiliar codebases, and larger refactors. Ask your instructor about classroom/education access before purchasing an individual plan. |
| **Continue** (`Continue.continue`) | Open-source chat + completion | Lets you plug in different AI models, including free or lower-cost ones, if you want more control than a single vendor's extension gives you. |
| **Error Lens** (`usernamehw.errorlens`, from section 11) | Not AI, but pairs well with it | Surfaces the exact error inline, which is exactly the text you will paste into an AI chat when you need help. |

Install whichever chat/completion extension you choose the same way as section 11.1:

```powershell
code --install-extension GitHub.copilot
code --install-extension GitHub.copilot-chat
```

You do not need more than one completion tool running at a time — two suggesting ghost text simultaneously is confusing rather than helpful. Pick one for this course.

### 15.4 Using AI well as a beginner: four rules

1. **Never run or submit code you cannot explain line by line.** If an assistant writes a function and you cannot say what each line does, you have not learned it — ask "explain this line by line" before moving on, every time, until it becomes automatic.
2. **Use it to get unstuck, not to skip the struggle entirely.** The productive moment in learning to program is usually the ten minutes before you understand something. Asking immediately removes that moment; asking after you have tried removes only the frustration.
3. **Verify, don't trust.** AI assistants confidently produce incorrect code, invent library functions that do not exist, and misremember syntax. Run the code. Check the output against what you expect. This habit matters more in data science than almost anywhere else, because a wrong analysis can look identical to a right one until someone checks the numbers.
4. **Check your course and institution's policy before using AI on graded work.** Using an assistant to understand a lab is usually encouraged; using one to produce a submission you present as entirely your own may not be, and the line between the two is a matter of institutional policy, not personal judgement. When in doubt, ask your instructor.

### 15.5 Practice exercise

1. Install a chat/completion extension from section 15.3.
2. Open the `main.py` you will write in section 16, or any short script you already have.
3. Deliberately introduce a bug — for example, change `==` to `=` inside a condition, or misspell a variable name.
4. Run the script, copy the exact error message, and ask the AI chat what it means and how to fix it, without asking it to just "fix my code."
5. Fix the bug yourself using the explanation, then, in one sentence, write down what caused the error in your own words.

If you can complete step 5 without looking at the AI's fix, you used the tool correctly.

> **Want to go deeper?** [GitHub's guide to responsible AI-assisted development](https://docs.github.com/en/copilot/responsible-use-of-github-copilot-features) and Anthropic's [Claude Code documentation](https://docs.claude.com/en/docs/claude-code) both go further into using these tools well. If interested, explore one of them after this session, and check your own institution's AI-use policy while you're at it — section 15.4's rule 4 applies immediately once graded work starts.

---

## 16. Your first project, end to end

Everything is installed. We now build a small project to confirm that the pieces work together. Every command below is identical on Windows, macOS, and Linux unless marked otherwise.

### 16.1 Create the project

In the terminal:

```powershell
cd ~/projects          # or cd C:\Users\YourName\projects on Windows
uv init iris-analysis
cd iris-analysis
code .
```

`uv init` creates a project folder containing:

| File | Purpose |
|---|---|
| `pyproject.toml` | The project description, including its dependencies |
| `main.py` | A starter script |
| `README.md` | Documentation for human readers — this is the Markdown file from section 10 |
| `.python-version` | Records which Python version this project uses |
| `.gitignore` | Lists files Git should ignore |

### 16.2 Add libraries

```powershell
uv add pandas matplotlib seaborn scikit-learn jupyter ipykernel
```

Watch the terminal. uv creates the `.venv` folder — the same kind of environment you built by hand in section 9 — resolves the dependency graph, and installs everything, typically in a few seconds. The same operation with older tools routinely took several minutes.

Note that you did not activate anything and did not run `pip`. `uv add` handled the environment for you, exactly as promised in section 9.7.

### 16.3 Write a script

Open `main.py` in the editor and replace its contents with:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load a classic dataset that ships with seaborn
iris = sns.load_dataset("iris")

print("Rows and columns:", iris.shape)
print()
print(iris.head())
print()
print(iris.groupby("species")["petal_length"].describe())

# Draw and save a figure
sns.scatterplot(data=iris, x="sepal_length", y="petal_length", hue="species")
plt.title("Sepal length against petal length")
plt.savefig("iris_scatter.png", dpi=150, bbox_inches="tight")
print("\nFigure saved as iris_scatter.png")
```

### 16.4 Run it

```powershell
uv run main.py
```

`uv run` executes the script inside the project environment. You never have to remember to activate anything.

You should see the summary tables printed, and a new file `iris_scatter.png` in the Explorer panel. Click it to view the figure.

### 16.5 Work in a notebook

Scripts are right for pipelines you will run repeatedly. Notebooks are right for exploration, where you want to see the result of each step before deciding on the next, mixing code cells with the Markdown text cells from section 10.

1. Create a new file called `exploration.ipynb`. In the Explorer panel, click the new file icon and type the name including the extension.
2. The notebook interface opens.
3. Click **Select Kernel** at the top right.
4. Choose **Python Environments**, then the entry showing `.venv` for your project. This is the environment uv built, and choosing correctly here is the step most people get wrong.
5. Type into the first cell:

```python
import seaborn as sns

iris = sns.load_dataset("iris")
iris.head()
```

6. Run the cell with `Shift + Enter`.

The dataframe appears below the cell. In the output, look for the **Open in Data Wrangler** button, which gives you a spreadsheet-style view for filtering, sorting, and cleaning, while writing the corresponding pandas code for you.

7. Add a new cell above it, change its type to **Markdown**, and write a one-line heading describing what the notebook does — put section 10's skills to immediate use.

### 16.6 Commands you will use every day

| Command | Effect |
|---|---|
| `uv add package-name` | Add a library to the project |
| `uv remove package-name` | Remove a library |
| `uv run script.py` | Run a script in the project environment |
| `uv sync` | Rebuild the environment to match `pyproject.toml` |
| `uv lock` | Update the lock file that pins exact versions |
| `uvx tool-name` | Run a command line tool without installing it permanently |

> **Want to go deeper?** The [seaborn example gallery](https://seaborn.pydata.org/examples/index.html) and the [pandas user guide](https://pandas.pydata.org/docs/user_guide/) show far more than the single scatter plot built here. If interested, pick one seaborn example after this session and adapt it to the iris dataset you already have loaded.

---

## 17. Pushing your project to GitHub

### 17.1 Initialise version control

Still inside the project folder:

```powershell
git init
git add .
git commit -m "Initial commit: iris analysis setup"
```

Reading these three lines: start tracking this folder, stage everything currently in it, and record a permanent snapshot with a short description.

A commit message should say what changed and why. `Add species comparison plot` is useful. `update` and `stuff` are not, and your future self will resent them.

### 17.2 Check what Git is ignoring

Open the `.gitignore` file that `uv init` created. It already excludes `.venv` and Python's cache folders. This is correct, because environments are rebuilt from `pyproject.toml` rather than shared.

Add a few more lines yourself:

```gitignore
# Data files, which are often large and sometimes confidential
data/raw/
*.csv
*.xlsx

# Credentials, which must never be committed
.env

# macOS clutter (harmless to include even if you are on Windows/Linux)
.DS_Store
```

> **A rule with no exceptions.** Never commit passwords, API keys, or personal data. Once something reaches GitHub it is in the history permanently, and deleting the file afterwards does not remove it. Treat this with the seriousness you would give to publishing patient records.

### 17.3 Create the repository on GitHub

The easiest route is through VS Code itself, identically on every operating system:

1. Open the **Source Control** panel (`Ctrl/Cmd + Shift + G`).
2. Click **Publish Branch**.
3. Choose **Publish to GitHub public repository** or the private option.
4. Authorise in the browser window if prompted.

VS Code creates the repository, connects it, and uploads your work.

The equivalent from the terminal, if you prefer to see the mechanics:

```powershell
git remote add origin https://github.com/your-username/iris-analysis.git
git branch -M main
git push -u origin main
```

### 17.4 The daily rhythm

After the first push, your working cycle is:

```powershell
git add .
git commit -m "Describe what you changed"
git push
```

Or use the Source Control panel: type a message in the box, click the tick to commit, then click **Sync Changes**.

Commit whenever you finish a coherent piece of work, which in practice means several times a day. Small, frequent commits are easy to review and easy to undo. One enormous commit at the end of the week is neither.

### 17.5 Practice exercise

Update your `README.md` (section 10's skills again) to properly describe the Iris project — what it does, how to run it, and what the figure shows — then commit and push that single change with a clear message. This is the smallest possible complete example of the daily rhythm you will repeat for the rest of the course.

> **Want to go deeper?** [GitHub's guide to writing a great README](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes) has more structure than section 10.4's minimal example. If interested, explore a few well-known open-source projects' READMEs after this session and notice what they choose to include and leave out.

---

## 18. Optional: conda and when you might need it

You will meet conda in scientific computing, and you should know where it fits, regardless of operating system.

Use **uv** for essentially everything on this course. It is faster, lighter, and produces cleaner projects.

Consider **conda** when:

- A package you need has heavy non-Python dependencies that are difficult to install with pip, for example some bioinformatics and cheminformatics tools such as RDKit, or older geospatial stacks.
- Your laboratory or supervisor already standardises on conda and you must match their environment.
- You are following a bioinformatics workflow that assumes Bioconda.

If you need it, install **Miniconda**, not the full Anaconda distribution, because Anaconda installs several gigabytes of packages you will never use.

Download from **https://www.anaconda.com/download/success** and choose the Miniconda installer matching your operating system and chip. After installing, run once:

```powershell
conda init powershell   # Windows
```

```bash
conda init zsh          # macOS
conda init bash         # Linux
```

Restart the terminal, then create environments as needed — identical commands on every platform:

```bash
conda create -n bioproject python=3.12
conda activate bioproject
conda install -c conda-forge rdkit
```

> **Keep them apart.** Do not use uv and conda in the same project folder. Each expects to control the environment, and mixing them produces failures that are extremely difficult to diagnose. One project, one manager.
>
> **Want to go deeper?** The [conda-forge documentation](https://conda-forge.org/docs/) explains the community package channel referenced above, and Bioconda's [getting-started guide](https://bioconda.github.io/) is the standard entry point if you end up in a bioinformatics lab. Explore these only if your future work actually needs them — this section is optional for a reason.

---

## 19. Troubleshooting

### 19.1 "uv is not recognised" / "command not found: uv"

Almost always because the terminal was open before uv was installed.

1. Close the terminal panel completely using the bin icon.
2. Open a new one with ``Ctrl + ` ``.
3. If it still fails, close VS Code entirely and reopen it.
4. If it still fails, restart your computer.

### 19.2 Typing `python` opens the Microsoft Store (Windows only)

Windows ships a placeholder that hijacks the `python` command. Disable it.

Open **Settings**, then **Apps**, then **Advanced app settings**, then **App execution aliases**. Turn **off** every entry named `python.exe` and `python3.exe`.

Note that with uv you rarely type `python` directly. Use `uv run` instead.

### 19.3 "Running scripts is disabled on this system" (Windows only)

PowerShell blocks scripts by default. Run this once:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

This applies to your user account only and does not require administrator rights. Answer `Y` when prompted.

### 19.4 `code .` does nothing (any platform)

The PATH entry, or the shell command, is missing. Open VS Code, press `Ctrl/Cmd + Shift + P`, type `Shell Command: Install 'code' command in PATH`, and run it. Then restart the terminal.

### 19.5 "Permission denied" when running a downloaded script (macOS/Linux)

macOS and Linux enforce file permissions more strictly than Windows. If a script refuses to run directly, either use the `sh`/`bash` prefix shown in section 7.1 (which sidesteps the permission entirely), or mark it executable first: `chmod +x script.sh`.

### 19.6 macOS says the app "cannot be opened because the developer cannot be verified"

Right-click (or Control-click) the app in Finder, choose **Open**, then confirm **Open** in the dialogue that appears. This is a one-time step per app and is expected behaviour for software downloaded outside the App Store.

### 19.7 The notebook cannot find a library you installed

You have selected the wrong kernel. Click the kernel name at the top right of the notebook, choose **Select Another Kernel**, then **Python Environments**, and pick the one showing `.venv` inside your project folder. Almost every "but I installed it" problem is this, on every operating system.

### 19.8 Downloads fail or time out

Frequently a network issue rather than a tool issue.

- Retry, because transient failures are common.
- If you are on a university or corporate network, a proxy may be blocking the connection. Try a mobile hotspot to confirm.
- If a download stalls repeatedly, run the command again. uv caches what it already fetched and resumes rather than starting over.

### 19.9 Git asks for a password and rejects it

GitHub stopped accepting account passwords for Git operations. Let Git's credential helper handle it: when a browser window opens, sign in there. On Windows, if credentials have become stale, open **Credential Manager** from the Start menu, go to **Windows Credentials**, and delete any entry mentioning `github.com`; the next push will prompt you afresh. On macOS, do the same via **Keychain Access**, searching for `github.com`.

### 19.10 Filename or path too long (Windows)

Windows historically limited paths to 260 characters. Shorten your project path, which is another reason to work in `C:\Users\YourName\projects` rather than deep inside Documents. You can also run, in a terminal opened as administrator:

```powershell
git config --system core.longpaths true
```

### 19.11 Everything is broken and you cannot work out why

Delete the environment and rebuild it. This is safe, because the environment is disposable by design, on every operating system.

```powershell
Remove-Item -Recurse -Force .venv   # Windows
```

```bash
rm -rf .venv                        # macOS/Linux
```

```powershell
uv sync
```

If the problem persists, note the exact error message, including the final few lines of output, and bring it to the class channel. "It does not work" cannot be diagnosed. The error text usually can be.

> **Want to go deeper?** Learning to search an error message well is its own skill — see [this classic guide to reading a Python traceback](https://realpython.com/python-traceback/). If interested, practice on a deliberately broken script after this session, before you need the skill under real time pressure.

---

## 20. Command reference card

### VS Code shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + Shift + P` | Command Palette, the answer to most questions |
| ``Ctrl + ` `` | Toggle the terminal (same key on macOS) |
| `Ctrl/Cmd + B` | Toggle the side bar |
| `Ctrl/Cmd + P` | Jump to a file by name |
| `Ctrl/Cmd + S` | Save |
| `Ctrl/Cmd + /` | Comment or uncomment the selected lines |
| `Ctrl/Cmd + Shift + V` | Preview a Markdown file |
| `Shift + Enter` | Run the current notebook cell |
| `Ctrl/Cmd + Shift + X` | Extensions |
| `Ctrl/Cmd + Shift + G` | Source Control |

### Terminal — cross-platform equivalents

| Task | PowerShell (Windows) | zsh / bash (macOS/Linux) |
|---|---|---|
| Where am I | `pwd` | `pwd` |
| List contents | `ls` | `ls` |
| Enter a folder | `cd folder-name` | `cd folder-name` |
| Go up one level | `cd ..` | `cd ..` |
| Go to home folder | `cd ~` | `cd ~` |
| Create a folder | `mkdir name` | `mkdir name` |
| Create an empty file | `New-Item name.txt` | `touch name.txt` |
| Print a file | `cat name.txt` | `cat name.txt` |
| Delete a file | `Remove-Item name.txt` | `rm name.txt` |
| Delete a folder | `Remove-Item -Recurse -Force name` | `rm -rf name` |
| Clear the screen | `cls` | `clear` |
| Open folder in VS Code | `code .` | `code .` |

### uv (identical across all platforms)

| Command | Action |
|---|---|
| `uv init project-name` | Create a new project |
| `uv add package` | Install a library into the project |
| `uv remove package` | Uninstall a library |
| `uv run script.py` | Run a script in the project environment |
| `uv sync` | Rebuild the environment from the project files |
| `uv venv` | Create a standalone virtual environment |
| `uv pip install package` | Install into an already-activated environment |
| `uv python install 3.12` | Install a Python version |
| `uv python list` | List available Python versions |
| `uv self update` | Update uv itself |
| `uvx tool` | Run a tool without installing it |

### Git (identical across all platforms)

| Command | Action |
|---|---|
| `git status` | What has changed, and what is staged |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Record a snapshot |
| `git push` | Upload to GitHub |
| `git pull` | Download changes from GitHub |
| `git log --oneline` | Show the history compactly |
| `git clone url` | Copy a repository from GitHub to your machine |

### Markdown

| Syntax | Renders as |
|---|---|
| `# Heading` | Heading |
| `**bold**` / `*italic*` | **bold** / *italic* |
| `` `code` `` | `code` |
| `- item` | Bulleted list |
| `1. item` | Numbered list |
| `[text](url)` | A link |
| `![alt](path)` | An image |
| ` ```lang ` … ` ``` ` | A fenced, highlighted code block |
| `\| a \| b \|` rows | A table |
| `> text` | A blockquote |

> **Want to go deeper?** Print or bookmark this card — it's meant as a quick lookup, not a read-through. If you're interested in more shortcuts, VS Code's Command Palette entry `Preferences: Open Keyboard Shortcuts` lists every one it has, searchable by name.

---

## 21. Setup checklist

Confirm each item before the next session. Where a check is a command, run it in a fresh VS Code terminal.

- [ ] Operating system and chip/architecture identified (section 2.1–2.2)
- [ ] A `projects` folder exists outside any cloud-synced location
- [ ] VS Code installed, with the `code` command working in the terminal
- [ ] `code .` opens the current folder
- [ ] Terminal opens with ``Ctrl + ` `` and you know which shell it is running
- [ ] You can navigate folders, list contents, and create/delete a file and folder without hesitation (section 6.9)
- [ ] `uv --version` returns a version number
- [ ] `uv python list` shows Python 3.12 installed
- [ ] You have created, activated, used, and deactivated a virtual environment by hand at least once (section 9.8)
- [ ] `git --version` returns a version number
- [ ] `git config --global --list` shows your name and email
- [ ] GitHub account created, with two-factor authentication enabled
- [ ] VS Code signed in to GitHub
- [ ] You can clone a repository, and you can fork one and add it as `upstream` (section 14.2–14.3)
- [ ] You have created a branch, made a commit, and pushed it, either through the Source Control panel or the terminal (section 14.5–14.6)
- [ ] You can write and preview basic Markdown — headings, lists, links, code blocks, a table (section 10.5)
- [ ] All extensions from section 11.1 installed
- [ ] An AI chat/completion extension installed and tried at least once (section 15.5)
- [ ] The `iris-analysis` project runs and produces `iris_scatter.png`
- [ ] A notebook runs a cell using the `.venv` kernel, including at least one Markdown cell
- [ ] The project is published to GitHub, with a proper `README.md`, and visible in the browser

If any item fails, work through section 19 first. Bring the exact error message to class if you remain stuck.

If you're interested in exploring further before the next session, pick just one item from the table below rather than all of them — depth on one resource beats a skim of seven.

---

## Where to go next

| Resource | Link |
|---|---|
| uv documentation | https://docs.astral.sh/uv/ |
| VS Code Python tutorial | https://code.visualstudio.com/docs/python/python-tutorial |
| VS Code Jupyter support | https://code.visualstudio.com/docs/datascience/jupyter-notebooks |
| Git and GitHub in VS Code | https://code.visualstudio.com/docs/sourcecontrol/overview |
| GitHub Skills, interactive courses | https://skills.github.com/ |
| GitHub Flavored Markdown Spec | https://github.github.com/gfm/ |
| pandas user guide | https://pandas.pydata.org/docs/user_guide/ |

A closing word. The setup you have just completed is the least interesting part of data science, and it is also the part that stops the most people. You have now done it, on your own machine, whichever operating system it runs. Everything from here is the actual work: asking questions of data, and building the arguments that answer them — starting with Python itself.

---

*Prepared for Arewa Data Science Academy. Corrections and improvements are welcome as pull requests.*
