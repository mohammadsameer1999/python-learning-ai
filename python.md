# Python Compilation and Execution (Simple Notes)

## How Python Works
- Python programs are written in `.py` files
- The Python interpreter first compiles the source code into **bytecode**
- The bytecode is executed by the **Python Virtual Machine (PVM)**

![Python Compilation Overview](images/python-compilation-overview.png)
*Overall Python compilation and execution process*

---

## Step 1: Compilation to Bytecode
- `.py` files are compiled into **bytecode**
- Bytecode is:
  - Low-level
  - Platform-independent
- Bytecode runs faster than source code

```text
.py → Bytecode
```

![Source to Bytecode](images/source-to-bytecode.png)
*Conversion of Python source code to bytecode*

## Step 2: Bytecode Files (.pyc)

Compiled bytecode is stored in `.pyc` files

`.pyc` files are:
- Not human-readable
- Frozen binaries
- Stored inside the `__pycache__` directory (internal use)

**Example:**
```
__pycache__/
  hello_sameer.cpython-314.pyc
```

![Pycache Directory](images/pycache-structure.png)
*Structure of __pycache__ directory with .pyc files*

## Step 3: __pycache__ Directory

Used internally by Python

Stores compiled bytecode

Bytecode is regenerated when:
- Source code changes
- Python version changes

Python checks timestamps and metadata to decide whether recompilation is required

## Step 4: When .pyc Files Are Created

`.pyc` files are created only for **imported modules**

`.pyc` files are **not** created for top-level scripts

**Example:**
```python
import hello_sameer   # .pyc file is created
```
```bash
python main.py        # no .pyc file for main.py
```

![Import vs Script Execution](images/import-vs-script.png)
*Difference between importing modules and running scripts*

## Execution Flow (Summary)
```
.py → Bytecode (.pyc) → Python Virtual Machine → Program Output
```

![Complete Execution Flow](images/execution-flow.png)
*Complete Python code execution flow diagram*
