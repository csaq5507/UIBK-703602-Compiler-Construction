# Guidelines

Deviate from these guidelines only if you have a valid reasons to do so.

## General

- *implementing* something also implies that it is *properly* (unit) tested, otherwise it is not considered implemented!
- don't be a git -- use [Git](https://git-scm.com/)!
- files are UTF-8 encoded and use Unix line-endings (`\n`)
- files contain *one* newline at the end
- lines do not contain trailing white-space
- enable and minimise compiler warnings
- do not waste time or space (memory leaks)
- check for leaks using `valgrind`, especially in error cases

## Plain-Text Files

- lines must not exceed 80 columns
- content is properly formatted
    - well structured
    - paragraphs are clearly separated
    - headings stand out
- files may contain *ASCII art* (not restricted to ASCII, UTF-8 characters are okay)
- files should be *self-contained* (ie no references to other files like images or so)

See issues of the [Phrack magazine](http://www.phrack.org/) as reference.

## Markdown Files

- lines may exceed 80 columns
- use newlines to separate sentences (works best when using Git)
- try to be compatible with [Pandoc](https://pandoc.org/)'s interpretation of Markdown

## C/C++ Files

- use a formatting tool, like [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)
- stick to the formatting used in the provided code-base (similar to [Linux Kernel Coding Style](https://www.kernel.org/doc/html/v4.10/process/coding-style.html))
- lines should not exceed 80 columns
- the structure of a source file should be similar to its corresponding header file
    - separators can be helpful

## System

I'll be using a virtualised, updated Ubuntu 17.10 (64 bit) to examine your submissions.
The submitted code has to compile and run on this system.
This information tells you which software versions I'll be using.

## Build System

You may use either [Meson], [CMake], Autotools, or plain Makefiles as build system (generator).
Yet, the dependencies between your source files must be modelled correctly.

[Meson]: <http://mesonbuild.com/>
[CMake]: <https://cmake.org/>

The default configuration should be a *release build*.
Switching to a *debug build* configuration should be possible via a commandline switch.

## Unit Testing

I highly recommend using [GoogleTest](https://github.com/google/googletest).
But you can choose a different unit testing framework if you want.
Just make sure it is present as package in my examination system's default package repository, or can be easily installed via your build system.

All of your unit tests should be run issuing only a single command (given the tests have been built).
I am expecting something like:

    $ ninja test

Your README must include instructions on how to build your code, run your unit and integration tests.

## Integration Testing

My recommendation is to build yourself an integration test runner.
Otherwise, the same conditions as for unit testing frameworks apply.
