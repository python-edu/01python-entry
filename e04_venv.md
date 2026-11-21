# Virtual environments (`venv`)

>- `venv` is a **module in Python's standard library**, not a separate program to install
>- it is included with Python and is run using `python -m venv`


What `venv` does:

- It creates a **virtual environment**: a directory containing a Python interpreter and a separate location for installed packages.
- Packages installed in one environment do not normally affect other environments or the system Python.
- Virtual environments are **recommended for Python projects**.
- The environment is usually created inside the project directory.

Documentation: [Python — `venv`](https://docs.python.org/3/library/venv.html).

---


# Create an environment

General syntax:

```text
python -m venv ENV_DIR

# or

python -m venv ENV_DIR --prompt DISPLAY_NAME
```

- `-m venv` — runs the `venv` module.
- `ENV_DIR` — directory to create; it can be a relative or absolute path.
- `--prompt DISPLAY_NAME` — sets the name shown in the terminal after activation. It does **not** rename the directory.

>- `--upgrade-deps`- another useful option which updates `pip` to the latest available version from PyPI (requires internet access):

```powershell
python -m venv env --upgrade-deps
```
---


# Environment names and usage

### Environment directory names

| Name | Usage |
| :--- | :--- |
| `env` | Common; used in this course |
| `venv` | Common alternative |
| `.env` | Valid, but often used as the name of a configuration file |
| `.venv` | Common in editors and modern Python tools |


>- These are **conventions, not requirements**!
>- using the same directory name in every project makes commands and `.gitignore` rules consistent.


### `--prompt`
Shows a custom name in the terminal instead of the directory name (`env`).

For example, in two **separate PowerShell terminals**:

**Project 1**

```powershell
PS ...\proj1> python -m venv env --prompt imagery
PS ...\proj1> .\env\Scripts\activate
(imagery) PS ...\proj1>
```

**Project 2**

```powershell
PS ...\proj2> python -m venv env --prompt terrain
PS ...\proj2> .\env\Scripts\activate
(terrain) PS ...\proj2>
```


### One project — one environment

**Recommended:** create a separate environment for each project. Different projects can then use different package
versions without conflicts.

**Possible:** several projects can use the same environment, including one stored outside their directories.
This is sometimes convenient, but changing its packages may affect every project that uses it.

---



# What `venv` creates

**Windows** (main files and directories):

```text
proj1/
└── env/
    ├── pyvenv.cfg
    ├── .gitignore
    ├── Scripts/
    │   ├── python.exe
    │   ├── pip.exe
    │   └── Activate.ps1
    └── Lib/
        └── site-packages/
```

**Linux / macOS**:

```text
proj1/
└── env/
    ├── pyvenv.cfg
    ├── .gitignore
    ├── bin/
    │   ├── python
    │   ├── pip
    │   └── activate
    └── lib/
        └── python3.X/
            └── site-packages/
```

- `pyvenv.cfg` — environment configuration, including the location of the base Python installation.
- `python` / `python.exe` — the interpreter used in this environment.
- `activate` — changes the current terminal session to use the environment's Python and tools.
- `site-packages` — directory where Python packages installed in this environment are stored (for example, by `pip`). Do not edit it manually.
- `.gitignore` — created automatically by `venv` in Python 3.13 and newer to keep the environment out of Git.

## Activate — Windows PowerShell 7

From the project directory:

```powershell
cd ~/python_course/projects/proj1
.\env\Scripts\activate
python --version
python -m pip --version
```

The prompt normally starts with `(env)` or the name chosen with `--prompt`.

If PowerShell blocks activation because of its execution policy, ask the instructor before changing the policy. Do not run PowerShell as administrator.

## Activate — Linux / macOS

From the project directory (Bash or Zsh):

```bash
cd ~/python_course/projects/proj1
source env/bin/activate
python --version
python -m pip --version
```

On Debian/Ubuntu, `python3 -m venv env` is common; the distribution may require the `python3-venv` package.

## Deactivate

On Windows, Linux and macOS:

```text
deactivate
```

Activation affects only the **current terminal session**. Activate the environment again when opening a new terminal.

---


# Rules

- Use `python -m pip` after activating the correct environment.
- Do not commit environment directories to Git. For this course, add `env/` to the project's `.gitignore` (Python 3.13+ also creates `env/.gitignore`).
- Do not copy an environment between computers or move it to another location. Recreate it from the project's dependencies.

---


# Alternatives

| Tool | Main difference from `venv` |
| :--- | :--- |
| [`virtualenv`](https://virtualenv.pypa.io/) | Separate tool for creating virtual environments; offers more options |
| [`uv`](https://docs.astral.sh/uv/) | Fast tool for managing Python versions, environments and packages; uses `.venv` by default in projects |
| [`Conda`](https://docs.conda.io/) / [`Mamba`](https://mamba.readthedocs.io/) | Manage environments and Python **and non-Python** packages; widely used in scientific computing |
| [`Poetry`](https://python-poetry.org/docs/) | Manages project dependencies, lockfiles and packaging; also creates virtual environments |

For this course, use Python's built-in `venv`.
