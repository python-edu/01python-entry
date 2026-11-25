# Python REPL

## Python and the interpreter

- **Python** is a programming language used for calculations, data analysis, automation, and writing programs.
- **`python.exe`** is the Python interpreter on Windows: a program that reads and executes Python code. In PowerShell, run it with the command `python` (the `.exe` extension can be omitted).
- The interpreter can work **interactively** or execute instructions saved in a **`.py` file**.
- The interpreter provides command-line help with `-h` or `--help`.

In PowerShell 7:

```powershell
python --version     # Check the installed version.
python -h            # Show interpreter command-line options.
python --help        # Same as -h.
python               # Start interactive Python.
```

## REPL — interactive Python

**REPL** stands for **Read–Evaluate–Print Loop**:

1. **Read** an expression entered by the user.
2. **Evaluate** it.
3. **Print** the result.
4. **Loop** — wait for the next expression.

After starting `python`, the prompt changes from PowerShell (`PS ...>`) to Python (`>>>`). Type only the expression, not the `>>>` prompt. Press **Enter** to evaluate it.

```python
>>> 6 + 4
10
>>> 9 * 3
27
```

## Arithmetic operators

### Addition — `+`

Adds two numbers.

```python
>>> 18 + 7
25
```

### Subtraction — `-`

Subtracts the second number from the first.

```python
>>> 42 - 19
23
```

### Multiplication — `*`

Multiplies two numbers.

```python
>>> 12 * 8
96
```

### Division — `/`

Divides and returns a floating-point result, even when the result is a whole number.

```python
>>> 19 / 4
4.75
>>> 20 / 4
5.0
```

### Floor division — `//`

Divides and rounds the result down to a whole number (for positive integers, the number of complete groups).

```python
>>> 19 // 4
4
```

### Modulo (remainder) — `%`

Returns the remainder after division.

```python
>>> 19 % 4
3
```

### Exponentiation — `**`

Raises a number to a power.

```python
>>> 3 ** 4
81
```

### Parentheses — `()`

Control the order of calculations. Without parentheses, multiplication is performed before addition.

```python
>>> 8 + 4 * 3
20
>>> (8 + 4) * 3
36
```

## Worked examples

### 1. Energy balance at a monitoring station

A station has **two 55 W solar panels**. They generate electricity for **4 h 15 min**, and **80%** of the generated energy can be used. The station consumes **28 W** for **12 h**. Calculate the available energy, consumption, remaining energy, and the surplus as a percentage of consumption.

```python
>>> # Convert 4 h 15 min into hours.
>>> 4 + 15 / 60
4.25
>>> # Usable solar energy in watt-hours (Wh).
>>> 2 * 55 * 4.25 * 0.8
374.0
>>> # Energy consumed in 12 hours (Wh).
>>> 28 * 12
336
>>> # Energy remaining (Wh).
>>> 374 - 336
38
>>> # Surplus relative to consumption (%).
>>> 38 / 336 * 100
11.30952380952381
```

### 2. Planning flight lines for an aerial survey

A survey area is **1020 m wide**. One flight line covers a strip **120 m wide**, and adjacent strips overlap by **30 m**. Flying one line takes **6 min**; turning between lines takes **2 min**. Calculate the number of flight lines and the total survey time in hours and minutes.

```python
>>> # New area covered by each additional line (m).
>>> 120 - 30
90
>>> # Additional lines after the first line.
>>> (1020 - 120) // 90
10
>>> # Total flight lines.
>>> 10 + 1
11
>>> # Flight time plus turns, in minutes.
>>> 11 * 6 + (11 - 1) * 2
86
>>> # Full hours.
>>> 86 // 60
1
>>> # Remaining minutes.
>>> 86 % 60
26
```

## Errors and exit

Python displays an error if an expression cannot be evaluated:

```python
>>> 8 / 0
Traceback (most recent call last):
  ...
ZeroDivisionError: division by zero
```

To leave the REPL and return to PowerShell:

```python
>>> exit
```

Exercises: [Arithmetic operators](https://github.com/python-edu/exercises/blob/main/01_arithmetic_exercises.md).

Documentation: [Python tutorial — Using Python as a calculator](https://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator).
