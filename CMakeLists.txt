cmake_minimum_required(VERSION 3.16)
project(YaneuraOu)

set(CMAKE_CXX_STANDARD 14)
file(
  GLOB YANEURAOU_ENGINE_BASE
  include/YaneuraOu/book/**.h
  include/YaneuraOu/book/**.cpp
  include/YaneuraOu/eval/**.h
  include/YaneuraOu/eval/**.cpp
  include/YaneuraOu/extra/**.h
  include/YaneuraOu/extra/**.cpp
  include/YaneuraOu/learn/**.h
  include/YaneuraOu/learn/**.cpp
  include/YaneuraOu/mate/**.h
  include/YaneuraOu/mate/**.cpp
  include/YaneuraOu/testcmd/**.h
  include/YaneuraOu/testcmd/**.cpp
  include/YaneuraOu/*.h
  include/YaneuraOu/**.cpp
)
include_directories(include/YaneuraOu)
include_directories(include/YaneuraOu/book)
include_directories(include/YaneuraOu/eval)
include_directories(include/YaneuraOu/extra)
include_directories(include/YaneuraOu/learn)
include_directories(include/YaneuraOu/mate)

add_library(YaneuraOu STATIC ${YANEURAOU_ENGINE_BASE})

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(YaneuraOu PUBLIC "-pthread")
