cmake_minimum_required(VERSION 3.16)
project(YaneuraOu)

set(CMAKE_CXX_STANDARD 14)
file(
  GLOB YANEURAOU_ENGINE_BASE
  YaneuraOu/source/book/**.h
  YaneuraOu/source/book/**.cpp
  YaneuraOu/source/eval/**.h
  YaneuraOu/source/eval/**.cpp
  YaneuraOu/source/extra/**.h
  YaneuraOu/source/extra/**.cpp
  YaneuraOu/source/learn/**.h
  YaneuraOu/source/learn/**.cpp
  YaneuraOu/source/mate/**.h
  YaneuraOu/source/mate/**.cpp
  YaneuraOu/source/testcmd/**.h
  YaneuraOu/source/testcmd/**.cpp
  YaneuraOu/source/*.h
  YaneuraOu/source/**.cpp
)
add_library(YaneuraOu STATIC ${YANEURAOU_ENGINE_BASE})
target_include_directories(YaneuraOu PUBLIC .)

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(YaneuraOu PUBLIC "-pthread")
