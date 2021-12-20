# PushDirectory.cmake

Quickly write CMake build scripts, without limiting your ability to customize the target further!

## Example

```cmake
cmake_minimum_required(VERSION 3.20) # might be a lower version, not sure right now
project(...)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake") # or wherever you stored PushDirectory.cmake
include(PushDirectory)

push_directory_executable(
    TARGET_NAME "hello"
    SOURCE_FILES "hello.cpp" "otherfile.cpp" # IMPORTANT: these go in ./src/hello/
    INCLUDED_DIRECTORIES "inc"
    LINKED_LIBRARIES "pthread"
)
```
The directory structure is customizable:
```cmake
push_directory_executable(
    TARGET_NAME "blah"
    SOURCE_DIRECTORY "Sources"
    SOURCE_FILES "blah.cpp" # now goes in ./Sources/blah/
    ...
)
push_directory_executable(
    TARGET_NAME "blah2"
    SOURCE_DIRECTORY_COMES_LAST
    SOURCE_DIRECTORY "source"
    SOURCE_FILES "blah.cpp" # goes in ./blah2/source/blah.cpp
    ...
)
```

I will add more features to this on request, it's just a tool for me currently. Contributions are welcomed!
