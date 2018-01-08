# Bonus Tasks

You are not obliged to implement them, but doing so may shift your grade.

## Assignment 1

- Implement a visitor mechanism which houses the logic of traversing the AST.
  Use this visitor for all tasks involving AST traversal.

- Investigate the tracing / debugging options provided by flex / bison.
  Provide a way to access these debugging information.

- Implement the following AST transformation:

      single_expr(unary_op("-"), single_expr(literal(α)))  ⟹  single_expr(literal(- α))

## Assignment 2

- Implement some form of trace output for the type checking process.

- Provide an executable to dump symbol tables in a human readable format.

- Use static single assignment (SSA).

## Assignment 3

- Implement a visitor mechanism for your CFGs.

- Implement the generation of the call graph.

- Perform register allocation.

## Assignment 4

- Implement some form of error recovery.
  Do not simply terminate the parsing process upon encountering an error.
  Continue at a sensible point in the token stream and accumulate errors.
