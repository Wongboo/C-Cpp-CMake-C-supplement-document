## Entry
[Homepage](../README.md)
[cross platform judgement](cross_platform.md)
[link library](library.md)

[OpenCV](##opencv)
[OpenMP](##openmp)
## OpenCV
### Entry
[Homepage](../README.md)
[cross platform judgement](cross_platform.md)
[link library](library.md)
```cmake
find_package(OpenCV REQUIRED)
#in MacOS and linux, this line is necessary
include_directories(${OpenCV_INCLUDE_DIRS})
#the OpenCV installed by brew hasn't opencv_world
link_libraries(${OpenCV_LIBS)
```

## OpenMP
### Entry
[Homepage](../README.md)
[cross platform judgement](cross_platform.md)
[link library](library.md)
```cmake
find_package(OpenMP REQUIRED)
link_libraries(OpenMP::OpenMP_CXX)
```