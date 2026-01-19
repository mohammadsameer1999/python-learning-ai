# Python Compilation and Execution (Simple Notes)

## How Python Works
- Python programs are written in `.py` files
- The Python interpreter first compiles the source code into **bytecode**
- The bytecode is executed by the **Python Virtual Machine (PVM)**

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Source Code   │───▶│    Bytecode     │───▶│  Python VM      │
│   (.py file)    │    │   (.pyc file)   │    │  (Execution)    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```
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

```
hello.py               Compiler               hello.pyc
┌──────────────┐       ┌────────┐       ┌─────────────────┐
│ def hello(): │      │ Python │      │ Bytecode:       │
│   print("Hi")│ ────▶│ Parser │────▶ │ LOAD_GLOBAL     │
│              │      │ & AST  │      │ CALL_FUNCTION   │
└──────────────┘       └────────┘       └─────────────────┘
```
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

```
Project Directory
│
├── main.py
├── hello_sameer.py
│
└── __pycache__/
    ├── hello_sameer.cpython-314.pyc
    ├── utils.cpython-314.pyc
    └── config.cpython-314.pyc
```
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

```
Import Module:                    Run Script:
┌─────────────────┐              ┌─────────────────┐
│ import module   │              │ python script.py│
│                 │              │                 │
│ ✓ Creates .pyc  │              │ ✗ No .pyc file │
│ ✓ Faster reload │              │ ✗ Compile every │
│                 │              │   time          │
└─────────────────┘              └─────────────────┘
```
*Difference between importing modules and running scripts*

## Execution Flow (Summary)
```
.py → Bytecode (.pyc) → Python Virtual Machine → Program Output
```

```
Complete Python Execution Flow:

Source Code (.py)
       │
       ▼
┌─────────────────┐
│ Lexical Analysis│ ──┐
└─────────────────┘   │
       │              │
       ▼              │ Python
┌─────────────────┐   │ Compiler
│ Parsing (AST)   │ ──┤
└─────────────────┘   │
       │              │
       ▼              │
┌─────────────────┐   │
│ Code Generation │ ──┘
└─────────────────┘
       │
       ▼
Bytecode (.pyc)
       │
       ▼
┌─────────────────┐
│ Python Virtual  │
│ Machine (PVM)   │
└─────────────────┘
       │
       ▼
Program Output
```
*Complete Python code execution flow diagram*


## Python Virtual Machine (PVM)
## Python (.py) → Bytecode (.pyc) → Python Virtual Machine → Machine Instructions
* Python = interpreted + bytecode-based language

* Not directly understood by the CPU

* code loop to iterate byte code
* Rum time Engine
* Also know as python interpreter
## Byte Code is not machine code

-- Python specific interpretatio
-> Cpython()standard implementation, Jython, Iron Python, StackLess, PyPy
