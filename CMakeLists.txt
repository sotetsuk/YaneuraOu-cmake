cmake_minimum_required(VERSION 3.16)
project(YaneuraOu)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D NO_SSE")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D TANUKI_MATE_ENGINE")
file(
  GLOB YANEURAOU_ENGINE_BASE
  YaneuraOu/source/book/**.h YaneuraOu/source/book/**.cpp
  YaneuraOu/source/eval/**.h YaneuraOu/source/eval/**.cpp
  YaneuraOu/source/extra/**.h YaneuraOu/source/extra/**.cpp
  YaneuraOu/source/learn/**.h YaneuraOu/source/learn/**.cpp
  YaneuraOu/source/mate/**.h YaneuraOu/source/mate/**.cpp
  YaneuraOu/source/testcmd/**.h YaneuraOu/source/testcmd/**.cpp
  YaneuraOu/source/*.h YaneuraOu/source/**.cpp
)
include_directories(YaneuraOu/source)
include_directories(YaneuraOu/source/book)
include_directories(YaneuraOu/source/eval)
include_directories(YaneuraOu/source/extra)
include_directories(YaneuraOu/source/learn)
include_directories(YaneuraOu/source/mate)

add_library(YaneuraOu STATIC ${YANEURAOU_ENGINE_BASE})

add_executable(
  tanuki
  YaneuraOu/source/engine/tanuki-mate-engine/tanuki-mate-search.cpp
)
target_link_libraries(tanuki PUBLIC YaneuraOu)

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(YaneuraOu PUBLIC "-pthread")
