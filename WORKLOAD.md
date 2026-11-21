# Phase I Workload Division

**Deadline: Week 11.** Deliverable: `src/lexer.l` + `src/parser.y`.

## How to Pick a Role

1. Read all 4 roles below.
2. Put your name in the **Claimed by** field of the role you want, then commit and push (or comment in the group chat).
3. First come, first served. If two people want the same role, discuss it in the group.
4. Once all 4 roles are claimed, copy the names into the **Team** table in `README.md`.

---

## Step 0: Everyone Together (first 1–2 days)

These must be done **before** anyone writes grammar rules:

- [ ] Agree on the language syntax and write it in `docs/language_spec.md`
  - data types (e.g. int, float, char, string, bool)
  - how declarations, constants, blocks, functions and classes look
  - statement terminator and block delimiters
- [ ] Agree on **all token names** and list them in `docs/tokens.md`
- [ ] Agree on the shared non-terminal names used across sections (`program`, `statement`, `statement_list`, `block`, `expression`, `type`)
- [ ] Set up the GitHub repo, branches, and make sure everyone can build an empty project

---

## Member 1: Lexer & Integration

**Claimed by:** Adam Amr (@Adam-Amr1)

**Files:** `src/lexer.l`, `Makefile`, `build.bat`, `run_tests.bat`, `README.md`, `docs/tokens.md`

### Tasks
- [ ] Keywords (data types, `const`, `if`, `else`, `while`, `repeat`, `until`, `for`, `switch`, `case`, `default`, `break`, `continue`, `return`, `function`, `class`, `new`, `this`, …)
- [ ] Operators: arithmetic, relational, logical, assignment, `.` (dot), unary
- [ ] Delimiters: `( ) { } [ ] ; , :`
- [ ] Literals: integer, float, char, string, boolean
- [ ] Identifiers
- [ ] Single-line and multi-line comments
- [ ] Whitespace handling and **line number tracking** (for error messages)
- [ ] Rule for unknown or invalid characters (report the line number)
- [ ] Build scripts (`build.bat`, `Makefile`) and test runner (`run_tests.bat`)
- [ ] Set up the `parser.y` skeleton with the marked sections for each member
- [ ] **Merge** everyone's sections, run all tests after each merge, and report conflicts to the section owner
- [ ] Write `docs/tokens.md` (token + description table, a required deliverable)

### Tests
- [ ] Lexer edge cases (comments, literals, invalid characters)
- [ ] `tests/valid/10_full_program.txt` (a program that uses every feature)

---

## Member 2: Declarations & Expressions

**Claimed by:** Mostafa Samir (@mostafasamiir)

**Section in** `src/parser.y`: *Program / Declarations / Expressions / Precedence*

### Tasks
- [ ] Top-level `program` rule
- [ ] Data `type` rule
- [ ] Variable declarations (with and without initialization, several in one line if supported)
- [ ] Constant declarations
- [ ] Assignment statements
- [ ] Arithmetic expressions (`+ - * / %`, parentheses)
- [ ] Relational expressions (`== != < > <= >=`)
- [ ] Logical expressions (`&& || !`)
- [ ] Unary minus, increment and decrement (if supported)
- [ ] **Precedence and associativity table** (`%left`, `%right`, `%nonassoc`)
- [ ] Agree with Member 4 on how function calls and `obj.attr` / `obj.method()` fit inside `expression`

### Tests
- [ ] `tests/valid/01_declarations.txt`
- [ ] `tests/valid/02_expressions.txt`
- [ ] `tests/valid/03_assignment.txt`
- [ ] `tests/invalid/syntax_errors_01_declarations.txt`
- [ ] `tests/invalid/syntax_errors_02_expressions.txt`

---

## Member 3: Control Flow & Blocks

**Claimed by:** Amira El Wakeel (@amiraelwakeel)

**Section in** `src/parser.y`: *Statements / Blocks / Control Flow*

### Tasks
- [ ] `statement` and `statement_list` rules
- [ ] `block` rule: nested scopes with declarations at the start
- [ ] `if-then` / `if-then-else`, and resolve the **dangling-else** conflict
- [ ] `while` loop
- [ ] `repeat-until` loop
- [ ] `for` loop
- [ ] `switch` with `case` / `default`
- [ ] `break` / `continue`
- [ ] Agree with Member 2 on how `statement` and `block` connect to declarations

### Tests
- [ ] `tests/valid/04_if_else.txt` (including nested if-else)
- [ ] `tests/valid/05_loops.txt`
- [ ] `tests/valid/06_switch.txt`
- [ ] `tests/valid/07_blocks_scopes.txt`
- [ ] `tests/invalid/syntax_errors_03_control_flow.txt`

---

## Member 4: Functions, Classes & Objects

**Claimed by:** Ali Osama (@ali0sama)

**Section in** `src/parser.y`: *Functions / Classes & Objects*

### Tasks
**Functions**
- [ ] Function declaration (return type, name, parameter list, body)
- [ ] Empty and multiple parameters
- [ ] `return` statement (with and without a value)
- [ ] Function calls with an argument list (as a statement and inside expressions)

**Classes & Objects**
- [ ] Class declaration with a class name
- [ ] Data members (attributes) inside classes
- [ ] Member functions (methods) inside classes
- [ ] Object declaration and instantiation (e.g. `new ClassName(...)`)
- [ ] Attribute access and modification with `.` (read and assign)
- [ ] Method calls through objects
- [ ] **[Bonus]** Constructors

### Tests
- [ ] `tests/valid/08_functions.txt`
- [ ] `tests/valid/09_classes_objects.txt`
- [ ] `tests/invalid/syntax_errors_04_functions.txt`
- [ ] `tests/invalid/syntax_errors_05_classes.txt`

---

## Timeline (suggested)

| When | Milestone |
|---|---|
| Days 1–2 | Step 0 done: language spec + token names agreed |
| End of week 1 | Lexer done, `parser.y` skeleton pushed, each member's rules started |
| End of week 2 | Every section done with its own tests passing |
| Week before deadline | Full integration, **zero unresolved conflicts**, all tests pass, docs finished |
| Week 11 | Submit Phase I |

## Rules

- Only edit **your own section** of `parser.y`. For changes in someone else's section, ask them first.
- Never push generated files (`lex.yy.c`, `parser.tab.*`, `*.exe`).
- Every PR must build cleanly and pass all tests.
- Shift/reduce or reduce/reduce conflicts are fixed by the **owner of the rules involved**.
- Say in the group chat when you're blocked. Don't wait until the deadline.
