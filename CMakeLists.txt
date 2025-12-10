cmake_minimum_required(VERSION 3.15)
project(ails_pr_cpp VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(CMAKE_BUILD_TYPE STREQUAL "Release")
    add_compile_options(-O3 -march=native -Wall -Wextra)
endif()

add_library(ails_core
    src/core/Instance.cpp
    src/io/Parser.cpp
)
target_include_directories(ails_core PUBLIC src)

add_executable(ails_app app/main.cpp)
target_link_libraries(ails_app PRIVATE ails_core)
