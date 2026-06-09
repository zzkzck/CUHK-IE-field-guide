# Programming Foundation

Programming is not a button. It is a workflow.

## 0. Why This Chapter Exists

A programming course may teach you how to write code.

It may not teach you how to live with code.

Year One programming courses usually focus on syntax, basic problem solving, and assignments. You may learn variables, loops, arrays, functions, pointers, classes, or simple algorithms. These are necessary. They are not enough.

The missing part is workflow.

A real programming workflow includes:

- knowing where your files are
- using a practical editor
- running code outside an IDE
- understanding basic compilation
- reading error messages
- debugging systematically
- using Git
- pushing projects to GitHub
- organising folders
- working with Linux or remote machines
- using AI without becoming dependent on it

This chapter is not a complete programming textbook. It will not teach every detail of C, Python, Git, Linux, or software engineering.

It has a narrower goal:

> Help you become minimally independent.

By the end of Year One, you do not need to be a professional software engineer. But you should not collapse the moment CLion breaks, a terminal appears, a server asks for SSH, or a project contains more than one file.

The goal is not to know every tool.

The goal is to stop being helpless.

---

## 1. Stop Depending on the Green Run Button

IDEs are useful.

CLion, VS Code, PyCharm, IntelliJ, and other editors can save time, catch mistakes, manage files, and make programming more comfortable. They are not the enemy.

The problem begins when your entire programming workflow becomes:

> open IDE → press green run button → hope

That is not a workflow. That is a habit.

An IDE hides many things for you:

- where the source file is stored
- which compiler or interpreter is used
- what command is actually executed
- where the executable is created
- what the working directory is
- how input and output files are located
- what environment variables are set

This is convenient when everything works.

It is dangerous when something breaks.

Sooner or later, you will meet an environment where the green run button does not exist: a Linux server, a course VM, a research codebase, an open-source project, a remote machine, or a terminal-only setup.

At that moment, the question is simple:

> Do you understand what your tools were doing for you?

If the answer is no, you are not doomed. But you need to learn.

Minimum standard: you should be able to run a small C or Python program without relying on an IDE button.

For C:

```bash
gcc main.c -o main
./main
```

For Python:

```bash
python3 script.py
```

You do not need to abandon IDEs. You need to understand what happens beneath them.

> If your workflow collapses when the green run button disappears, you do not have a workflow.  
> You have a habit.

---

## 2. Know Where Your Code Actually Lives

Many beginner programming problems are not algorithm problems.

They are file problems.

The code is in the wrong folder.  
The input file is somewhere else.  
The executable is outdated.  
The submitted file is not the latest version.  
There are five copies of `main.c`, and nobody knows which one matters.

This is not funny when a deadline is close.

You need basic file system awareness.

At minimum, understand:

- folder / directory
- file path
- absolute path
- relative path
- working directory
- source file
- executable file
- input and output files

A common beginner mistake is not knowing the working directory.

Your code may be correct, but it cannot find `input.txt` because the program is running from a different folder than you think. Then you blame C, Python, CLion, macOS, Windows, or the universe.

Sometimes the problem is simply that your mental map of the folder is wrong.

Do not code directly in random places:

- `Downloads`
- Desktop chaos
- WeChat file folders
- temporary folders
- folders named `new new final`

Create one folder per lab, assignment, or project.

Example:

```text
engg1110-lab03/
├── README.md
├── main.c
├── input.txt
├── output.txt
└── notes.md
```

For a slightly larger project:

```text
small-c-project/
├── README.md
├── src/
│   └── main.c
├── data/
│   └── input.txt
├── output/
└── notes.md
```

The exact structure can change. The principle does not.

Your files should not be a crime scene.

Minimum standard: you should be able to point to your source file, executable, input files, output files, and Git repository without guessing.

> If you do not know where your code lives, you do not fully control your code.

---

## 3. Terminal Is Not Optional

The terminal is not black magic.

It is just another interface.

A graphical interface lets you click.  
A terminal lets you describe actions precisely.

You do not need to love the terminal. You do not need to become a Linux wizard in Year One. But you need to stop being helpless in front of it.

The terminal is used for:

- navigating folders
- compiling programs
- running scripts
- using Git
- connecting to remote machines
- managing files
- running build commands
- checking logs
- automating repeated tasks

Basic commands you should know:

```bash
pwd       # show current directory
ls        # list files
cd        # change directory
mkdir     # create directory
cp        # copy files
mv        # move or rename files
rm        # remove files
cat       # print file content
grep      # search text
man       # read manual pages
```

Do not memorise commands without understanding what problem they solve.

For example:

```bash
pwd
```

answers:

> Where am I?

```bash
ls
```

answers:

> What is here?

```bash
cd folder-name
```

answers:

> How do I move there?

That is the level you need first.

Be careful with destructive commands.

```bash
rm file.txt
```

removes a file.

```bash
rm -r folder/
```

removes a folder recursively.

Do not run commands you do not understand just because the internet told you to. Especially not commands with `sudo`, `rm -rf`, or random installation scripts.

Terminal confidence is not about typing fast. It is about knowing what you are doing.

> Terminal is not optional.  
> Panic is.

Minimum standard: you should be able to navigate to a project folder, list files, compile a C program, run a Python script, and use Git from the terminal.

---

## 4. Compilation: Understand the Basic Pipeline

C code does not run directly.

A `.c` file is source code. It must be compiled into an executable before your computer can run it.

The simplified pipeline is:

```text
source code → compiler → executable → runtime behaviour
```

Example:

```bash
gcc main.c -o main
./main
```

Here:

- `main.c` is your source file
- `gcc` is the compiler
- `-o main` tells the compiler to create an executable named `main`
- `./main` runs the executable

This matters because different errors happen at different stages.

### Compile-time errors

These happen when the compiler cannot translate your code.

Examples:

- missing semicolon
- undeclared variable
- wrong function signature
- type mismatch
- syntax error

The program never runs.

### Runtime errors

These happen while the program is running.

Examples:

- segmentation fault
- division by zero
- invalid memory access
- file not found
- infinite recursion

The program starts, then fails.

### Logical errors

These are the most dangerous.

The program compiles.  
The program runs.  
The answer is wrong.

Examples:

- off-by-one error
- wrong condition
- incorrect formula
- mistaken loop boundary
- using the wrong variable
- misunderstanding the problem

A compiler cannot save you from all logical errors. That is why testing and debugging matter.

Also, warnings are not decoration.

If the compiler gives warnings, read them. Many warnings are early signs of future bugs.

Useful flags:

```bash
gcc -Wall -Wextra main.c -o main
```

This asks the compiler to warn you more aggressively.

Do not treat compiler errors as insults.

A compiler error means:

> Your mental model and the language rules disagree somewhere.

Your job is to locate the disagreement.

Minimum standard: you should understand the difference between source code, executable, compile-time error, runtime error, and logical error.

---

## 5. Debugging Is a Skill, Not a Mood

Many beginners debug by emotion.

They stare at the code.  
They randomly change lines.  
They run again.  
They hope the error disappears.  
Sometimes they ask AI to rewrite everything.

This is not debugging.

This is gambling with syntax.

Debugging is the process of reducing uncertainty.

A basic debugging workflow:

1. Reproduce the bug.
2. Reduce the input.
3. Read the error message.
4. Locate the suspicious region.
5. Add observations.
6. Change one thing at a time.
7. Verify the fix.
8. Explain what was wrong.

### Reproduce the bug

If you cannot reproduce the bug, you do not control the situation.

Find the exact input, command, or action that causes the problem.

### Reduce the case

Do not debug the largest possible case first.

Use a smaller input.  
Use fewer variables.  
Use a shorter example.  
Make the bug easier to see.

### Read the error message

Actually read it.

Not emotionally. Technically.

Look for:

- file name
- line number
- error type
- variable name
- function name
- expected type
- actual type

The error message may not tell you the full cause, but it often tells you where to start.

### Add observations

Print debugging is not shameful.

Bad print debugging:

```c
printf("here\n");
printf("here2\n");
printf("????\n");
```

Better print debugging:

```c
printf("i = %d, sum = %d, arr[i] = %d\n", i, sum, arr[i]);
```

Observe variables that matter.

### Change one thing at a time

If you change five things and the bug disappears, you may not know which change fixed it.

Then you have learned almost nothing.

### Verify the fix

One successful run is not proof.

Test:

- normal cases
- edge cases
- small cases
- large cases
- invalid or unexpected cases if relevant

After fixing a bug, you should be able to say:

- what was wrong
- why it happened
- how you found it
- why your fix works

If you cannot explain the fix, the bug may only be temporarily asleep.

> Debugging is not guessing faster.  
> It is reducing uncertainty.

Minimum standard: do not merely make the error disappear. Understand why it disappeared.

---

## 6. Git: Save Your Work Like an Adult

If losing one file can destroy your week, your workflow is irresponsible.

Git is version control.

It lets you track changes, save snapshots, compare versions, recover old work, and understand how your project evolved.

Git is not GitHub.

Git is the tool.  
GitHub is one platform that hosts Git repositories online.

Learn Git locally first. If you do not know what `git status` means, pushing to GitHub will only upload confusion to the internet.

Basic Git commands:

```bash
git init
git status
git add
git commit
git log
git diff
```

A minimal workflow:

```bash
git init
git status
git add main.c
git commit -m "Implement initial solution"
git status
```

Use `git status` often.

It tells you what changed, what is staged, and what is not being tracked.

Use `git diff` before committing.

It shows what you actually changed. This prevents stupid commits.

Do not use Git only at the end of a project. That is like wearing a seatbelt after the crash.

Commit when you complete a meaningful step:

- initial project setup
- implement input parsing
- add main algorithm
- fix off-by-one bug
- add test cases
- update README
- refactor function names

Bad commit messages:

```text
update
fix
final
asdf
changes
```

Better commit messages:

```text
Implement input parser
Fix loop boundary in sorting function
Add test cases for empty input
Update README with compile instructions
```

A commit message is not decoration. It is a note to your future self.

And your future self is usually tired.

Do not keep files like:

```text
main_final.c
main_final2.c
main_real_final.c
main_real_final_fixed.c
main_really_final_submit_this_one.c
```

This is not version control. This is digital panic.

Use Git.

> Git is not decoration.  
> It is a seatbelt.

Minimum standard: by the end of Year One, you should be able to initialise a repository, commit changes, inspect history, compare changes, and recover from small mistakes.

---

## 7. GitHub: Your Code Needs a Home

Git saves your work.

GitHub gives your work a place to live.

Do not confuse them.

Git is the version control system on your machine. GitHub is a remote platform where you can store repositories, back up your work, share projects, collaborate with others, and show what you have built.

In Year One, GitHub does not need to be impressive.

It needs to exist.

You do not need a perfect profile. You do not need ten polished projects. You do not need to pretend that every lab exercise is a startup prototype.

But you should have at least one small repository that proves you can:

- create a project folder
- initialise Git
- write a basic README
- commit changes properly
- push code to GitHub
- organise files clearly
- explain how to run your code

A GitHub repository is not just storage.

It is a communication object.

When someone opens your repository, they should not need to guess what it is. A minimum useful repository should answer:

- What is this project?
- Why does it exist?
- What language or tools does it use?
- How do I run it?
- What files matter?
- What is unfinished or planned?

This is why `README.md` matters.

A project without a README is like a lab report with no title, no explanation, and no instructions. Maybe the code works. Nobody knows.

A simple README is enough:

```markdown
# Project Name

A short description of what this project does.

## Features

- Feature 1
- Feature 2
- Feature 3

## How to Run

`gcc main.c -o main`

`./main`

## Notes

This is a Year One practice project for learning C, Git, and basic project organisation.
```

Do not upload everything blindly.

Be careful with:

- assignment solutions that should not be public
- private course materials
- passwords, API keys, tokens, or `.env` files
- personal data
- files you do not have permission to share
- messy generated files
- build files
- random downloads

GitHub is public by default if you create a public repository.

Treat it like publishing, not dumping.

For course assignments, use private repositories unless the course clearly allows public sharing. Academic honesty still applies. A public GitHub repo can accidentally become someone else's plagiarism source — and your problem.

GitHub also becomes useful later.

When you apply for internships, research opportunities, project teams, or collaborations, people may ask what you have built. A clean GitHub profile is not a guarantee of anything, but an empty or chaotic one says something too.

You do not need to look like a professional developer in Year One.

But you should start leaving evidence that you are learning seriously.

> GitHub is not a trophy cabinet.  
> It is a workshop with windows.

Minimum standard: by the end of Year One, you should have at least one clean GitHub repository with a README, meaningful commits, and code that another person can understand without asking you five basic questions.

---

## 8. Project Structure: Stop Throwing Files Everywhere

A messy folder is not a personality trait.

It is technical debt with a cute name.

As your programs grow, file organisation matters. A single `main.c` is fine for a tiny lab. But once you have multiple source files, input files, output files, notes, test cases, and reports, chaos becomes expensive.

A small beginner project may look like this:

```text
my-lab/
├── README.md
├── main.c
├── input.txt
├── output.txt
└── notes.md
```

A more structured C project may look like this:

```text
c-project/
├── README.md
├── src/
│   ├── main.c
│   └── utils.c
├── include/
│   └── utils.h
├── tests/
│   └── test_cases.txt
├── data/
│   └── sample_input.txt
└── docs/
    └── notes.md
```

A Python project may look like this:

```text
python-project/
├── README.md
├── src/
│   └── main.py
├── data/
│   └── sample.csv
├── notebooks/
├── tests/
└── requirements.txt
```

Do not blindly copy structures you do not understand. Start simple. Add folders only when they solve a real problem.

Basic principles:

- source code should be easy to find
- data files should not be mixed randomly with code
- generated output should be separated
- notes should not be hidden in chat history
- README should explain how to run the project
- file names should be clear
- avoid spaces and strange characters in paths when learning terminal
- do not commit unnecessary build files

Use `.gitignore` when needed.

A `.gitignore` file tells Git what not to track.

Examples:

```gitignore
*.o
*.out
.DS_Store
__pycache__/
.env
build/
```

Do not make your future self reverse-engineer your own folder.

That is unpaid labour.

Minimum standard: every project folder should make sense to someone opening it for the first time.

---

## 9. Python and C Serve Different Purposes

Do not turn programming languages into personality politics.

C and Python are both useful. They train different muscles.

C teaches you what the machine refuses to hide.

You need to care about:

- memory
- pointers
- arrays
- compilation
- types
- manual structure
- data representation
- low-level behaviour

C is not always comfortable. That is part of the point.

It exposes details that higher-level languages hide. If you study data structures, operating systems, embedded systems, networking, or performance-sensitive code, C forces you to respect the machine.

Python helps you move fast.

It is useful for:

- scripting
- data analysis
- automation
- quick experiments
- visualisation
- machine learning
- file processing
- small tools
- notebooks

Python lets you test ideas quickly. It is also widely used in research, data science, AI, and engineering workflows.

Do not use Python's convenience as an excuse to avoid understanding.

Do not use C's difficulty as an excuse to feel superior.

An IE student should ideally be comfortable with both:

- C for foundations and systems thinking
- Python for productivity and experimentation

They are not enemies.

They are different tools for different layers of reality.

> C teaches you what the machine refuses to hide.  
> Python helps you move fast once you know what you are doing.

Minimum standard: by the end of Year One, you should be able to write small programs in both C and Python, and understand why each language is useful.

---

## 10. Linux, SSH, and Remote Machines

A lot of real engineering work happens on Linux.

Servers run Linux.  
Research machines often run Linux.  
Many course environments use Linux or Linux-like systems.  
Remote development usually assumes you can survive in a terminal.

You do not need to become a Linux administrator in Year One.

But you should not panic when a course asks you to log into a remote machine.

Basic ideas:

- Linux is an operating system family widely used in servers and development.
- macOS is Unix-like, so terminal skills transfer reasonably well.
- Windows users can use WSL2 to get a Linux environment.
- SSH lets you log into a remote machine securely.
- Remote machines often do not have a graphical interface.
- File paths, permissions, and environment variables matter.

A basic SSH command looks like:

```bash
ssh username@server-address
```

For example:

```bash
ssh student@example.com
```

Do not worry if this feels strange at first. The important thing is to understand the idea:

> You are using your local machine to control a remote machine through the terminal.

You may also need to transfer files.

Common tools include:

```bash
scp local_file.txt username@server-address:/remote/path/
```

or:

```bash
scp username@server-address:/remote/path/file.txt .
```

The first command sends a file to the remote machine.  
The second command copies a file back to your current local folder.

Remote workflow requires discipline.

You need to know:

- which machine you are on
- which folder you are in
- where the files are stored
- whether you are editing local or remote files
- how to move files safely
- how to avoid overwriting work

Many remote mistakes come from one simple problem:

> The student does not know where they are.

Use `pwd`.

Use `ls`.

Check before deleting or overwriting anything.

Minimum standard: by the end of Year One, you should understand what SSH is for, log into a remote machine at least once, and transfer a file without panic.

---

## 11. AI Coding: Use It Without Becoming Useless

AI can help you learn programming.

It can also help you avoid learning programming.

The difference is not the tool.

The difference is how you use it.

AI is useful for:

- explaining compiler errors
- explaining unfamiliar syntax
- generating small examples
- suggesting test cases
- reviewing code style
- comparing approaches
- locating likely bug regions
- explaining concepts at different levels
- helping you start when you are stuck

Good prompts:

```text
Explain this compiler error. Assume I am a beginner in C.
```

```text
Here is my C code. Do not rewrite it. Help me identify where the bug may be.
```

```text
Give me three small test cases for this function. Hide the expected output first.
```

```text
Explain the difference between compile-time error, runtime error, and logical error using this example.
```

```text
Review my README. Tell me what information is missing.
```

Bad prompts:

```text
Write my assignment.
```

```text
Fix everything.
```

```text
Give me the final answer.
```

```text
Make this code work. I do not care why.
```

If AI writes code that you cannot explain, the code is not really yours in any meaningful learning sense.

Maybe it passes the test.

Maybe you get the mark.

But your foundation remains empty.

This becomes dangerous later. Higher-level courses assume you actually learned the earlier material. Projects assume you can debug. Internships assume you can read code. Research assumes you can survive ambiguity.

AI can cover your weakness for a while.

It cannot remove the weakness unless you use it to learn.

A better AI workflow:

1. Try the problem yourself.
2. Identify where you are stuck.
3. Ask AI for explanation or hints.
4. Apply the idea manually.
5. Test the result.
6. Explain the solution in your own words.
7. Check course policy before using AI in assessed work.

Academic honesty still matters.

Different courses may have different rules. Some allow AI assistance. Some restrict it. Some require declaration. Some prohibit certain uses entirely.

Read the course policy.

Do not destroy your academic record because you wanted to save two hours.

> AI can make a strong programmer faster.  
> It can also make a weak programmer better at pretending.

Minimum standard: never submit code you cannot explain.

---

## 12. Minimum Programming Setup for Year One

The exact tools may change.

The capability should not.

You do not need the most expensive setup. You need a setup that lets you write, run, debug, save, and organise code reliably.

### If You Use macOS

A reasonable setup:

- VS Code
- Xcode Command Line Tools
- Git
- Python 3
- Homebrew
- SSH client
- optional: CLion or another IDE

Useful commands:

```bash
xcode-select --install
git --version
python3 --version
gcc --version
```

Homebrew is useful for installing developer tools, but do not install random packages without understanding why you need them.

### If You Use Windows

A reasonable setup:

- VS Code
- WSL2
- Ubuntu on WSL
- Git
- Python 3
- GCC inside WSL
- SSH client
- optional: CLion or another IDE

Windows itself is not the problem.

The problem is having no clean development environment.

WSL2 is useful because many engineering tools assume a Linux-like workflow. If a course or project expects Linux commands, WSL2 can save you from fighting Windows path issues for no reason.

### If You Use Linux

A reasonable setup:

- VS Code or a terminal editor
- Git
- GCC
- Python 3
- SSH
- build tools
- package manager for your distribution

Linux gives you a development-friendly environment, but it also gives you more responsibility. Do not blindly run commands with `sudo` because a forum said so.

### For Everyone

You should be able to:

- create a project folder
- open it in an editor
- write code
- run code from terminal
- commit changes with Git
- push a small project to GitHub
- write a README
- debug basic errors
- recover from small mistakes

Do not spend two weeks perfecting your setup before writing any code.

Tool setup is not the achievement.

The achievement is using the tools to build things.

> A clean setup should reduce friction.  
> It should not become your excuse for avoiding work.

Minimum standard: your setup should allow you to complete a small programming project without losing files, guessing commands, or depending entirely on one IDE button.

---

## 13. Practical Checklist

This checklist is not meant to turn you into a professional developer overnight.

It is meant to make sure your foundation is not fake.

### Environment

- [ ] Install a practical code editor.
- [ ] Know where your code files are stored.
- [ ] Create one folder per lab, assignment, or project.
- [ ] Avoid coding directly in Downloads or Desktop chaos.
- [ ] Understand what a working directory is.
- [ ] Know the difference between source files, executable files, input files, and output files.

### Terminal

- [ ] Use `pwd`, `ls`, `cd`, `mkdir`, `cp`, `mv`, and `rm`.
- [ ] Navigate to a project folder from terminal.
- [ ] Compile and run a C program from terminal.
- [ ] Run a Python script from terminal.
- [ ] Understand relative and absolute paths.
- [ ] Avoid running dangerous commands you do not understand.

### C and Compilation

- [ ] Know the difference between source code and executable.
- [ ] Compile with `gcc`.
- [ ] Run an executable from terminal.
- [ ] Understand compile-time errors.
- [ ] Understand runtime errors.
- [ ] Understand logical errors.
- [ ] Read compiler errors before asking for help.
- [ ] Treat warnings seriously.

### Debugging

- [ ] Reproduce the bug.
- [ ] Use small test cases.
- [ ] Read the error message carefully.
- [ ] Use print debugging with purpose.
- [ ] Change one thing at a time.
- [ ] Verify the fix with more than one test.
- [ ] Explain the bug after fixing it.

### Git and GitHub

- [ ] Understand that Git and GitHub are not the same thing.
- [ ] Initialise a Git repository.
- [ ] Use `status`, `add`, `commit`, `log`, and `diff`.
- [ ] Write meaningful commit messages.
- [ ] Create a GitHub account.
- [ ] Push one small project to GitHub.
- [ ] Write a basic `README.md`.
- [ ] Keep assignment solutions private unless public sharing is allowed.
- [ ] Do not upload passwords, tokens, private data, or restricted course materials.
- [ ] Stop using `final_final.c`.

### Project Structure

- [ ] Organise files clearly.
- [ ] Separate source code, data, output, notes, and documentation when needed.
- [ ] Use clear file names.
- [ ] Add a README explaining how to run the project.
- [ ] Use `.gitignore` for generated files and sensitive files.
- [ ] Make your project understandable to someone opening it for the first time.

### Python and C

- [ ] Write small C programs without relying only on an IDE.
- [ ] Write small Python scripts from terminal.
- [ ] Understand why C is useful for foundations.
- [ ] Understand why Python is useful for productivity.
- [ ] Do not use one language as an excuse to avoid learning the other.

### Linux and Remote Workflow

- [ ] Understand what Linux is used for.
- [ ] Understand what SSH is used for.
- [ ] Log into a remote machine at least once.
- [ ] Transfer a file to or from a remote machine.
- [ ] Check which machine and folder you are working in.
- [ ] Do not delete or overwrite remote files blindly.

### AI Coding

- [ ] Ask AI to explain concepts.
- [ ] Ask AI to explain compiler errors.
- [ ] Ask AI to suggest test cases.
- [ ] Ask AI to review your code without rewriting everything.
- [ ] Check course policy before using AI in assessed work.
- [ ] Do not submit code you cannot explain.
- [ ] Use AI to learn faster, not to pretend better.

---

## Final Note

Programming foundation is not glamorous.

It is mostly boring competence.

Knowing where your files are.  
Reading error messages.  
Running code from terminal.  
Using Git before disaster.  
Writing a README.  
Testing small cases.  
Debugging without panic.  
Keeping secrets off GitHub.  
Understanding enough Linux not to freeze.  
Using AI without outsourcing your brain.

None of this will impress people in a short conversation.

But it will save you repeatedly.

Most students do not fail programming because they lack intelligence. They fail because their workflow is fragile. They depend on buttons they do not understand, folders they cannot navigate, errors they do not read, and tools they only use when deadlines are already burning.

Do not build your programming life on panic.

Build a workflow.

