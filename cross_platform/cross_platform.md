## Entry
[Homepage](../README.md)
[cross_platform_judgement](cross_platform.md)
[link_library](library.md)

[platform](##platform)
[SIMD](##simd)
[forceinline](##forceinline)
[_s_function](##_s)
## Platform
### Entry
[Homepage](../README.md)
[cross_platform_judgement](cross_platform.md)
[link_library](library.md)
```C++
//detect WIN32

//detect WIN64
//
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
#detect Clang
if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
#or other lang
if (CMAKE_<LANG>_COMPILER_ID STREQUAL "Clang")
```
## SIMD
### Entry
[Homepage](../README.md)
[cross_platform_judgement](cross_platform.md)
[link_library](library.md)
```C++
//GCC https://gcc.gnu.org/onlinedocs/gcc/Loop-Specific-Pragmas.html
//CLANG https://llvm.org/docs/Vectorizers.html
//MSVC https://docs.microsoft.com/en-us/cpp/preprocessor/loop?view=msvc-160
#pragma GCC ivdep
#pragma clang loop vectorize(enable) 
#pragma loop( ivdep )
```
```cmake
if(MSVC)
#change to AVX... https://docs.microsoft.com/en-us/cpp/build/reference/arch-minimum-cpu-architecture?view=msvc-160
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /arch:AVX2")
else()
#or change to the deployed machine environment
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -march=native")
endif()
```

## forceinline
### Entry
[Homepage](../README.md)
[cross_platform_judgement](cross_platform.md)
[link_library](library.md)
```C++
#ifndef _WIN32
#define __forceinline inline __attribute__((always_inline))
#endif
```

## _s
### Entry
[Homepage](../README.md)
[cross_platform_judgement](cross_platform.md)
[link_library](library.md)
```C++
//if not MSVC, do not define MACRO, to control MACRO num
#if defined(_MSC_VER) && !defined(_CRT_SECURE_NO_WARNINGS)
#define _CRT_SECURE_NO_WARNINGS
#endif
```