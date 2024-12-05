cmake_minimum_required(VERSION 3.29.2)

project(overriding_warning_level CXX)

add_library(warning_ignore INTERFACE)
target_compile_options(warning_ignore INTERFACE $<$<CXX_COMPILER_ID:MSVC>:/w>)
add_library(warnings::ignore ALIAS warning_ignore)

add_library(warning_level_3 INTERFACE)
target_compile_options(warning_level_3 INTERFACE $<$<CXX_COMPILER_ID:MSVC>:/W3>)
add_library(warnings::level_3 ALIAS warning_level_3)

add_executable(test_app_with_ignore_warnings main.cpp)
target_link_libraries(test_app_with_ignore_warnings PRIVATE warnings::ignore)

add_executable(test_app_with_3_level_warnings main.cpp)
target_link_libraries(test_app_with_3_level_warnings PRIVATE warnings::level_3)
