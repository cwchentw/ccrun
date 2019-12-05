# ccrun

`ccrun`, aka *C* or *C*++ *Run*ner, compiles and executes C or C++ code base automatically.

## Warning

`ccrun` will compile and execute target source. Hence, DON'T use `ccrun` to run untrusted source.

## Why `ccrun`?

C or C++ are compiled languages. We have to compile its source before executing it. Nevertheless, it is tedious to compile C or C++ source manually. For small code base, it is overkill to write Makefile or other project configuration file as well.

To address the issue, `ccrun` can automatically compile and execute C or C++ source without any project configuration file, handy for small code base.

## System Requirements

`ccrun` itself is written in POSIX shell. Besides, you need a C or C++ compiler to compile target source.

By default, `ccrun` will invoke `gcc` or `g++` for compilation tasks. You may change to another C or C++ compiler by setting related environment variables.

We tested `ccrun` against several Unix or Unix-like systems:

* Ubuntu 18.04 LTS
* Amazon Linux, largely RHEL or CentOS compatible
* TrueOS, FreeBSD compatible
* Solaris

It should work on other Unix or Unix-like systems as well.

## Supported File Formats

`ccrun` supports the following file formats:

* *.c* for C source
* *.cpp*, *.cxx* or *.cc* for C++ source

`ccrun` can handle projects that mix C and C++ together.

## Usage

Add exec mode for `ccrun` before using it:

```
$ chmod +x path/to/ccrun
```

It is recommended to copy `ccrun` to a valid **$PATH** like *$HOME/bin* or */usr/local/bin*.

Run single source:

```
$ ccrun path/to/file.c
```

Run multiple sources in a project:

```
$ ccrun path/to/*.c
```

Run multiple C and C++ mixed sources in a project:

```
$ ccrun path/to/*.c path/to/*.cpp
```

Run target sources with arguments:

```
$ ccrun path/to/*.c -- --opt param_a param_b param_c
```

## Environment Variables

You can adjust the behavior of `ccwarn` with the following environment variables:

* **CC** to set GCC compiler
* **CXX** to set G++ compiler
* **OUT_FILE** to set the name of a temporary output file
* **CFLAGS** to set custom include paths and compiler flags for C
* **CXXFLAGS** to set custom include paths and compiler flags for C++
* **LDFLAGS** to set custom lib paths
* **LIBS** to set custom library linkages
* **LD_LIBRARY_PATH** to set custom binary file paths

All environment variables are optional, set with sensible default values.

## Note

If you want to check code quality and conform some language standard for your C or C++ source, see [ccwarn](https://github.com/cwchentw/ccwarn).

## Copyright

Copyright 2019, Michael Chen; licensed under [MIT](https://opensource.org/licenses/MIT).
