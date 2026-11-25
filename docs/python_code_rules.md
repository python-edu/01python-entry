# Python Code Rules

> - **Requirement** — mandatory Python language syntax.
> - **Convention** — recommended coding style (PEP 8 or PEP 257); valid Python may use another style.

# Contents

- [Whitespace in calculations](#whitespace-in-calculations)
- [Variables, constants, and functions](#variables-constants-and-functions)
- [Whitespace in function calls and collections](#whitespace-in-function-calls-and-collections)
- [Line length](#line-length)
- [Indentation](#indentation)
- [Blank lines](#blank-lines)
- [Comments and docstrings](#comments-and-docstrings)
- [Classes](#classes)
- [Modules](#modules)
- [Imports](#imports)

# Whitespace in calculations

### 1. Spaces around operators

**Rule:** Use one space on both sides of assignment and comparison operators. Usually use spaces around arithmetic operators; keep spacing consistent with operator precedence.  
**Type:** Convention  
**Documentation:** [PEP 8: Other Recommendations](https://peps.python.org/pep-0008/#other-recommendations)

**Good:**

```python
x = 2 + 3
result = x * 4
```

**Bad:**

```python
x=2+3
result=x*4
```

### 2. Trailing whitespace

**Rule:** Remove spaces and tabs at the ends of lines.  
**Type:** Convention  
**Documentation:** [PEP 8: Other Recommendations](https://peps.python.org/pep-0008/#other-recommendations)

---


# Variables, constants, and functions

| Rule | Good | Bad | Type | Documentation |
|---|---|---|---|---|
| Start a name with a letter or `_`; digits may follow. | `band_2` | `2_band` | Requirement | [Python: Names](https://docs.python.org/3.14/reference/lexical_analysis.html#names-identifiers-and-keywords) |
| Do not use spaces, hyphens, or reserved keywords in identifiers. | `pixel_size`, `class_name` | `pixel size`, `pixel-size`, `class` | Requirement | [Python: Names](https://docs.python.org/3.14/reference/lexical_analysis.html#names-identifiers-and-keywords), [Keywords](https://docs.python.org/3.14/reference/lexical_analysis.html#keywords) |
| Names are case-sensitive. | `value = 1; print(value)` | `value = 1; print(Value)` | Requirement | [Python: Names](https://docs.python.org/3.14/reference/lexical_analysis.html#names-identifiers-and-keywords) |
| Use lowercase names with `_` for variables and functions. | `pixel_size`, `calculate_area()` | `pixelSize`, `CalculateArea()` | Convention | [PEP 8: Function and Variable Names](https://peps.python.org/pep-0008/#function-and-variable-names) |
| Use uppercase names with `_` for constants. | `MAX_ITERATIONS` | `maxIterations` | Convention | [PEP 8: Constants](https://peps.python.org/pep-0008/#constants) |
| Avoid single-letter names `l`, `O`, `I`. | `index` | `I` | Convention | [PEP 8: Names to Avoid](https://peps.python.org/pep-0008/#names-to-avoid) |
| For a function argument conflicting with a keyword, append `_`. | `def f(class_): pass` | `def f(clss): pass` | Convention | [PEP 8: Function and Method Arguments](https://peps.python.org/pep-0008/#function-and-method-arguments) |


---


# Whitespace in function calls and collections

### 1. Commas and parentheses

**Rule:** Put a space after a comma, not before it. Do not add spaces immediately inside parentheses or between a function name and `(`.  
**Type:** Convention  
**Documentation:** [PEP 8: Whitespace in Expressions and Statements](https://peps.python.org/pep-0008/#whitespace-in-expressions-and-statements)

**Good:**

```python
print(10, 20)
```

**Bad:**

```python
print ( 10 ,20 )
```

### 2. Spaces in lists and dictionaries

**Rule:** Do not add spaces just inside `[]` or `{}`. Put a space after commas and after the colon in dictionary entries.  
**Type:** Convention  
**Documentation:** [PEP 8: Whitespace in Expressions and Statements](https://peps.python.org/pep-0008/#whitespace-in-expressions-and-statements)

**Good:**

```python
values = [10, 20, 30]
record = {"x": 10, "y": 20}
```

**Bad:**

```python
values = [ 10,20,30 ]
record = { "x":10,"y":20 }
```

---


# Line length

### 1. Maximum code line length

**Rule:** Keep code lines at 79 characters or fewer. A project may adopt up to 99 characters by agreement.  
**Type:** Convention  
**Documentation:** [PEP 8: Maximum Line Length](https://peps.python.org/pep-0008/#maximum-line-length)

### 2. Break long expressions

**Rule:** Prefer splitting long expressions inside `()`, `[]`, or `{}` instead of using `\` at the end of a line.  
**Type:** Convention  
**Documentation:** [PEP 8: Maximum Line Length](https://peps.python.org/pep-0008/#maximum-line-length)

**Good:**

```python
total = (
    100 + 200 + 300
    + 400 + 500
)
```

**Less preferred:**

```python
total = 100 + 200 + 300 \
    + 400 + 500
```

### 3. Comments and docstrings

**Rule:** Keep comment and docstring lines at 72 characters or fewer.  
**Type:** Convention  
**Documentation:** [PEP 8: Maximum Line Length](https://peps.python.org/pep-0008/#maximum-line-length)

---


# Indentation

### 1. Indent the body of a compound statement

**Rule:** Indent the statements inside `if`, `for`, `while`, `def`, etc.  
**Type:** Requirement  
**Documentation:** [Python: Indentation](https://docs.python.org/3.14/reference/lexical_analysis.html#indentation), [Compound Statements](https://docs.python.org/3.14/reference/compound_stmts.html)

**Good:**

```python
if x > 0:
    print(x)
```

**Bad:**

```python
if x > 0:
print(x)
```

### 2. Keep the same indentation level within a block

**Rule:** Statements in the same block must start at the same indentation level.  
**Type:** Requirement  
**Documentation:** [Python: Indentation](https://docs.python.org/3.14/reference/lexical_analysis.html#indentation)

**Good:**

```python
if x > 0:
    print(x)
    print(x + 1)
```

**Bad:**

```python
if x > 0:
    print(x)
      print(x + 1)
```

### 3. Do not mix tabs and spaces ambiguously

**Rule:** Mixing tabs and spaces so that the indentation depends on tab width raises `TabError`.  
**Type:** Requirement  
**Documentation:** [Python: Indentation](https://docs.python.org/3.14/reference/lexical_analysis.html#indentation)

### 4. Use four spaces per indentation level

**Rule:** Use 4 spaces for each level of block indentation.  
**Type:** Convention  
**Documentation:** [PEP 8: Indentation](https://peps.python.org/pep-0008/#indentation)

### 5. Prefer spaces over tabs

**Rule:** Use spaces. Use tabs only to match an existing tab-indented project.  
**Type:** Convention  
**Documentation:** [PEP 8: Tabs or Spaces?](https://peps.python.org/pep-0008/#tabs-or-spaces)

### 6. Indent long expressions consistently

**Rule:** Align continued elements with the first element, or start them on a new line with extra indentation (*hanging indent*).  
**Type:** Convention  
**Documentation:** [PEP 8: Indentation](https://peps.python.org/pep-0008/#indentation)

**Good — aligned arguments:**

```python
result = calculate_area(width, height,
                        scale, offset)
```

**Good — hanging indent:**

```python
result = calculate_area(
    width, height,
    scale, offset
)
```

**Bad:**

```python
result = calculate_area(width, height,
    scale, offset)
```

## Blank lines

### 1. Top-level functions and classes

**Rule:** Use two blank lines between top-level function and class definitions.  
**Type:** Convention  
**Documentation:** [PEP 8: Blank Lines](https://peps.python.org/pep-0008/#blank-lines)

### 2. Methods inside a class

**Rule:** Separate method definitions with one blank line.  
**Type:** Convention  
**Documentation:** [PEP 8: Blank Lines](https://peps.python.org/pep-0008/#blank-lines)

### 3. Inside a function

**Rule:** Use blank lines sparingly to separate logical parts of a function.  
**Type:** Convention  
**Documentation:** [PEP 8: Blank Lines](https://peps.python.org/pep-0008/#blank-lines)

## Comments and docstrings

### 1. Comment syntax

**Rule:** `#` starts a comment outside a string. The comment continues to the end of the line.  
**Type:** Requirement  
**Documentation:** [Python: Comments](https://docs.python.org/3.14/reference/lexical_analysis.html#comments)

**Example:**

```python
# Convert metres to kilometres.
distance_km = distance_m / 1000
```

### 2. Comment style

**Rule:** Start a comment with `# ` (hash and a space). Keep comments accurate and useful.  
**Type:** Convention  
**Documentation:** [PEP 8: Comments](https://peps.python.org/pep-0008/#comments), [Block Comments](https://peps.python.org/pep-0008/#block-comments)

**Good:**

```python
# Use the pixel size in metres.
pixel_area = pixel_size**2
```

**Bad:**

```python
#pixel size
pixel_area = pixel_size**2
```

### 3. Inline comments

**Rule:** Use inline comments sparingly. Separate them from code with at least two spaces, then `# `.  
**Type:** Convention  
**Documentation:** [PEP 8: Inline Comments](https://peps.python.org/pep-0008/#inline-comments)

### 4. Function docstrings

**Rule:** Document public functions with a docstring as the first statement. Use triple double quotes (`"""`).  
**Type:** Convention  
**Documentation:** [PEP 8: Documentation Strings](https://peps.python.org/pep-0008/#documentation-strings), [PEP 257: What is a Docstring?](https://peps.python.org/pep-0257/#what-is-a-docstring)

**Good:**

```python
def area(width, height):
    """Return the area of a rectangle."""
    return width * height
```

**Bad — ordinary comment instead of a docstring:**

```python
def area(width, height):
    # Return the area of a rectangle.
    return width * height
```

### 5. One-line docstrings

**Rule:** Write a short summary on one line with closing `"""` on the same line.  
**Type:** Convention  
**Documentation:** [PEP 257: One-line Docstrings](https://peps.python.org/pep-0257/#one-line-docstrings)

## Classes

| Rule | Good | Bad | Type | Documentation |
|---|---|---|---|---|
| Class names must be valid identifiers. | `class SatelliteImage: pass` | `class 2Image: pass` | Requirement | [Python: Names](https://docs.python.org/3.14/reference/lexical_analysis.html#names-identifiers-and-keywords) |
| Use `CapWords` (PascalCase). | `SatelliteImage` | `satellite_image` | Convention | [PEP 8: Class Names](https://peps.python.org/pep-0008/#class-names) |
| Use the suffix `Error` for exceptions representing errors. | `RasterReadError` | `RasterReadProblem` | Convention | [PEP 8: Exception Names](https://peps.python.org/pep-0008/#exception-names) |

## Modules

| Rule | Good | Bad | Type | Documentation |
|---|---|---|---|---|
| Names written directly in `import` statements must be valid identifiers. | `import image_tools` | `import image-tools` | Requirement | [Python: Import Statement](https://docs.python.org/3.14/reference/simple_stmts.html#the-import-statement), [Names](https://docs.python.org/3.14/reference/lexical_analysis.html#names-identifiers-and-keywords) |
| Use short, lowercase module names; `_` is allowed. | `raster.py`, `image_tools.py` | `ImageTools.py` | Convention | [PEP 8: Package and Module Names](https://peps.python.org/pep-0008/#package-and-module-names) |

## Imports

### 1. Put imports at the beginning of a module

**Rule:** Put imports after the module comments/docstring and before ordinary variables or functions.  
**Type:** Convention  
**Documentation:** [PEP 8: Imports](https://peps.python.org/pep-0008/#imports)

**Good:**

```python
import math

radius = 5
area = math.pi * radius**2
```

**Bad:**

```python
radius = 5
import math
area = math.pi * radius**2
```

### 2. Separate imports

**Rule:** Import separate modules on separate lines.  
**Type:** Convention  
**Documentation:** [PEP 8: Imports](https://peps.python.org/pep-0008/#imports)

**Good:**

```python
import math
import os
```

**Bad:**

```python
import math, os
```

### 3. Group imports

**Rule:** Order imports: standard library, third-party packages, local modules. Separate groups with blank lines.  
**Type:** Convention  
**Documentation:** [PEP 8: Imports](https://peps.python.org/pep-0008/#imports)

**Example:**

```python
import math

import numpy as np

import image_tools
```
