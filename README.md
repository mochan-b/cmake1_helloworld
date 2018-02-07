# CMake Tutorial - Part 1. Hello World

## Introduction

We want a CMake file for our hello world cpp application. It will have one file: `hello.cpp` and compile it into an executable `hello`. 

The contents of `hello.cpp` is as follows, 
```cpp
#include <iostream>

int main()
{
    std::cout << "Hello World" << std::endl;
    return 0;
}
```

## Hello World CMake file

By convention, we name the CMake file as `CMakeLists.txt`. When `cmake` runs, it looks for this file. 

The contents of the `CMakeLists.txt` is:
```cmake
add_executable(hello hello.cpp)
```
which creates an executable `hello` from `hello.cpp`.

The next convention (at least for *nix systems) is to create a `build` directory and then inside the `build` directory run 
```
cmake ..
```

When you run cmake it will look for the C/C++ compiler and generate a whole bunch of files. For *nix systems, it will be a `Makefile` which can be used to build your system. 

The next step is to build the system and then run 
```
make
```

You should have a file `hello` in your directory that you can run and it should output `Hello World`.

## Project Name

We can also give the project a name and specify if in the CMake file.

```cmake
project(hello)
add_executable(${PROJECT_NAME} hello.cpp)
```

`${PROJECT_NAME}` is a way to use a CMake variable `PROJECT_NAME` which is set when we use the `project` command. The value is by default is `Project`.

## CMake Version Number

You can also specify the minimum version of CMake that will be required to make the build files. In this way, the user gets a friendly error message about a CMake that is too old rather than cryptic CMake errors.

```cmake
cmake_minimum_required(VERSION 3.0.0)
project(hello)
add_executable(${PROJECT_NAME} hello.cpp)
```

## Conclusion

We have made a CMake file to build our hello world C++ program. Then, we also added the project name and the minimum CMake version required.