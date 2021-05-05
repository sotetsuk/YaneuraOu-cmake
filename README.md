[![ci](https://github.com/sotetsuk/YaneuraOu-cmake/actions/workflows/ci.yml/badge.svg)](https://github.com/sotetsuk/YaneuraOu-cmake/actions/workflows/ci.yml)

# YaneuraOu-cmake

Cmake files to build YaneuraOu.

## Usage

Link and include `YaneuraOu` lib in your CmakeLists.txt like 

```cmake
target_link_libraries(YOUR_ENGINE PUBLIC YaneuraOu)
target_include_directories(YOUR_ENGINE PUBLIC ${YaneuraOu_SOURCE_DIR}/include)
```

Your engine can include `YaneuraOu` headers like

```cpp
#include "YaneuraOu/extra/all.h"
```

## Example

Build tanuki solver with `CmakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.16)
project(tanuki)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D NO_SSE")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D TANUKI_MATE_ENGINE")

include(FetchContent)
set(FETCHCONTENT_QUIET OFF)
set(FETCHCONTENT_UPDATES_DISCONNECTED ON)

fetchcontent_declare(
  YaneuraOu
  GIT_REPOSITORY https://github.com/sotetsuk/YaneuraOu-cmake
  GIT_TAG master
)
fetchcontent_makeavailable(YaneuraOu)

add_executable(
  tanuki
  tanuki-mate-search.cpp
)
target_link_libraries(tanuki PUBLIC YaneuraOu)
target_include_directories(
  tanuki PUBLIC
  ${YaneuraOu_SOURCE_DIR}/include
)
```
