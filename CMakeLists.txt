cmake_minimum_required(VERSION 3.12)
project(Gist VERSION 1.0.7)

set(CMAKE_CXX_STANDARD 11)
option(BUILD_TESTS "Build tests" OFF)

# Check for FFTW
find_package(FFTW QUIET)
if(FFTW_FOUND)
    message(STATUS "FFTW found.")
    add_definitions(-DUSE_FFTW)
else()
    message(STATUS "Using KISS FFT as fallback.")
    add_definitions(-DUSE_KISS_FFT)
endif()

add_subdirectory(src)

if(BUILD_TESTS)
    enable_testing()
    add_subdirectory(tests)
endif()

set(CMAKE_SUPPRESS_REGENERATION true)
