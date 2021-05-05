cmake_minimum_required(VERSION 3.16)
project(YaneuraOu)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D NO_SSE")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D TANUKI_MATE_ENGINE")
file(
  GLOB YANEURAOU_ENGINE_BASE
  YaneuraOu/source/book/apery_book.cpp
  YaneuraOu/source/book/apery_book.h
  YaneuraOu/source/book/book.cpp
  YaneuraOu/source/book/book.h
  YaneuraOu/source/eval/material/evaluate_material.cpp
  YaneuraOu/source/eval/evaluate.cpp
  YaneuraOu/source/eval/evaluate_bona_piece.cpp
  YaneuraOu/source/eval/evaluate_io.cpp
  YaneuraOu/source/eval/evaluate_io.h
  YaneuraOu/source/eval/evaluate_mir_inv_tools.cpp
  YaneuraOu/source/eval/evaluate_mir_inv_tools.h
  YaneuraOu/source/extra/all.h
  YaneuraOu/source/extra/bitop.cpp
  YaneuraOu/source/extra/bitop.h
  YaneuraOu/source/extra/key128.h
  YaneuraOu/source/extra/long_effect.cpp
  YaneuraOu/source/extra/long_effect.h
  YaneuraOu/source/extra/macros.h
  YaneuraOu/source/extra/sfen_packer.cpp
  YaneuraOu/source/extra/super_sort.cpp
  YaneuraOu/source/learn/learn.h
  YaneuraOu/source/learn/learner.cpp
  YaneuraOu/source/mate/mate.cpp
  YaneuraOu/source/mate/mate.h
  YaneuraOu/source/mate/mate1ply_with_effect.cpp
  YaneuraOu/source/mate/mate1ply_without_effect.cpp
  YaneuraOu/source/mate/mate_solver.cpp
  YaneuraOu/source/testcmd/benchmark.cpp
  YaneuraOu/source/testcmd/mate_test_cmd.cpp
  YaneuraOu/source/testcmd/normal_test_cmd.cpp
  YaneuraOu/source/bitboard.cpp
  YaneuraOu/source/bitboard.h
  YaneuraOu/source/config.h
  YaneuraOu/source/evaluate.h
  YaneuraOu/source/main.cpp
  YaneuraOu/source/misc.cpp
  YaneuraOu/source/misc.h
  YaneuraOu/source/movegen.cpp
  YaneuraOu/source/movepick.cpp
  YaneuraOu/source/movepick.h
  YaneuraOu/source/position.cpp
  YaneuraOu/source/position.h
  YaneuraOu/source/search.h
  YaneuraOu/source/thread.cpp
  YaneuraOu/source/thread.h
  YaneuraOu/source/thread_win32_osx.h
  YaneuraOu/source/timeman.cpp
  YaneuraOu/source/tt.cpp
  YaneuraOu/source/tt.h
  YaneuraOu/source/types.cpp
  YaneuraOu/source/types.h
  YaneuraOu/source/usi.cpp
  YaneuraOu/source/usi.h
  YaneuraOu/source/usi_option.cpp
)
include_directories(YaneuraOu/source)
include_directories(YaneuraOu/source/book)
include_directories(YaneuraOu/source/eval)
include_directories(YaneuraOu/source/extra)
include_directories(YaneuraOu/source/learn)
include_directories(YaneuraOu/source/mate)

add_executable(
  tanuki
  ${YANEURAOU_ENGINE_BASE}
  YaneuraOu/source/engine/tanuki-mate-engine/tanuki-mate-search.cpp
)

# link pthread
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(tanuki PUBLIC "-pthread")
