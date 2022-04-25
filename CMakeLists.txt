cmake_minimum_required (VERSION 2.8.12)

project(xcbswitch)

SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/lib)


option(CMAKE_RELEASE "CMAKE_RELEASE" FALSE)

if(CMAKE_RELEASE)
    add_definitions(-DNDEBUG)
    set(CMAKE_CXX_FLAGS "-std=c++1y -O3 -Werror=return-type -Wall -Wextra -Werror ${CMAKE_CXX_FLAGS}")
else()
    set(CMAKE_CXX_FLAGS "-std=c++1y -O0 -g -Werror=return-type -Wall ${CMAKE_CXX_FLAGS}")
endif()

add_executable(xkbswitch_bin xkbswitch.m)

target_link_libraries(xkbswitch_bin "-framework Carbon -framework Foundation")
set_target_properties(xkbswitch_bin PROPERTIES
    OUTPUT_NAME xkbswitch)

add_library(xkbswitch STATIC libxkbswitch.c)

message("SRC ${CMAKE_SOURCE_DIR}")
