# Installing packages with `pip`

>- `pip` is a **Python package and command-line tool**. It is not part of the standard library.
>- It installs, upgrades and removes Python packages and their dependencies.
>- By default, it downloads packages from [PyPI — Python Package Index](https://pypi.org/).
>- It is the **reference package installer** for Python. It is included with python.org installers and, by default, in environments created with `venv`.
>- Use `python -m pip` to run `pip` with the selected Python interpreter.

Documentation: [pip](https://pip.pypa.io/en/stable/).

---

# Basic commands

In `proj1`, with `env` active:

- `-V`, `--version` — pip version and installation location.
- `list` — installed packages.

```bash
python -m pip --version
# or
python -m pip -V

python -m pip list
```

## Install `ipython`

- `install` — installs the package and required dependencies.
- `==` — installs the specified version.
- `show` — package details, including its installation location.
- `check` — checks installed package dependencies for conflicts.

```bash
python -m pip install ipython
# or: install a specific version
python -m pip install "ipython==9.5.0"

python -m pip show ipython
python -m pip list
python -m pip check
```

## Other commands

- `-U`, `--upgrade` — upgrade IPython.
- `uninstall` — remove IPython.
- `-h`, `--help` — show pip commands and options.

```bash
python -m pip install --upgrade ipython
# or
python -m pip install -U ipython

python -m pip uninstall ipython

python -m pip --help
# or
python -m pip -h
```

## Record dependencies

### Manual `requirements.txt`

- Lists packages required by the project.
- Versions are optional. Without them, `pip` selects compatible versions at installation time.
- Add only the packages you choose to use; `pip` installs their dependencies.

Create `requirements.txt` in `proj1`:

```bash
echo "ipython" > requirements.txt
```

File contents:

```text
ipython
```

### Installed packages

- `freeze` — lists installed packages and their exact versions, including dependencies.
- Save the complete list separately. Do not overwrite the manual `requirements.txt`.

```bash
python -m pip freeze > requirements_frozen.txt
```

Keep dependency files in Git. Do not commit `env/`.

### Install from `requirements.txt`

- `-r`, `--requirement` — install the packages listed in a requirements file.

```bash
python -m pip install --requirement requirements.txt
# or
python -m pip install -r requirements.txt
```

## Create an environment from `requirements.txt`

`venv` creates the environment. `pip` installs its packages from the file.

**Windows — PowerShell 7** (new `proj2`):

```powershell
cd ~/python_course/projects
mkdir proj2
cd proj2
python -m venv env --upgrade-deps
.\env\Scripts\activate
python -m pip install --requirement ../proj1/requirements.txt
# or
python -m pip install -r ../proj1/requirements.txt
```

**Linux / macOS** (Bash / Zsh):

```bash
cd ~/python_course/projects
mkdir proj2
cd proj2
python3 -m venv env --upgrade-deps
source env/bin/activate
python -m pip install --requirement ../proj1/requirements.txt
# or
python -m pip install -r ../proj1/requirements.txt
```

On macOS, use `python3.14` to select the course interpreter when required.

Verify the installation:

```bash
python -m pip show ipython
python -m pip check
```

---

# Alternatives

| Tool | Main difference from `pip` |
| :--- | :--- |
| [`uv`](https://docs.astral.sh/uv/) | Fast package installer; also manages Python versions, environments and projects |
| [`Conda`](https://docs.conda.io/) / [`Mamba`](https://mamba.readthedocs.io/) | Manage environments and Python and non-Python packages; Mamba is a faster Conda-compatible implementation |
| [`Poetry`](https://python-poetry.org/docs/) | Manages project dependencies, lockfiles, environments and packaging |

For this course, use `python -m pip`.
