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
add_library(YaneuraOu STATIC ${YANEURAOU_ENGINE_BASE})
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu)
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu/book)
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu/eval)
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu/extra)
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu/learn)
target_include_directories(YaneuraOu PUBLIC include/YaneuraOu/mate)

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(YaneuraOu PUBLIC "-pthread")
