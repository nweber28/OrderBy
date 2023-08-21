# @file CMakeLists.txt
# 
# CMake files for the OrderBy tool

# Can be run by any version of CMake >= this
cmake_minimum_required(VERSION 3.17)

# project info
project(OrderBy)

# C++17 standard
set(CMAKE_CXX_STANDARD 17)

add_executable(OrderBy OrderBy.cpp)

# CLI11 download
include(FetchContent)
FetchContent_Declare(cli11
  URL https://github.com/CLIUtils/CLI11/releases/download/v2.2.0/CLI11.hpp
  DOWNLOAD_NO_EXTRACT TRUE
)
FetchContent_MakeAvailable(cli11)
add_library(cli11 INTERFACE IMPORTED)
target_include_directories(cli11 SYSTEM INTERFACE ${cli11_SOURCE_DIR})
target_link_libraries(OrderBy PRIVATE cli11)

include(GNUInstallDirs)
install(TARGETS OrderBy)
