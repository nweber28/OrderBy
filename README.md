# OrderBy

## Prerequisites
- [cmake](https://cmake.org/)

## What does it do?
OrderBy orders header and implementation files by directory path with the header file occurring first and the implementation file coming second.

OrderBy expects a relative/absolute file path as input and traverses the directory (and subdirectories) recursively to order files together.
Files MUST have the same absolute directory path to be considered a pair (must reside in same directory).

Ex: 'user/bar/foo.hpp' and 'user/foo.cpp' will NOT be considered a pair.

## Installation and Build

Clone or download this repo

Build using cmake:

```
cmake [path to CMakeLists.txt]
```

## Usage

OrderBy is run on the command line

```
./OrderBy [relative path] 
./OrderBy [absolute path]
```

Help
```
./OrderBy --help
```

## Options
  -o, --output [file name] - File name of output - ordered list of file names (prints ordered pairs to cmd line by default
  
  -w, --warningReport [file name] - Output optional report file for unpaired .cpp (off by default)
  
  -n, --nonrecursive - Enables nonrecursive traversion of subdirectories (off by default)
  
  -q, --quiet - Disables warnings (warnings on by default)
  
  -f, --fullPath - Output contains full path of each file (relative path by default)
  
## Output
OrderBy outputs ordered pairs of header and implementation files (header files first, then implementation files second).
Single header files are also outputted even if they do not have a corresponding implementation file.

Implementation files that do not have a corresponding header file are considered unpaired and will not be contained in the outputted file of pairs.

A seperate warning report option (-w) is available that places all implementation files without corresponding headers inside of it.

Supported header (first) file extensions:
- .h
- .hpp
- .hxx
- .hh
- .h++
- .H
- .i
- .ii
- .tcc
  
Supported Implementation (second) file extensions: 
- .c
- .cpp
- .CPP
- .cp
- .cxx
- .cc
- .c++
- .C
