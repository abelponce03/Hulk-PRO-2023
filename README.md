# 💥 HULK Interpreter — Programming Language in C#

![Language](https://img.shields.io/badge/Language-C%23-239120?logo=csharp&logoColor=white)
![Framework](https://img.shields.io/badge/.NET-6.0-512BD4?logo=dotnet)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

A complete **interpreter for the HULK programming language**, implemented in C#. Features a full pipeline from lexical analysis through recursive descent parsing with operator precedence to AST construction and tree-walking evaluation. Supports variables (`let-in`), user-defined functions, conditionals (`if-else`), math functions (`sin`, `cos`, `log`), string concatenation, and `print`.

---

## 📑 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [How to Build & Run](#how-to-build--run)
- [How It Works](#how-it-works)
- [Academic Context](#academic-context)

---

## ✨ Features

- **Lexical Analysis** — Tokenizes HULK source code into a structured token stream
- **Recursive Descent Parser** — Parses expressions with correct operator precedence
- **Abstract Syntax Tree (AST)** — Clean tree representation of programs with many node types
- **Tree-Walking Evaluator** — Executes programs by traversing the AST
- **Variables** — `let x = expr in body` scoped variable bindings
- **User-Defined Functions** — First-class function declarations and calls
- **Conditionals** — `if-else` expressions
- **Built-in Math** — `sin`, `cos`, `tan`, `log`, `sqrt`, `exp`, `PI`, `E`
- **String Operations** — String literals and `@` concatenation operator
- **Print** — Output values to the console

---

## 🛠 Tech Stack

| Component       | Technology       |
|-----------------|------------------|
| Language         | C#               |
| Runtime          | .NET 6           |
| Paradigm         | Interpreter      |

---

## 📁 Project Structure

```
Hulk-PRO-2023/
├── AST/                          # Abstract Syntax Tree node definitions
│   ├── NumberNode.cs             # Numeric literal
│   ├── BinaryOpNode.cs          # Binary operations (+, -, *, /)
│   ├── LetInNode.cs             # let-in variable binding
│   ├── IfElseNode.cs            # Conditional expression
│   ├── FunctionCallNode.cs      # Function invocation
│   └── ...                      # Many more AST node types
├── Lexer/
│   └── Analizador_lexico.cs     # Lexical analyzer (scanner)
├── Parser/
│   └── Orden_Prioridad.cs       # Recursive descent parser with precedence
├── Evaluate/
│   └── Evaluador.cs             # Tree-walking evaluator
├── Funciones/                    # Built-in and user-defined function support
└── Program.cs                    # Entry point — REPL or file execution
```

---

## 🚀 How to Build & Run

### Prerequisites

- .NET 6 SDK

### Build

```bash
dotnet build
```

### Run

```bash
dotnet run
```

### Example HULK Code

```
>> let x = 42 in print(x);
42

>> function factorial(n) => if (n == 0) 1 else n * factorial(n - 1);
>> print(factorial(5));
120

>> let name = "HULK" in print("Hello " @ name);
Hello HULK

>> print(sin(PI / 2));
1
```

---

## ⚙️ How It Works

### Interpreter Pipeline

```
Source Code → [Lexer] → Tokens → [Parser] → AST → [Evaluator] → Result
```

1. **Lexical Analysis** (`Analizador_lexico.cs`) — Scans the input string character by character, producing tokens: numbers, strings, identifiers, keywords (`let`, `in`, `if`, `else`, `function`), operators, and punctuation.

2. **Parsing** (`Orden_Prioridad.cs`) — A recursive descent parser consumes tokens and builds an AST. Operator precedence is handled through grammar stratification (additive → multiplicative → unary → primary).

3. **AST Construction** — Each syntactic construct maps to a node type: `NumberNode`, `BinaryOpNode`, `LetInNode`, `IfElseNode`, `FunctionCallNode`, etc.

4. **Evaluation** (`Evaluador.cs`) — A tree-walking evaluator visits each AST node:
   - **Literals** return their value.
   - **Binary operations** evaluate both children and apply the operator.
   - **let-in** creates a new scope, binds the variable, and evaluates the body.
   - **if-else** evaluates the condition and selects the appropriate branch.
   - **Function calls** look up the function, bind arguments, and evaluate the body.

---

## 🎓 Academic Context

> **Course Project** — Programming, University of Havana, 2023
