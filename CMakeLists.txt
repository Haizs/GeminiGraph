cmake_minimum_required(VERSION 3.10)
project(GeminiGraph)

include_directories(./)

find_package(MPI REQUIRED)
include_directories(${MPI_INCLUDE_PATH})

set(CMAKE_CXX_COMPILER /usr/bin/mpicxx)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -Wall -std=c++11 -g -fopenmp -lnuma -march=native")
set(CMAKE_CXX_COMPILE_FLAGS ${CMAKE_CXX_COMPILE_FLAGS} ${MPI_COMPILE_FLAGS})
set(CMAKE_CXX_LINK_FLAGS "${CMAKE_CXX_LINK_FLAGS} ${MPI_LINK_FLAGS}")
link_libraries(numa)

add_definitions(-DPRINT_DEBUG_MESSAGES)

add_executable(bc
        toolkits/bc.cpp)

add_executable(bfs
        toolkits/bfs.cpp)

add_executable(cc
        toolkits/cc.cpp)

add_executable(pagerank
        toolkits/pagerank.cpp)

add_executable(sssp
        toolkits/sssp.cpp)
