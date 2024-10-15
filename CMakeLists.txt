cmake_minimum_required(VERSION 3.22)
project(cologra CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}")

# -fopenmp flag (enables OpenMP)
# set(GCC_COVERAGE_COMPILE_FLAGS "-Wall -pedantic -lm -O3 -funroll-loops -fopenmp")

add_executable(${PROJECT_NAME} src/main.cpp)

# MPI
find_package(MPI REQUIRED)
target_link_libraries(cologra PUBLIC MPI::MPI_CXX)
