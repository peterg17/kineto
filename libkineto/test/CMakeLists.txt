# Copyright (c) Meta Platforms, Inc. and affiliates.
# All rights reserved.
#
# This source code is licensed under the BSD-style license found in the
# LICENSE file in the root directory of this source tree.

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

# TODO

# GoogleTest requires at least C++14
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

get_filename_component(PARENT_DIR ../ ABSOLUTE)
include_directories(${PARENT_DIR})
include_directories(/usr/local/include/kineto/)
include_directories(${PARENT_DIR}/third_party/fmt/include)
include_directories(${PARENT_DIR}/third_party/googletest/googlemock/include)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)

FetchContent_MakeAvailable(googletest)

enable_testing()

add_executable(
  CuptiActivityProfilerTest
  CuptiActivityProfilerTest.cpp
)
target_link_libraries(
  CuptiActivityProfilerTest
  GTest::gtest_main
)

include(GoogleTest)
