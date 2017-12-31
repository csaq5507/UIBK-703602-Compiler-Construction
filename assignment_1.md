# Assignment 1 -- Flex / Bison

*due on 4 April 2018*

In this assignment you will implement the first part of your mC compiler front-end.

To get you started, some code is provided as [mCc Template](https://github.com/W4RH4WK/mCc).
Your are encouraged, but *not required* to use this code-base.

The specification of the input language mC can be found in [`mC_specification.md`](mC_specification.md).

Your compiler must be written in C, although you can use C++ for unit testing.

Build your compiler as (shared) library and use it via dedicated executables.
See the template repository regarding this requirement.

## Task 0

If you decide to use the provided code-base, make sure you understand it.
Modify it to your liking before continuing with the assignment.
State *and justify* all modifications in the markdown file `doc/changes.md`.

## Task 1

Implement an abstract syntax tree (AST) which models the input language.

(Optional) Implement a visitor mechanism which houses the logic for traversing the AST.

Provide a mechanism to print a given AST in the [DOT format] so it can be visualised using [Graphviz].

[DOT format]: <(https://en.wikipedia.org/wiki/DOT_(graph_description_language)>
[Graphviz]: <https://graphviz.gitlab.io/>

## Task 2

Implement lexer and parser, using `flex` and `bison` respectively.
The goal of this task is to have lexer and parser which convert a (valid) mC input program to its corresponding AST.

- Pay attention to operator precedence.
- Attach source location information to the resulting AST nodes.
- Your parser must be [*pure (re-entrant)*](https://www.gnu.org/software/bison/manual/html_node/Pure-Decl.html).

> Implicit state is evil.

## Task 3

Modify your lexer and parser implementation to do basic error handling.
Do not worry about error recovery or such fancy features.
Simply terminate the parsing process (not the application) and provide some meaningful error on what went wrong.

Do not print to `stdout` / `stderr` directly!
Your *parse* function should return a *parser result* which, either contains the AST upon parsing valid input, or a meaningful error.

Ensure you do not leak memory upon encountering a parse error.

## Task 4

Create 4 different, valid example inputs, each around 30 lines of code.
They do not have to be meaningful, but they should be valid semantically.
For instance, do not call a function taking 2 parameters with 3 arguments.

The example inputs of all teams will be made available to have a decent number of integration tests.

## Submission

Each team (not each person):

1. `cd` into your compiler repository
2. commit all pending changes
3. checkout the revision you want to submit
4. run the following command where `XX` is the number of your team with leading zero (eg `07`)

       $ git archive --prefix=team_XX_assignment_1/ --format=zip HEAD > team_XX_assignment_1.zip

5. send me the resulting archive using the following link (do not modify the subject)\
   :email: [send email](mailto:alexander.hirsch@uibk.ac.at?subject=703602%20-%20Assignment%201)
