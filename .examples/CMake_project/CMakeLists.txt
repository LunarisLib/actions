cmake_minimum_required(VERSION 3.20)
project(Example VERSION 1.0 DESCRIPTION "A simple example project")

file(GLOB_RECURSE source_list "src/*.cpp" "include")
add_executable(${PROJECT_NAME} ${source_list})

# Set C++ version
set_target_properties(${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
 )