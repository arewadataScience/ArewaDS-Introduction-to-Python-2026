# Getting Started with VS Code for Data Science

### A step by step setup guide for Windows

**Arewa Data Science Academy**

This guide takes you from a fresh Windows computer to a working data science environment. It assumes no prior programming experience. If you come from chemistry, biology, or any other background where the laboratory is a physical space rather than a screen, this guide is written for you.

Work through the sections in order. Do not skip ahead, because each step depends on the one before it. Set aside about ninety minutes for the whole process, and make sure you have a stable internet connection before you begin.

---

## Table of contents

1. [What we are building and why](#1-what-we-are-building-and-why)
2. [Before you begin](#2-before-you-begin)
3. [Installing VS Code](#3-installing-vs-code)
4. [A tour of the VS Code window](#4-a-tour-of-the-vs-code-window)
5. [The integrated terminal](#5-the-integrated-terminal)
6. [Survival commands for the terminal](#6-survival-commands-for-the-terminal)
7. [Installing uv](#7-installing-uv)
8. [Installing Python with uv](#8-installing-python-with-uv)
9. [Installing Git](#9-installing-git)
10. [Setting up GitHub](#10-setting-up-github)
11. [VS Code extensions for data science](#11-vs-code-extensions-for-data-science)
12. [Your first project, end to end](#12-your-first-project-end-to-end)
13. [Pushing your project to GitHub](#13-pushing-your-project-to-github)
14. [Optional: conda and when you might need it](#14-optional-conda-and-when-you-might-need-it)
15. [Troubleshooting](#15-troubleshooting)
16. [Command reference card](#16-command-reference-card)
17. [Setup checklist](#17-setup-checklist)

---

## 1. What we are building and why

### 1.1 What is VS Code?

Visual Studio Code (usually shortened to VS Code) is a free text editor made by Microsoft. Calling it a text editor undersells it. Think of it as a laboratory bench: a single surface where you keep your code, your data, your notes, your version history, and your command line, all within reach and all visible at once.

You could write Python in Notepad and run it from a separate black window. Thousands of people did exactly that for years. VS Code simply removes the friction, so that you spend your attention on the analysis rather than on the mechanics of moving between windows.

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

You may have heard of Anaconda or conda. They are widely used in scientific computing and there is nothing wrong with them. On this course we will use **uv** instead, because it is dramatically faster, much smaller to download, installs Python for you, and produces reproducible projects with far less ceremony. Section 14 explains the cases where conda is still the better choice.

Do not install both and mix them in the same project. Pick one per project.

---

## 2. Before you begin

### 2.1 Check your Windows version

Press `Windows key + R`, type `winver`, and press Enter. A small window will tell you your Windows version. You need **Windows 10 (version 1809 or later) or Windows 11**. Anything older will cause problems that this guide cannot solve.

### 2.2 Check whether your machine is 64 bit

Open **Settings**, then **System**, then **About**. Look at **System type**. Almost every machine made in the last decade says *64 bit operating system, x64 based processor*. If yours says ARM, note this down, because you will need the ARM64 downloads rather than the x64 ones at every step.

### 2.3 Free disk space

You need roughly **5 GB free**. Data science libraries are large. Check your C drive in **File Explorer** under **This PC**.

### 2.4 Create a folder for your work

This step is small but it will save you many hours of confusion later.

Open File Explorer and create a folder at:

```
C:\Users\YourName\projects
```

Replace `YourName` with your Windows username.

> **Important.** Do not put your code inside **Documents**, **Desktop**, or **OneDrive**. OneDrive synchronises files continuously, and it will fight with Python and Git over the thousands of small files a project creates. Symptoms include files that mysteriously vanish, environments that break overnight, and Git repositories that corrupt themselves. Keep your projects outside OneDrive.

Also avoid spaces, accents, and special characters in folder names. `heart-disease-analysis` is a good name. `My Project (final) 2!` will cause trouble.

---

## 3. Installing VS Code

### 3.1 Download

Go to **https://code.visualstudio.com/download** and click the blue **Windows** button. This downloads the *User Installer* for x64, which is what you want. It does not require administrator rights, which matters if you are using a shared or university machine.

The file will be named something like `VSCodeUserSetup-x64-1.xx.x.exe` and will appear in your **Downloads** folder.

### 3.2 Run the installer

Double click the file and work through the screens:

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

The two "Open with Code" options mean you can right click any folder in File Explorer and open it directly in VS Code. You will use this constantly.

**Add to PATH** means you can type `code .` in any terminal to open the current folder in VS Code. If you miss this option, see section 15.4 for the fix.

### 3.3 First launch

VS Code opens on a Welcome tab. You will be asked to choose a colour theme. Pick whichever you find comfortable, and do not agonise over it, because you can change it at any time with `Ctrl + K` then `Ctrl + T`.

You may be prompted to install extra tooling. Ignore all prompts for now. We install extensions deliberately in section 11.

---

## 4. A tour of the VS Code window

Before installing anything else, learn the geography. The window has four regions.

### 4.1 The Activity Bar (far left)

A vertical strip of icons. The five that matter now, from top to bottom:

| Icon | Name | Shortcut | Purpose |
|---|---|---|---|
| Two pages | **Explorer** | `Ctrl + Shift + E` | The files in your current folder |
| Magnifying glass | **Search** | `Ctrl + Shift + F` | Find text across every file |
| Branching lines | **Source Control** | `Ctrl + Shift + G` | Git, covered in section 9 |
| Play with a bug | **Run and Debug** | `Ctrl + Shift + D` | Step through code line by line |
| Four squares | **Extensions** | `Ctrl + Shift + X` | Install add-ons |

### 4.2 The Side Bar

Whatever the Activity Bar icon you clicked wants to show you. Toggle it away with `Ctrl + B` when you want more room.

### 4.3 The Editor

The large central area where files open, in tabs. You can split it into two or three columns by dragging a tab to the side, which is useful when comparing a script against its output.

### 4.4 The Panel (bottom)

Contains **Terminal**, **Problems**, **Output**, and **Debug Console**. Open and close it with ``Ctrl + ` `` (the backtick key, usually just under Escape on the left of the `1` key).

### 4.5 The Command Palette

The single most useful thing in VS Code. Press:

```
Ctrl + Shift + P
```

A search box appears at the top. Everything VS Code can do is in here and can be found by typing part of its name. If you forget a menu location or a shortcut, open the Command Palette and describe what you want. Commit this shortcut to memory.

### 4.6 Opening a folder

VS Code works on **folders**, not loose files. Go to **File**, then **Open Folder**, and choose `C:\Users\YourName\projects`. Everything in the Explorer panel is now relative to that folder, and the terminal will open inside it too.

---

## 5. The integrated terminal

### 5.1 What a terminal actually is

A terminal is a text conversation with your computer. You type an instruction, press Enter, and the computer replies in text. It feels primitive at first. It is in fact far more precise than clicking, because an instruction that works can be written down, shared, and repeated exactly, which is the same reason we write laboratory protocols rather than describing procedures from memory.

Everything in the rest of this guide happens in the terminal.

### 5.2 Opening it

Press ``Ctrl + ` ``, or go to **Terminal**, then **New Terminal**.

A panel opens at the bottom with a line ending in `>`. This is the prompt, and it is waiting for you.

### 5.3 Which shell you are using

Windows offers several shells, and the difference matters because the commands are not identical.

| Shell | Notes |
|---|---|
| **PowerShell** | The VS Code default on Windows. Use this one. All commands in this guide assume PowerShell. |
| **Command Prompt (cmd)** | Older and more limited. Avoid. |
| **Git Bash** | Arrives with Git. Uses Linux style commands. Useful later, but not our default. |

Confirm what you have. The dropdown on the right of the terminal panel names the current shell. To set the default explicitly, open the Command Palette (`Ctrl + Shift + P`), type `Terminal: Select Default Profile`, and choose **PowerShell**.

### 5.4 Terminal habits worth forming now

- The terminal always has a **current folder**. Commands act on that folder. Most beginner errors come from being in the wrong one.
- Press the **Up arrow** to bring back your previous command instead of retyping it.
- Press **Tab** to complete a half typed file or folder name.
- Press `Ctrl + C` to interrupt a command that is stuck or running too long.
- Type `cls` to clear a cluttered screen.

---

## 6. Survival commands for the terminal

Practise each of these now, in your terminal, before moving on.

### 6.1 Where am I?

```powershell
pwd
```

Prints the working directory, meaning the folder you are currently in.

### 6.2 What is in here?

```powershell
ls
```

Lists the contents of the current folder.

### 6.3 Move into a folder

```powershell
cd projects
```

`cd` means change directory. To move back up one level:

```powershell
cd ..
```

To go straight to a specific location:

```powershell
cd C:\Users\YourName\projects
```

If a path contains spaces, wrap it in quotation marks: `cd "C:\My Folder"`.

### 6.4 Make a new folder

```powershell
mkdir my-first-project
```

### 6.5 Open the current folder in VS Code

```powershell
code .
```

The full stop means "this folder". This command works only if you ticked **Add to PATH** during installation.

### 6.6 Check whether a tool is installed

```powershell
python --version
git --version
uv --version
```

Right now, all three will fail with a message about the command not being recognised. That is expected, and we are about to fix it.

---

## 7. Installing uv

**uv** is a Python package and project manager written in Rust. It replaces a long list of older tools, and it does the job between ten and a hundred times faster than the traditional approach. Crucially for us, it also installs Python itself, so it is the only thing you need to install by hand.

### 7.1 Install

In your VS Code terminal, paste this command exactly and press Enter:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

For Mac users:

```powershell
curl -LsSf https://astral.sh/uv/install.sh | sh
```




Reading it from left to right: run PowerShell with script restrictions bypassed for this one command, download the installation script from astral.sh, and execute it.

Installation takes a few seconds and prints a short summary when it finishes.

### 7.2 Restart the terminal

This step is not optional. Close the terminal panel by clicking the bin icon, then open a fresh one with ``Ctrl + ` ``. A terminal only reads the system PATH when it starts, so an existing terminal will not find newly installed tools.

### 7.3 Verify

```powershell
uv --version
```

You should see something like `uv 0.9.x`. If you see an error instead, go to section 15.1.

### 7.4 Keeping uv current

```powershell
uv self update
```

Run this every few weeks.

---

## 8. Installing Python with uv

### 8.1 Install Python

```powershell
uv python install 3.12
```

uv downloads a self contained Python 3.12 and stores it where uv can find it. This takes a minute or two on a reasonable connection.

We use 3.12 rather than the newest release because the scientific libraries you will rely on, such as NumPy, pandas, and scikit-learn, are thoroughly tested against it. Being one version behind is a feature, not a compromise.

### 8.2 Check what you now have

```powershell
uv python list
```

This lists the Python versions available to uv, marking those it has installed.

### 8.3 Why we are not downloading Python from python.org

Installing Python from the website works, and you will see it in many tutorials. It also has a well documented tendency to create difficulties for beginners: multiple competing installations, a PATH that points at the wrong one, and the Microsoft Store stub that intercepts the `python` command and does nothing useful. Letting uv manage Python versions sidesteps all of this. If you already installed Python from python.org, leave it alone; uv will not interfere with it.

### 8.4 A concept you must understand: the virtual environment

This is the single idea that separates people who fight their tools from people who do not.

Suppose your first project needs pandas version 1.5, and a project you start next year needs version 2.2. If all libraries live in one shared pile, installing the second version breaks the first project. In a field where reproducing a result months later is the whole point, this is unacceptable.

A **virtual environment** is a private box of libraries belonging to one project and nothing else. Each project gets its own. They never interfere with each other.

With uv, the environment lives in a folder called `.venv` inside your project, and uv creates and maintains it for you automatically. You will rarely think about it. But when something behaves strangely, the first question to ask is always: which environment am I actually in?

---

## 9. Installing Git

### 9.1 What Git is, and why it is not optional

Git records the state of your project every time you ask it to. Every recorded state can be returned to. This gives you three things:

- **Undo without limit.** If your analysis worked on Tuesday and is broken on Thursday, you can see precisely what changed, and go back.
- **An end to file name chaos.** No more `analysis_final.py`, `analysis_final_v2.py`, `analysis_final_REALLY_FINAL.py`. There is one file, with a complete history behind it.
- **Collaboration.** Two people can work on the same project without overwriting each other's work.

Git is a laboratory notebook for code, and the argument for keeping one is exactly the same.

### 9.2 Download and install

Go to **https://git-scm.com/download/win** and choose the **64 bit Git for Windows Setup** installer.

The installer asks many questions. The defaults are sensible, but three screens deserve attention:

1. **Choosing the default editor used by Git.** Select **Use Visual Studio Code as Git's default editor** from the dropdown. The default is Vim, which is a legendary source of panic for beginners who cannot work out how to exit it.
2. **Adjusting the name of the initial branch.** Select **Override the default branch name for new repositories** and leave it as `main`. This matches GitHub.
3. **Adjusting your PATH environment.** Keep the recommended middle option, *Git from the command line and also from 3rd-party software*.

Accept the defaults on every other screen and click through to **Install**.

### 9.3 Restart the terminal and verify

Close and reopen the terminal in VS Code, then run:

```powershell
git --version
```

You should see something like `git version 2.4x.x.windows.1`.

### 9.4 Tell Git who you are

Git labels every change with an author. Set this once, and it applies to all future projects. Use the same email address that you will use for GitHub.

```powershell
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"
```

Set two further defaults that avoid common annoyances:

```powershell
git config --global init.defaultBranch main
git config --global core.autocrlf true
```

Confirm your settings:

```powershell
git config --global --list
```

---

## 10. Setting up GitHub

### 10.1 Git and GitHub are different things

A frequent point of confusion. **Git** is the program on your computer that tracks changes. **GitHub** is a website that stores copies of Git projects online. Git works perfectly well without GitHub. GitHub without Git would be meaningless.

The relationship is roughly that of a laboratory notebook to the departmental archive.

### 10.2 Create your account

Go to **https://github.com/signup** and register.

Two pieces of advice on the username, because it is difficult to change later and it will appear on your CV:

- Use something professional and close to your real name. `amina-yusuf` or `ayusuf-data` are good. `coolguy2005` is not.
- Keep it short and easy to type.

Verify your email address when the confirmation arrives.

### 10.3 Enable two factor authentication

GitHub requires this for all accounts. Go to **Settings**, then **Password and authentication**, and follow the prompts. Use an authenticator app on your phone. Save the recovery codes somewhere safe, because if you lose your phone without them, you lose the account.

### 10.4 Apply for the Student Developer Pack

If you have a university email address, go to **https://education.github.com/pack** and apply. It is free, and it includes GitHub Copilot and a long list of other services.

### 10.5 Connecting VS Code to GitHub

You do not need to configure SSH keys or personal access tokens by hand. Git for Windows installs **Git Credential Manager**, which handles authentication through your browser.

To sign VS Code in as well, click the **Accounts** icon at the bottom of the Activity Bar, choose **Sign in with GitHub**, and complete the process in the browser window that opens. This enables settings sync and smooths every later interaction with GitHub.

The first time you push code, a browser window will open asking you to authorise. Approve it once, and Windows remembers the credentials.

---

## 11. VS Code extensions for data science

### 11.1 Installing from the terminal

Extensions can be installed by clicking through the Extensions panel, but it is faster and far more reproducible to use the terminal. Paste this block into your VS Code terminal:

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
| Data Wrangler | `ms-toolsai.datawrangler` | Point and click inspection and cleaning of dataframes, with the equivalent pandas code generated for you |
| Ruff | `charliermarsh.ruff` | Extremely fast linting and formatting, so your code stays readable |
| GitLens | `eamodio.gitlens` | Shows who changed each line, and when |
| GitHub Pull Requests | `GitHub.vscode-pull-request-github` | Review and manage pull requests without leaving the editor |
| Rainbow CSV | `mechatroner.rainbow-csv` | Colours CSV columns so raw data files are readable |
| Error Lens | `usernamehw.errorlens` | Displays errors inline rather than hiding them in a panel |
| Markdown All in One | `yzhang.markdown-all-in-one` | Preview and shortcuts for README files |
| Even Better TOML | `tamasfe.even-better-toml` | Syntax support for `pyproject.toml`, which uv creates |

**A caution.** Extensions are tempting to collect. Each one consumes memory and startup time, and a heavily loaded VS Code becomes sluggish on a modest laptop. Install the list above, use it for a term, and add further extensions only when you have felt the specific need.

### 11.3 A few settings worth changing

Open the Command Palette, type `Preferences: Open User Settings (JSON)`, and add the following inside the outer braces:

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

---

## 12. Your first project, end to end

Everything is installed. We now build a small project to confirm that the pieces work together.

### 12.1 Create the project

In the terminal:

```powershell
cd C:\Users\YourName\projects
uv init iris-analysis
cd iris-analysis
code .
```

`uv init` creates a project folder containing:

| File | Purpose |
|---|---|
| `pyproject.toml` | The project description, including its dependencies |
| `main.py` | A starter script |
| `README.md` | Documentation for human readers |
| `.python-version` | Records which Python version this project uses |
| `.gitignore` | Lists files Git should ignore |

### 12.2 Add libraries

```powershell
uv add pandas matplotlib seaborn scikit-learn jupyter ipykernel
```

Watch the terminal. uv creates the `.venv` folder, resolves the dependency graph, and installs everything, typically in a few seconds. The same operation with older tools routinely took several minutes.

Note that you did not activate anything and did not run `pip`. uv handled the environment for you.

### 12.3 Write a script

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

### 12.4 Run it

```powershell
uv run main.py
```

`uv run` executes the script inside the project environment. You never have to remember to activate anything.

You should see the summary tables printed, and a new file `iris_scatter.png` in the Explorer panel. Click it to view the figure.

### 12.5 Work in a notebook

Scripts are right for pipelines you will run repeatedly. Notebooks are right for exploration, where you want to see the result of each step before deciding on the next.

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

The dataframe appears below the cell. In the output, look for the **Open in Data Wrangler** button, which gives you a spreadsheet style view for filtering, sorting, and cleaning, while writing the corresponding pandas code for you.

### 12.6 Commands you will use every day

| Command | Effect |
|---|---|
| `uv add package-name` | Add a library to the project |
| `uv remove package-name` | Remove a library |
| `uv run script.py` | Run a script in the project environment |
| `uv sync` | Rebuild the environment to match `pyproject.toml` |
| `uv lock` | Update the lock file that pins exact versions |
| `uvx tool-name` | Run a command line tool without installing it permanently |

---

## 13. Pushing your project to GitHub

### 13.1 Initialise version control

Still inside the project folder:

```powershell
git init
git add .
git commit -m "Initial commit: iris analysis setup"
```

Reading these three lines: start tracking this folder, stage everything currently in it, and record a permanent snapshot with a short description.

A commit message should say what changed and why. `Add species comparison plot` is useful. `update` and `stuff` are not, and your future self will resent them.

### 13.2 Check what Git is ignoring

Open the `.gitignore` file that `uv init` created. It already excludes `.venv` and Python's cache folders. This is correct, because environments are rebuilt from `pyproject.toml` rather than shared.

Add two more lines yourself:

```gitignore
# Data files, which are often large and sometimes confidential
data/raw/
*.csv
*.xlsx

# Credentials, which must never be committed
.env
```

> **A rule with no exceptions.** Never commit passwords, API keys, or personal data. Once something reaches GitHub it is in the history permanently, and deleting the file afterwards does not remove it. Treat this with the seriousness you would give to publishing patient records.

### 13.3 Create the repository on GitHub

The easiest route is through VS Code itself:

1. Open the **Source Control** panel (`Ctrl + Shift + G`).
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

### 13.4 The daily rhythm

After the first push, your working cycle is:

```powershell
git add .
git commit -m "Describe what you changed"
git push
```

Or use the Source Control panel: type a message in the box, click the tick to commit, then click **Sync Changes**.

Commit whenever you finish a coherent piece of work, which in practice means several times a day. Small, frequent commits are easy to review and easy to undo. One enormous commit at the end of the week is neither.

---

## 14. Optional: conda and when you might need it

You will meet conda in scientific computing, and you should know where it fits.

Use **uv** for essentially everything on this course. It is faster, lighter, and produces cleaner projects.

Consider **conda** when:

- A package you need has heavy non Python dependencies that are difficult to install with pip, for example some bioinformatics and cheminformatics tools such as RDKit, or older geospatial stacks.
- Your laboratory or supervisor already standardises on conda and you must match their environment.
- You are following a bioinformatics workflow that assumes Bioconda.

If you need it, install **Miniconda**, not the full Anaconda distribution, because Anaconda installs several gigabytes of packages you will never use.

Download from **https://www.anaconda.com/download/success** and choose the Miniconda Windows 64 bit installer. After installing, run once:

```powershell
conda init powershell
```

Restart the terminal, then create environments as needed:

```powershell
conda create -n bioproject python=3.12
conda activate bioproject
conda install -c conda-forge rdkit
```

> **Keep them apart.** Do not use uv and conda in the same project folder. Each expects to control the environment, and mixing them produces failures that are extremely difficult to diagnose. One project, one manager.

---

## 15. Troubleshooting

### 15.1 "uv is not recognised as the name of a cmdlet"

Almost always because the terminal was open before uv was installed.

1. Close the terminal panel completely using the bin icon.
2. Open a new one with ``Ctrl + ` ``.
3. If it still fails, close VS Code entirely and reopen it.
4. If it still fails, restart Windows.

### 15.2 Typing `python` opens the Microsoft Store

Windows ships a placeholder that hijacks the `python` command. Disable it.

Open **Settings**, then **Apps**, then **Advanced app settings**, then **App execution aliases**. Turn **off** every entry named `python.exe` and `python3.exe`.

Note that with uv you rarely type `python` directly. Use `uv run` instead.

### 15.3 "Running scripts is disabled on this system"

PowerShell blocks scripts by default. Run this once:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

This applies to your user account only and does not require administrator rights. Answer `Y` when prompted.

### 15.4 `code .` does nothing

The PATH entry is missing. Open VS Code, press `Ctrl + Shift + P`, type `Shell Command: Install 'code' command in PATH`, and run it. Then restart the terminal.

### 15.5 The notebook cannot find a library you installed

You have selected the wrong kernel. Click the kernel name at the top right of the notebook, choose **Select Another Kernel**, then **Python Environments**, and pick the one showing `.venv` inside your project folder. Almost every "but I installed it" problem is this.

### 15.6 Downloads fail or time out

Frequently a network issue rather than a tool issue.

- Retry, because transient failures are common.
- If you are on a university or corporate network, a proxy may be blocking the connection. Try a mobile hotspot to confirm.
- If a download stalls repeatedly, run the command again. uv caches what it already fetched and resumes rather than starting over.

### 15.7 Git asks for a password and rejects it

GitHub stopped accepting account passwords for Git operations. Let Git Credential Manager handle it: when a browser window opens, sign in there. If credentials have become stale, open **Credential Manager** from the Windows Start menu, go to **Windows Credentials**, and delete any entry mentioning `github.com`. The next push will prompt you afresh.

### 15.8 Filename or path too long

Windows historically limited paths to 260 characters. Shorten your project path, which is another reason to work in `C:\Users\YourName\projects` rather than deep inside Documents. You can also run, in a terminal opened as administrator:

```powershell
git config --system core.longpaths true
```

### 15.9 Everything is broken and you cannot work out why

Delete the environment and rebuild it. This is safe, because the environment is disposable by design.

```powershell
Remove-Item -Recurse -Force .venv
uv sync
```

If the problem persists, note the exact error message, including the final few lines of output, and bring it to the class channel. "It does not work" cannot be diagnosed. The error text usually can be.

---

## 16. Command reference card

### VS Code shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl + Shift + P` | Command Palette, the answer to most questions |
| ``Ctrl + ` `` | Toggle the terminal |
| `Ctrl + B` | Toggle the side bar |
| `Ctrl + P` | Jump to a file by name |
| `Ctrl + S` | Save |
| `Ctrl + /` | Comment or uncomment the selected lines |
| `Shift + Enter` | Run the current notebook cell |
| `Ctrl + Shift + X` | Extensions |
| `Ctrl + Shift + G` | Source Control |

### Terminal

| Command | Action |
|---|---|
| `pwd` | Show the current folder |
| `ls` | List the contents |
| `cd folder-name` | Enter a folder |
| `cd ..` | Go up one level |
| `mkdir name` | Create a folder |
| `cls` | Clear the screen |
| `code .` | Open the current folder in VS Code |

### uv

| Command | Action |
|---|---|
| `uv init project-name` | Create a new project |
| `uv add package` | Install a library into the project |
| `uv remove package` | Uninstall a library |
| `uv run script.py` | Run a script in the project environment |
| `uv sync` | Rebuild the environment from the project files |
| `uv python install 3.12` | Install a Python version |
| `uv python list` | List available Python versions |
| `uv self update` | Update uv itself |
| `uvx tool` | Run a tool without installing it |

### Git

| Command | Action |
|---|---|
| `git status` | What has changed, and what is staged |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Record a snapshot |
| `git push` | Upload to GitHub |
| `git pull` | Download changes from GitHub |
| `git log --oneline` | Show the history compactly |
| `git clone url` | Copy a repository from GitHub to your machine |

---

## 17. Setup checklist

Confirm each item before the next session. Where a check is a command, run it in a fresh VS Code terminal.

- [ ] Windows version confirmed as 10 (1809 or later) or 11
- [ ] A `projects` folder exists outside OneDrive
- [ ] VS Code installed, with "Add to PATH" enabled
- [ ] `code .` opens the current folder
- [ ] Terminal opens with ``Ctrl + ` `` and the shell is PowerShell
- [ ] `uv --version` returns a version number
- [ ] `uv python list` shows Python 3.12 installed
- [ ] `git --version` returns a version number
- [ ] `git config --global --list` shows your name and email
- [ ] GitHub account created, with two factor authentication enabled
- [ ] VS Code signed in to GitHub
- [ ] All extensions from section 11.1 installed
- [ ] The `iris-analysis` project runs and produces `iris_scatter.png`
- [ ] A notebook runs a cell using the `.venv` kernel
- [ ] The project is published to GitHub and visible in the browser

If any item fails, work through section 15 first. Bring the exact error message to class if you remain stuck.

---

## Where to go next

| Resource | Link |
|---|---|
| uv documentation | https://docs.astral.sh/uv/ |
| VS Code Python tutorial | https://code.visualstudio.com/docs/python/python-tutorial |
| VS Code Jupyter support | https://code.visualstudio.com/docs/datascience/jupyter-notebooks |
| Git and GitHub in VS Code | https://code.visualstudio.com/docs/sourcecontrol/overview |
| GitHub Skills, interactive courses | https://skills.github.com/ |
| pandas user guide | https://pandas.pydata.org/docs/user_guide/ |

A closing word. The setup you have just completed is the least interesting part of data science, and it is also the part that stops the most people. You have now done it. Everything from here is the actual work: asking questions of data, and building the arguments that answer them.

---

*Prepared for Arewa Data Science Academy. Corrections and improvements are welcome as pull requests.*
