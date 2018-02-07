# Assignment 1 -- Flex / Bison

*due on 4 April 2018*

In this assignment you will implement the first part of your mC compiler front-end.

To get you started, some code is provided as [mCc Template](https://github.com/W4RH4WK/mCc).
You are encouraged, but *not required* to use this code-base.

The specification of the input language mC can be found in [`mC_specification.md`](mC_specification.md).

Your compiler must be written in C, although you can use C++ for unit testing.

Build your compiler as (shared) library and use it via dedicated executables.
An example for this can be found in the provided code.

## Task 0

If you decide to use the provided code-base, make sure you understand it.
Modify it to your liking before continuing with the assignment.
State *and justify* modifications not directly related to any of the following tasks in the markdown file `doc/changes.md` -- simply append to it.

## Task 1

Implement an abstract syntax tree (AST) which models the input language.

Provide a mechanism to print a given AST in the [DOT format] so it can be visualised using [Graphviz].

[DOT format]: <https://en.wikipedia.org/wiki/DOT_(graph_description_language)>
[Graphviz]: <https://graphviz.gitlab.io/>

## Task 2

Implement lexer and parser, using `flex` and `bison` respectively.
The goal of this task is to have a lexer and a parser which convert a (valid) mC input program to its corresponding AST.

- Pay attention to operator precedence.
- Attach source location information to the resulting AST nodes.
- Your parser must be [*pure (re-entrant)*](https://www.gnu.org/software/bison/manual/html_node/Pure-Decl.html).

> Implicit state is evil.

## Task 3

Modify your lexer and parser implementation to do basic error handling.
Do not worry about error recovery or such fancy features.
Simply terminate the parsing process (not the application) and provide some meaningful error on what went wrong.

Do not directly print to `stdout` / `stderr` from your library!
The *parse* function should return a *parser result* which, either contains the AST upon parsing valid input, or a meaningful error.
The error message should be examined / printed by the dedicated executable which invoked the *parse* function.

Ensure you do not leak memory upon parsing an invalid program.

## Task 4

Create 4 different, valid example inputs, each around 30 lines of code.
They do not have to be meaningful, but they should be valid semantically.
For instance, do not call a function taking 2 parameters with 3 arguments.

All 4 examples combined should cover everything stated in the specification.

Also, try to do some computational / memory heavy operations in your mC programs so we can later benchmark the generated code.

The example inputs of all teams will be made available so everyone has a decent number of integration tests.

## Submission

Each team (not each person):

1. `cd` into your compiler repository
2. commit all pending changes
3. checkout the revision you want to submit
4. ensure the revision builds, and all unit and integration tests succeed
5. run the following command where `XX` is the number of your team with leading zero (eg `07`)

       $ git archive --prefix=team_XX_assignment_1/ --format=zip HEAD > team_XX_assignment_1.zip

6. verify that the resulting archive contains everything you want to submit, and nothing more (no binaries, etc)
7. send me the resulting archive using the following link (do not modify the subject)

:email: [send email](mailto:alexander.hirsch@uibk.ac.at?subject=703602%20-%20Assignment%201)

*Note:* You might want to tag the revision you are submitting.
