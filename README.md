# C-Cpp-CMake-C-supplement-document
C/Cpp/CMake-C-supplement-document
## Entry
[cross_platform_judgement](cross_platform/cross_platform.md)    
[link_library](library/library.md)
## Main purpose
The main purpose of this document is to provide supplement document fo C/C++ and CMake.This document has some extraordinay features, it's dedicately designed to fit these demand:
- Are you tired of finding linking library phase in CMake, every library has its' own linking method. Even the method works for some OS, say, Windows, but it may failes on other, for example:
```cmake
find_package(OpenCV REQUIRED)
link_libraries(opencv_world)
```
But meanwhile, these lines of code couldn't compile on macOS, You should change to
```cmake
find_package(OpenCV REQUIRED)
#in MacOS and linux, this line is necessary
include_directories(${OpenCV_INCLUDE_DIRS})
#the OpenCV installed by brew hasn't opencv_world
link_libraries(${OpenCV_LIBS)
```
To solve this, I scheduled to provide full cross-platform link command for all package, I appreciate your contribution!

- Some times we want to use *MACRO* to distinguish OS and compiler difference, but existing files tend to separate OS and compiler, for example, do not consider clang-cl, meanwhile, they seperate C/C++ macros and CMake judgement, in my document, they will intergrate, here are some most simpile way to detect OS or compiler(note they are imcomplete)
```C++
//detect MSVC
#ifdef _MSC_VER
//detect GCC
#elif defined(__GNUC__)
//detect Clang
#elif defined(__clang__)
```
```cmake
#detect Windows
if(WIN32)
#detect MacOS
if(APPLE)
#detect Linux
IF (CMAKE_SYSTEM_NAME MATCHES "Linux")

#detect MSVC
if (MSVC)
#detect GCC, use C++
if (CMAKE_COMPILER_IS_GNUCXX)
#or other lang
if (CMAKE_<LANG>_COMPILER_ID STREQUAL "Clang")
#detect Clang
if (CMAKE_<LANG>_COMPILER_ID STREQUAL "Clang")
```
Note that, in most case, the simplest way for one compiler may not work on other, say, if(GCC) is invalid. And you also want more, for example, \_\_forceinline or inline \_\_attribute__((always_inline)), or __declspec, so on
