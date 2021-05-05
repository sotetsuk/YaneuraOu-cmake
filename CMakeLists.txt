cmake_minimum_required(VERSION 3.16)
project(YaneuraOu)

set(CMAKE_CXX_STANDARD 14)
file(
  GLOB YANEURAOU_ENGINE_BASE
  include/YaneuraOu/source/book/**.h YaneuraOu/source/book/**.cpp
  include/YaneuraOu/source/eval/**.h YaneuraOu/source/eval/**.cpp
  include/YaneuraOu/source/extra/**.h YaneuraOu/source/extra/**.cpp
  include/YaneuraOu/source/learn/**.h YaneuraOu/source/learn/**.cpp
  include/YaneuraOu/source/mate/**.h YaneuraOu/source/mate/**.cpp
  include/YaneuraOu/source/testcmd/**.h YaneuraOu/source/testcmd/**.cpp
  include/YaneuraOu/source/*.h YaneuraOu/source/**.cpp
)
include_directories(include/YaneuraOu/source)
include_directories(include/YaneuraOu/source/book)
include_directories(include/YaneuraOu/source/eval)
include_directories(include/YaneuraOu/source/extra)
include_directories(include/YaneuraOu/source/learn)
include_directories(include/YaneuraOu/source/mate)

add_library(YaneuraOu STATIC ${YANEURAOU_ENGINE_BASE})

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(YaneuraOu PUBLIC "-pthread")
