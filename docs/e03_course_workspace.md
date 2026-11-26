# Course workspace

Course files belong under `python_course` in the **home directory** (`~`).

```text
~/python_course/
├── projects/               # independent projects
│   └── proj1/              # first project (created next)
├── data/                   # shared input data
├── jupyter_work/
│   ├── notebooks/          # notebooks outside projects
│   └── envs/               # shared Jupyter environments
└── student-work/                  # Git repository
    ├── lab1/
    │   └── results.md
    ├── lab2/
    │   └── results.md
    └── ...
```

## Create the directories

In **PowerShell 7** (the same commands work in Bash and Zsh):

```powershell
cd ~
mkdir python_course
cd python_course
mkdir projects
mkdir data
mkdir jupyter_work
cd jupyter_work
mkdir notebooks
mkdir envs
cd ..
```

If a directory already exists, use the existing directory; do not delete its contents.

- `cd` — change directory.
- `mkdir` — create a directory.
- `~` — your home directory; `..` — parent directory.

## Check

```powershell
pwd
ls
ls jupyter_work
cd projects
mkdir proj1
cd proj1
pwd
```

Use the project directory (`projects/proj1`) in the next exercise. Project-specific scripts, data, notebooks and environments stay together inside the project.

Practice: [python-edu/exercises](https://github.com/python-edu/exercises).
