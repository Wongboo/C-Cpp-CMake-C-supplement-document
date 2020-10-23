# C-Cpp-CMake-C-supplement-document
C/Cpp/CMake-C-supplement-document
## Entry
[cross platform judgement](cross_platform.md)    
[link library](library.md)
### Main purpose
The main purpose of this document is to provide supplement document fo C/C++ and CMake.This document has some extraordinay features, it's dedicately designed to fit these demand:
- Are you tired of finding linking library phase in CMake, every library has its' own linking method. Even the method works for some OS, but it may failes on other, for example:
```cmake
find_package(OpenCV REQUIRED)
link_libraries(opencv_world)
```
  T

- 
