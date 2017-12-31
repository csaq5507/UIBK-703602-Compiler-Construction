# Requirements

Deviate from these requirements only if you have valid reasons to do so.

## General

- *implementing* something also implies that it is *properly* (unit) tested, otherwise it is not considered implemented!
- don't be a git -- use [Git](https://git-scm.com/)!
- files are UTF-8 encoded and use Unix line-endings (`\n`)
- files contain *one* newline at the end
- lines do not contain trailing white-space

## Plain-Text Files

- lines must not exceed 80 columns
- content is properly formatted
    - well structured
    - paragraphs are separated by one empty line
    - headings are clearly visible
- files may contain *ASCII art* (not restricted to ASCII, UTF-8 characters are okay)
- files should be *self-contained* (ie no references to other files like images or so)

See issues of the [Phrack magazine](http://www.phrack.org/) as reference.

## Markdown Files

- lines may exceed 80 columns
- use newlines to separate sentences (works best when using Git)
- try to be compatible with [Pandoc](https://pandoc.org/)'s interpretation of Markdown

## C / C++ Files

- use a formatting tool, like [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)
- stick to the formatting used in the provided code-base
- lines should not exceed 80 columns
- the structure of a source file should be similar to its corresponding header file.

## System

I'll be using a virtualised, up-to-date Ubuntu 17.10 (64 bit) to examine your submissions.
This tells you which software versions I'll be using.

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
Just make sure it can be easily installed via your build system, or is present as package in my examination system's default package repository.

All of your unit tests should be run issuing only a single command (given the application has been built).
I am expecting something like:

    $ ninja test

Your README must include instructions on how to build, and run your tests.

## Integration Testing

My recommendation is to build yourself an integration test runner.
Otherwise, the same conditions as for unit testing frameworks apply.
