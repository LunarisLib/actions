cmake_minimum_required(VERSION 3.5)
project(Example VERSION 1.0 DESCRIPTION "A simple example project")


if (${CMAKE_BUILD_TYPE} STREQUAL Debug)
    set_directory_properties(PROPERTIES COMPILE_DEFINITIONS "_DEBUG")
else ()
    set_directory_properties(PROPERTIES COMPILE_DEFINITIONS "NDEBUG")
endif ()

if (UNIX AND NOT APPLE)
    set(CMAKE_C_COMPILER gcc CACHE STRING "C compiler" FORCE)
    set(CMAKE_CXX_COMPILER g++ CACHE STRING "C++ compiler" FORCE)
elseif (WIN32)
    set(CMAKE_C_COMPILER cl CACHE STRING "C compiler" FORCE)
    set(CMAKE_CXX_COMPILER cl CACHE STRING "C++ compiler" FORCE)
else() # apple
    set(CMAKE_C_COMPILER clang CACHE STRING "C compiler" FORCE)
    set(CMAKE_CXX_COMPILER clang++ CACHE STRING "C++ compiler" FORCE)
endif()



file(GLOB_RECURSE source_list "src/*.cpp" "include")
add_executable(${PROJECT_NAME} ${source_list})


# Set C++ version
set_target_properties(${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
 )