project(ctti)
cmake_minimum_required(VERSION 3.1)

option(CTTI_BUILD_TESTS "Build ctti feature tests" OFF)
option(CTTI_BUILD_EXAMPLES "Build ctti examples" OFF)

include(cmake/vs_source_groups.cmake)

set(CTTI_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})

add_library(ctti INTERFACE)

target_compile_features(ctti INTERFACE cxx_std_20)
set_target_properties(ctti PROPERTIES CXX_EXTENSIONS OFF)

target_include_directories(ctti INTERFACE ${CTTI_SOURCE_DIR}/include)

if(CTTI_BUILD_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif()

if(CTTI_BUILD_EXAMPLES)
    add_subdirectory(examples)
endif()
