# Python installation

- [Windows 10 / 11](#windows-10--11)
- [macOS](#macos)
- [Linux (Debian / Ubuntu)](#linux-debian--ubuntu)

## Choosing a Python version

- Use Python 3 (preferably version 3.11 or newer).
- For beginners, differences between recent Python 3 versions are usually not important.
- **Python 3.14** is used in this course. It is a stable, supported release with broad support from scientific Python libraries.
- **Python 3.15** is the newer stable series (November 2026). New major releases may require time for third-party libraries
  to provide compatible versions.

---

# Windows 10 / 11

- Sign in to the course account `rs_lab`.
- Installation is the same on Windows 10 and 11; some Windows settings are in different locations.

### 1. Install Python install manager

1. Open [Python downloads for Windows](https://www.python.org/downloads/windows/) in your web browser.
2. Find **Python install manager** (not a specific Python release).
3. Download **Installer (MSIX)**.
4. Open **Downloads** and double-click the downloaded `.msix` file.
5. In the Windows installer window, click **Install**.

A terminal window may open for initial configuration. You may see these or similar questions (their wording and order can vary):

| If asked about… | What to do |
| :--- | :--- |
| Adding the Python commands directory to your user `PATH` | Choose **Yes** (`y` + Enter). |
| Installing CPython immediately | Choose **No**. We will install version `3.14` explicitly. |
| Enabling Windows long paths | Choose **Yes**. If administrator permission is required, ask the instructor. |
| Opening online help | Choose **No**. |

Close the configuration terminal when finished. If no questions appear, continue.

> The **Python install manager** is not the Python interpreter. It downloads and manages Python runtimes (interpreters).

### 2. Install Python 3.14

> Close terminal and open a **new PowerShell 7** window. Type:

```powershell
pymanager install 3.14
```

- `pymanager` runs the Python install manager.
- `install` asks it to install a Python runtime.
- `3.14` selects the course version.

If configuration questions appear instead of the download, answer them, close PowerShell, open it again and repeat the command.

### 3. Check the installation

In PowerShell 7, type:

```powershell
python --version
```

> Expected result: `Python 3.14.x` (`x` is the installed patch version).

### `pymanager`, `py`, `python`

| Command | Purpose |
| :--- | :--- |
| `pymanager` | Installs, lists and manages Python versions |
| `py` | Another entry point for the manager; also runs Python and can select versions |
| `python` | Runs the default Python interpreter and Python programs |

>- In PowerShell, `Tab` can complete command names.
>- You may see `.exe` added to a name: `.exe` is the extension of a Windows
executable. Both `python` and `python.exe` work; Windows can find the executable without typing `.exe`.
>- We use `pymanager` for installation and troubleshooting. From this point on, use `python` in Windows exercises.

---

# Windows troubleshooting

## `python` command not found

### 1. Restart PowerShell

1. Close all PowerShell windows.
2. Open **PowerShell 7** again.
3. Run `python --version`.

### 2. Check app execution aliases

Open Windows **Settings** using **Win + I**. Then follow the path for your system:

- **Windows 11:** `Settings > Apps > Advanced app settings > App execution aliases`
- **Windows 10:** `Settings > Apps > Apps & features > App execution aliases` (or **Manage app execution aliases**)

On the **App execution aliases** page:

1. Scroll through the list to find the Python entries.
2. Find **Python (default)** — `python.exe`. Set its switch to **On**.
3. Find **Python install manager** — `pymanager.exe`. Set its switch to **On**.
4. If a required switch is already **On**, turn it **Off**, then **On** again.
5. Close Settings, reopen PowerShell 7 and run `python --version`.

![Example of the Windows 11 App execution aliases settings](https://i.sstatic.net/BHcocFvz.png)

>- example screenshot: the Python (default) switch is `Off` in the picture!
>- for this course it should be `On`. Source: [Super User discussion](https://superuser.com/questions/1935718/how-can-i-set-the-default-python-version-that-gets-launched-when-typing-python3).*

### 3. Check your user `Path`

If `python` is still not found:

1. Press **Win + R**, type `sysdm.cpl` and press **Enter**.
2. In **System Properties**, open the **Advanced** tab and click **Environment Variables…**.
3. In **User variables for rs_lab** (the upper part of the window), select **Path** and click **Edit…**. Do not change **System variables**.
4. In the window **Edit environment variable**, look for this entry as one of the rows:

   ```text
   %USERPROFILE%\AppData\Local\Microsoft\WindowsApps
   ```

5. If it is already in the list, leave it unchanged. If it is missing, click **New** and paste the path above into the new row. **Do not enter it in PowerShell.**
6. Click **OK** to close each settings window.
7. Close PowerShell 7, reopen it and run `python --version`.

## Python version is not 3.14

In PowerShell 7, type:

```powershell
pymanager list
```

Check whether Python `3.14` is listed. If not, run `pymanager install 3.14`. If another installed version still opens, set the preferred version for your account:

```powershell
setx PYTHON_MANAGER_DEFAULT 3.14
```

Close PowerShell 7, reopen it and check `python --version`. If an unrelated older installation still takes precedence, ask the instructor to inspect it rather than changing the system PATH.

Documentation: [Python on Windows — installation and troubleshooting](https://docs.python.org/3/using/windows.html).

---

# Linux (Debian / Ubuntu)

Open the system terminal and check:

```bash
python3 --version
```

`python3` is the standard command on Debian and Ubuntu. `python` may also work, but is not guaranteed to be installed as a command on every system. The `python-is-python3` package can provide it.

Use the system's Python 3 installation. If Python is missing, the operating-system installation must be prepared before the exercises.

Documentation: [Debian Python](https://wiki.debian.org/Python).

---

# macOS

With Homebrew available in the prepared account:

```bash
brew install python@3.14
python3.14 --version
```

The versioned command selects Homebrew's Python `3.14`, not the interpreter provided by macOS. If Homebrew is already set up, the commands do not require `sudo`.

Documentation: [Homebrew and Python](https://docs.brew.sh/Homebrew-and-Python).
