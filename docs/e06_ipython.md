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
- **Archive terminal** — save course work and use Git.

In the **IPython terminal**, open `proj1` and activate its environment.

**Windows — PowerShell 7:**

```powershell
cd ~/python_course/projects/proj1
~/python_course/projects/proj1/env/Scripts/activate
ipython
```

**Linux / macOS — Bash or Zsh:**

```bash
cd ~/python_course/projects/proj1
source ~/python_course/projects/proj1/env/bin/activate
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

- Start each task with `# lab2/taskNN — title`.
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
In [21]: # lab2/task01 — classification accuracy
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
In [31]: # lab2/task02 — ground sampling distance
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

## Archive your work

- `projects/` — Python projects and their environments.
- `student-work/` — your Git repository for **all course tasks**.
- `lab1/`, `lab2/`, ... — course topics, not Python projects.
- `results.txt` — text results from IPython, terminal or other tools.
- Overwrite `results.txt` for each new task. Git keeps earlier versions.
- Add other files when required by the task.

```text
~/python_course/
├── projects/
│   ├── proj1/
│   ├── proj2/
│   └── ...
└── student-work/                  # Git repository
    ├── lab1/
    │   ├── results.txt
    │   └── answers.txt
    ├── lab2/
    │   ├── results.txt
    │   ├── answers.txt
    │   ├── requirements.txt
    │   └── requirements_frozen.txt
    └── ...
```

### 1. Initialize Git

Keep IPython open in the **IPython terminal**. In the **Archive terminal**:

```bash
mkdir ~/python_course/student-work
mkdir ~/python_course/student-work/lab2
cd ~/python_course/student-work
git init
```

Git paths such as `lab2/results.txt` are relative to `~/python_course/student-work`.

### 2. Archive Task 01

In the **IPython terminal**, export Task 01 (`21-30`) to `lab2/results.txt`:

```ipython
%history -n -o -y -f ~/python_course/student-work/lab2/results.txt 21-30
# or
%hist -n -o -y -f ~/python_course/student-work/lab2/results.txt 21-30
```

In the **Archive terminal**, inspect and commit the file. Include the lab and task in the message:

```bash
cd ~/python_course/student-work
git status
git add lab2/results.txt
git commit -m "lab2/task01: classification accuracy"
# or
git commit --message "lab2/task01: classification accuracy"
```

Use **one** of the two commit commands.

### 3. Archive Task 02

In the **IPython terminal**, export Task 02 (`31-43`) to the **same file**. It replaces Task 01:

```ipython
%history -n -o -y -f ~/python_course/student-work/lab2/results.txt 31-43
# or
%hist -n -o -y -f ~/python_course/student-work/lab2/results.txt 31-43
```

In the **Archive terminal**, commit the new version:

```bash
cd ~/python_course/student-work
git status
git add lab2/results.txt
git commit -m "lab2/task02: ground sampling distance"
# or
git commit --message "lab2/task02: ground sampling distance"
```

### 4. Archive instructor's answers

- If the instructor provides an answer file, save it as `~/python_course/student-work/lab2/answers.txt`.
- Replace this file for each new task.
- In the **Archive terminal**, commit the file. Include the task number.

```bash
cd ~/python_course/student-work
git add lab2/answers.txt
git commit -m "lab2/task01: answers"
# or
git commit --message "lab2/task01: answers"
```

Keep the repository **private**. Do not publish the instructor's answers.

---

## Show or submit work

### 1. Show a task on screen

In the **Archive terminal**, `git log` lists all commits, newest first:

```bash
cd ~/python_course/student-work
git log
```

- `--oneline` — show short commit IDs and commit messages.
- `--` — separate Git options from file paths. It is **not an option**.
- `lab2/results.txt` — show only commits affecting this file, not all commits.

```bash
cd ~/python_course/student-work
git log --oneline
# or
git log --oneline -- lab2/results.txt
```

Find the task by its commit message. Display the saved history:

```bash
cd ~/python_course/student-work
git show COMMIT_ID:lab2/results.txt
```

For the instructor's answers, use `COMMIT_ID:lab2/answers.txt` instead.

   >- In `git show`, the path after `:` belongs to the commit.
   >- It is not a system path; do not use `~/` there.

### 2. Generate a report file

In the **Archive terminal**, export the selected task to a **temporary text file outside the repository**:

```bash
cd ~/python_course/student-work
git show COMMIT_ID:lab2/results.txt > ~/python_course/lab2_task01_results.txt
```

Send `~/python_course/lab2_task01_results.txt` to the instructor. Then delete the temporary file:

```bash
rm ~/python_course/lab2_task01_results.txt
```

No additional report is required.

Documentation: [IPython magic commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html).
