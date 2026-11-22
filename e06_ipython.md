# IPython

>- `IPython` is an enhanced interactive Python shell, installed as a Python package.
>- It uses the Python interpreter from the active `venv` when installed and started there. It has no separate interpreter.
>- It supports tab completion, editable command history and *magic commands* (`%`).
>- Documentation: [IPython tutorial](https://ipython.readthedocs.io/en/stable/interactive/tutorial.html).

---

## Start IPython

Open two terminal sessions, preferably as **tabs** in one window:

- **Windows Terminal (PowerShell 7):** `Ctrl+Shift+T` or `+` (select PowerShell 7).
- **Linux (GNOME Terminal):** `Ctrl+Shift+T`.
- **macOS (Terminal):** `Cmd+T`.

Use these names throughout the tutorial:

- **IPython terminal** — run IPython and solve tasks.
- **History terminal** — save files and use Git.

In the **IPython terminal**, open `proj1` and activate its environment.

**Windows — PowerShell 7:**

```powershell
cd ~/python_course/projects/proj1
.\env\Scripts\activate
ipython
```

**Linux / macOS — Bash or Zsh:**

```bash
cd ~/python_course/projects/proj1
source env/bin/activate
ipython
```

- `In [1]:` — input prompt.
- `Out[1]:` — result of an expression.
- `exit` — return to the terminal.

## Work in IPython

- **Tab** — complete variable and command names.
- **↑ / ↓** — recall earlier inputs; edit and press **Enter** to run them again.
- `?` — display help for an object (e.g. `round?`).
- `%pwd` — show the current directory.

Variables, reassignment, numeric types and conversions:

```ipython
In [1]: sample_count = 12
In [2]: sample_count
Out[2]: 12
In [3]: type(sample_count)
Out[3]: int
In [4]: sample_count += 3
In [5]: sample_count
Out[5]: 15
In [6]: average = sample_count / 4
In [7]: average
Out[7]: 3.75
In [8]: type(average)
Out[8]: float
In [9]: round(average, 1)
Out[9]: 3.8
```

---

## Document and select history

- Start each task with `# project/task — title`.
- Use `#` comments to describe calculations and results.
- Enter expressions to display their values.
- Save only the inputs belonging to the task.

`%history` (`%hist`) displays the session history. `-n` adds input numbers. Find the first and last line of your task.

```ipython
%history -n
# or
%hist -n
```

`-l 30` displays the last 30 inputs. `-o` includes results.

```ipython
%history -n -o -l 30
# or
%hist -n -o -l 30
```

`-f FILE` saves a selected range (`START-END`) to a plain-text file. `-n` saves input numbers; `-o` saves results. The file is **overwritten** if it exists. `-y` skips overwrite confirmation.

```ipython
%history -n -o -y -f FILE START-END
# or
%hist -n -o -y -f FILE START-END
```

Use the line numbers from your own session. Each task can occupy only part of a longer history.

---

## Example 1 — Classification accuracy

A classification has **180 reference points**; **163** are classified correctly. Calculate the number of errors and Overall Accuracy (OA). Round OA to one decimal place.

- **Errors** — incorrectly classified reference points.
- **Overall Accuracy (OA)** — share of all reference points classified correctly. It measures overall agreement with the reference data.
- `N` — all reference points; `C` — correctly classified points.

$$
\mathrm{Errors} = N - C
$$

$$
\mathrm{OA}\;(\%) = \frac{C}{N} \times 100
$$

```ipython
In [21]: # proj1/task01 — classification accuracy
In [22]: reference_points = 180
In [23]: correct_points = 163
In [24]: # Incorrect classifications
In [25]: errors = reference_points - correct_points
In [26]: errors
Out[26]: 17
In [27]: # Overall Accuracy (OA), in percent
In [28]: oa_pct = correct_points / reference_points * 100
In [29]: round(oa_pct, 1)
Out[29]: 90.6
In [30]: type(oa_pct)
Out[30]: float
```

## Example 2 — Ground sampling distance

A camera has a **35 mm focal length** and a **3.45 µm pixel size**. Calculate Ground Sampling Distance (GSD) for flight heights of **120 m** and **90 m above ground**. Round to two decimal places.

- **Ground Sampling Distance (GSD)** — ground distance represented by one image pixel. Smaller GSD means finer ground detail.
- `H` — flight height above ground (m); `p` — sensor pixel size; `f` — focal length (mm).

Convert the sensor pixel size to millimetres:

$$
p_{\mathrm{mm}} = \frac{p_{\mathrm{\mu m}}}{1000}
$$

Calculate GSD in centimetres per pixel:

$$
\mathrm{GSD}\;(\mathrm{cm/pixel}) = \frac{H_{\mathrm{m}}\;p_{\mathrm{mm}}}{f_{\mathrm{mm}}} \times 100
$$

```ipython
In [31]: # proj1/task02 — ground sampling distance
In [32]: focal_length_mm = 35
In [33]: pixel_size_um = 3.45
In [34]: # Convert pixel size from µm to mm
In [35]: pixel_size_mm = pixel_size_um / 1000
In [36]: flight_height_m = 120
In [37]: # GSD in centimetres per pixel
In [38]: gsd_cm = flight_height_m * pixel_size_mm / focal_length_mm * 100
In [39]: round(gsd_cm, 2)
Out[39]: 1.18
In [40]: # Recalculate for 90 m above ground
In [41]: flight_height_m = 90
In [42]: gsd_cm = flight_height_m * pixel_size_mm / focal_length_mm * 100
In [43]: round(gsd_cm, 2)
Out[43]: 0.89
```

Input numbers are examples. Use the numbers from your own IPython session.

---

## Create the history repository

- Keep projects in `projects/`.
- Use **one Git repository**: `ipython-history/`.
- Create **one directory per project**.
- Keep **two files per project**: `history.txt` and `answers.txt`.
- Overwrite these files for each new task. Git stores their earlier versions.

```text
~/python_course/
├── projects/
│   ├── proj1/
│   ├── ...
│   └── proj_n/
└── ipython-history/              # Git repository
    ├── proj1/
    │   ├── history.txt           # student's work
    │   └── answers.txt           # instructor's answers
    ├── ...
    └── proj_n/
        ├── history.txt
        └── answers.txt
```

### 1. Initialize Git

Keep IPython open in the **IPython terminal**. In the **History terminal**:

```bash
cd ~/python_course
mkdir ipython-history
cd ipython-history
git init
mkdir proj1
```

### 2. Archive Task 01

In the **IPython terminal**, export only Task 01 (`21-30`) to `proj1/history.txt`:

```ipython
%history -n -o -y -f ../../ipython-history/proj1/history.txt 21-30
# or
%hist -n -o -y -f ../../ipython-history/proj1/history.txt 21-30
```

In the **History terminal**, inspect and commit the file. Identify the project and task in the message:

```bash
git status
git add proj1/history.txt
git commit -m "proj1/task01: classification accuracy"
# or
git commit --message "proj1/task01: classification accuracy"
```

Use **one** of the two commit commands.

### 3. Archive Task 02

In the **IPython terminal**, export Task 02 (`31-43`) to the **same file**. Its previous contents are replaced:

```ipython
%history -n -o -y -f ../../ipython-history/proj1/history.txt 31-43
# or
%hist -n -o -y -f ../../ipython-history/proj1/history.txt 31-43
```

In the **History terminal**, commit the new version:

```bash
git status
git add proj1/history.txt
git commit -m "proj1/task02: ground sampling distance"
# or
git commit --message "proj1/task02: ground sampling distance"
```

### 4. Archive instructor's answers

- If the instructor provides an answer file, save it as `proj1/answers.txt`.
- Replace the file for the next task.
- In the **History terminal**, commit each version. Include the task number in the message.

```bash
git add proj1/answers.txt
git commit -m "proj1/task01: answers"
# or
git commit --message "proj1/task01: answers"
```

Keep the repository **private**. Do not publish the instructor's answers.

---

## Show or submit work

### 1. Show a task on screen

In the **History terminal**, `git log` lists all commits, newest first:

```bash
git log
```

- `--oneline` — show short commit IDs and commit messages.
- `--` — separate Git options from file paths. It is **not an option**.
- `proj1/history.txt` — show only commits affecting this file, not all commits.

```bash
git log --oneline
# or
git log --oneline -- proj1/history.txt
```

Find the task by its commit message. Display the saved history:

```bash
git show COMMIT_ID:proj1/history.txt
```

For the instructor's answers, use `proj1/answers.txt` instead.

### 2. Generate a report file

In the **History terminal**, export the selected task to a **temporary text file outside the repository**:

```bash
git show COMMIT_ID:proj1/history.txt > ../proj1_task01_history.txt
```

Send `proj1_task01_history.txt` to the instructor. Then delete the temporary file:

```bash
rm ../proj1_task01_history.txt
```

No additional report is required.

Documentation: [IPython magic commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html).
