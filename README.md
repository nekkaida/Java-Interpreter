# Lox Interpreter

A Java implementation of the Lox programming language from Robert Nystrom's book ["Crafting Interpreters"](https://craftinginterpreters.com/).

## Overview

This project is an implementation of the Lox programming language, a small dynamic language with C-like syntax that supports:

- Variables and basic data types (numbers, strings, booleans, nil)
- Control flow (if statements, while loops, for loops)
- Functions with proper closures
- Classes with inheritance
- Lexical scoping

The interpreter is implemented as a tree-walk interpreter in Java, focusing on clarity and correctness rather than performance.

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Running Lox Programs](#running-lox-programs)
  - [Interactive Mode](#interactive-mode)
  - [Execution Modes](#execution-modes)
- [Language Syntax](#language-syntax)
  - [Basic Syntax](#basic-syntax)
  - [Variables](#variables)
  - [Control Flow](#control-flow)
  - [Functions](#functions)
  - [Classes](#classes)
- [Project Structure](#project-structure)
- [Implementation Details](#implementation-details)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Features

- **Complete Language Implementation**: Fully implements the Lox language as described in "Crafting Interpreters"
- **Multiple Execution Modes**: Run complete programs, evaluate expressions, parse code, or just tokenize
- **Robust Error Handling**: Provides clear error messages with line information
- **Interactive REPL**: Try out code snippets in an interactive shell

## Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or higher
- Git (for cloning the repository)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/lox-interpreter.git
   cd lox-interpreter
   ```

2. Compile the source code:
   ```bash
   javac *.java
   ```

## Usage

### Running Lox Programs

To run a Lox program from a file:

```bash
java Main run path/to/your/program.lox
```

Or simply:

```bash
java Main path/to/your/program.lox
```

### Interactive Mode

To start the interactive prompt (REPL):

```bash
java Main
```

In the REPL, you can type Lox code and see the results immediately. Type Ctrl+D (or Ctrl+Z on Windows) to exit.

### Execution Modes

The interpreter supports several execution modes:

- **run**: Execute a Lox program file (default)
  ```bash
  java Main run script.lox
  ```

- **evaluate**: Evaluate and print the result of expressions
  ```bash
  java Main evaluate script.lox
  ```

- **parse**: Parse the program and print the abstract syntax tree
  ```bash
  java Main parse script.lox
  ```

- **tokenize**: Tokenize the program and print the tokens
  ```bash
  java Main tokenize script.lox
  ```

## Language Syntax

### Basic Syntax

Lox has a C-like syntax with statements ending in semicolons:

```
// This is a comment
print "Hello, world!";
```

### Variables

```
var name = "Bob";
var age = 25;
print name + " is " + age + " years old.";
```

### Control Flow

```
// If statement
if (condition) {
  print "True!";
} else {
  print "False!";
}

// While loop
var i = 0;
while (i < 10) {
  print i;
  i = i + 1;
}

// For loop
for (var i = 0; i < 10; i = i + 1) {
  print i;
}
```

### Functions

```
// Function declaration
fun fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 2) + fibonacci(n - 1);
}

// Function call
print fibonacci(10);
```

### Classes

```
// Class declaration
class Person {
  init(name, age) {
    this.name = name;
    this.age = age;
  }

  sayName() {
    print "My name is " + this.name;
  }
}

// Inheritance
class Employee < Person {
  init(name, age, title) {
    super.init(name, age);
    this.title = title;
  }

  sayJob() {
    print "I work as a " + this.title;
  }
}

// Using classes
var employee = Employee("Alice", 30, "Developer");
employee.sayName();  // "My name is Alice"
employee.sayJob();   // "I work as a Developer"
```

## Project Structure

```
.
├── Main.java               # Main entry point for the interpreter
├── Scanner.java            # Lexical analyzer (tokenizer)
├── Token.java              # Token representation
├── TokenType.java          # Token type enumeration
├── Parser.java             # Syntax analyzer
├── Expr.java               # Expression AST nodes
├── Stmt.java               # Statement AST nodes
├── Interpreter.java        # Tree-walk interpreter
├── Environment.java        # Variable environment
├── LoxCallable.java        # Function interface
├── LoxFunction.java        # Function implementation
├── LoxClass.java           # Class implementation
├── LoxInstance.java        # Instance implementation
├── Resolver.java           # Variable resolution and binding
├── Return.java             # Return value handling
├── RuntimeError.java       # Runtime error handling
└── examples/               # Example Lox programs
```

## Implementation Details

The interpreter follows a classic compiler pipeline:

1. **Scanning (Lexical Analysis)**: Converts source code into tokens
2. **Parsing (Syntax Analysis)**: Converts tokens into an abstract syntax tree (AST)
3. **Static Analysis**: Resolves variable bindings
4. **Interpretation**: Executes the AST

The implementation emphasizes clarity and follows object-oriented design principles:

- **Visitor Pattern**: Used to traverse and interpret the AST
- **Error Handling**: Both compile-time and runtime errors are reported with line information
- **Environment Chain**: Implements lexical scoping through linked environments

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Robert Nystrom for his excellent book ["Crafting Interpreters"](https://craftinginterpreters.com/)
- The Lox language design, which provides an excellent teaching language