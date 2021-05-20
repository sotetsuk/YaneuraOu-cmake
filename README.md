[![ci](https://github.com/sotetsuk/YaneuraOu-cmake/actions/workflows/ci.yml/badge.svg)](https://github.com/sotetsuk/YaneuraOu-cmake/actions/workflows/ci.yml)

# YaneuraOu-cmake

Utility to build [YaneuraOu](https://github.com/yaneurao/YaneuraOu) as static library using Cmake

## Usage

Link `YaneuraOu` lib in your `CmakeLists.txt` like 

```cmake
target_link_libraries(YOUR_ENGINE PUBLIC YaneuraOu)
```

Then, your engine can include `YaneuraOu` headers like

```cpp
#include "YaneuraOu/source/extra/all.h"
```

## Example

Build [tanuki solver](https://github.com/yaneurao/YaneuraOu/blob/master/source/engine/tanuki-mate-engine/tanuki-mate-search.cpp) with `CmakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.16)
project(tanuki)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D NO_SSE")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D TANUKI_MATE_ENGINE")

# download YaneuraOu using FetchContent
include(FetchContent)
set(FETCHCONTENT_QUIET OFF)
set(FETCHCONTENT_UPDATES_DISCONNECTED ON)
fetchcontent_declare(
  YaneuraOu
  GIT_REPOSITORY https://github.com/sotetsuk/YaneuraOu-cmake
  GIT_TAG master
)
fetchcontent_makeavailable(YaneuraOu)

# build tanuki solver
add_executable(
  tanuki
  tanuki-mate-search.cpp
)
target_link_libraries(tanuki PUBLIC YaneuraOu)
```

## LICENSE

MIT
