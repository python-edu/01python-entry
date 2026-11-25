# pipx — Python command-line applications

Use **pip** for project libraries and **pipx** for standalone Python command-line applications. pipx creates isolated application environments.

## Install pipx

Windows (prepared account, PowerShell 7):

```powershell
python -m pip install --user pipx
python -m pipx ensurepath
```

Close and reopen PowerShell after changing `PATH`, then check:

```powershell
pipx --version
```

On Debian/Ubuntu, prefer the distribution's `pipx` package (often `sudo apt install pipx` on a system you manage). On macOS, Homebrew can install it with `brew install pipx`.

## Install an application

```powershell
pipx install ruff
ruff --version
pipx list
```

`ruff` is now available as a terminal command independently of the active project environment.

## Maintain installed applications

```powershell
pipx upgrade ruff
pipx uninstall ruff
```

For the next exercise, reinstall `ruff` if you removed it.

## Check

Compare `python -m pip list` inside `proj1/env` with `pipx list`. These commands list packages in different environments.

Documentation: [pipx](https://pipx.pypa.io/stable/).
