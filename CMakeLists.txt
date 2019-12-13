cmake_minimum_required(VERSION 3.16)
project(Project)

add_library(testmain STATIC main.cpp)
target_compile_definitions(testmain PRIVATE CATCH_CONFIG_MAIN PUBLIC CATCH_CONFIG_FAST_COMPILE)
target_precompile_headers(testmain INTERFACE catch.hpp)

add_executable(test test.cpp)
target_link_libraries(test PRIVATE testmain)
target_compile_options(test PRIVATE -ftime-trace -ftime-trace-granularity=0)
