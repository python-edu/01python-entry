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

- `freeze` — saves installed package versions, including dependencies.
- Keep `requirements.txt` in Git; do not commit `env/`.

```bash
python -m pip freeze > requirements.txt
```

Install the recorded versions in an environment:

- `-r`, `--requirement` — install packages listed in a file.

```bash
python -m pip install --requirement requirements.txt
# or
python -m pip install -r requirements.txt
```

---

# Alternatives

| Tool | Main difference from `pip` |
| :--- | :--- |
| [`uv`](https://docs.astral.sh/uv/) | Fast package installer; also manages Python versions, environments and projects |
| [`Conda`](https://docs.conda.io/) / [`Mamba`](https://mamba.readthedocs.io/) | Manage environments and Python and non-Python packages; Mamba is a faster Conda-compatible implementation |
| [`Poetry`](https://python-poetry.org/docs/) | Manages project dependencies, lockfiles, environments and packaging |

For this course, use `python -m pip`.
