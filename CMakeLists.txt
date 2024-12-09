cmake_minimum_required(VERSION 3.29.2)

project(overriding_warning_level CXX)

# cl : command line  warning D9025: overriding '/W1' with '/w'
add_library(warning_ignore INTERFACE)
target_compile_options(warning_ignore INTERFACE $<$<CXX_COMPILER_ID:MSVC>:/w>)
add_library(warnings::ignore ALIAS warning_ignore)

# The same, but use /W0 flag. No warnings
add_library(warning_level_0 INTERFACE)
target_compile_options(warning_level_0 INTERFACE $<$<CXX_COMPILER_ID:MSVC>:/W0>)
add_library(warnings::level_0 ALIAS warning_level_0)

add_executable(test_app_with_ignore_warnings main.cpp)
target_link_libraries(test_app_with_ignore_warnings PRIVATE warnings::ignore)

add_executable(test_app_with_0_level_warnings main.cpp)
target_link_libraries(test_app_with_0_level_warnings PRIVATE warnings::level_0)
