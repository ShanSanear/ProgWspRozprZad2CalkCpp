cmake_minimum_required(VERSION 3.15)
project(OpenMPProjectTwo)

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++2a -fopenmp")
add_library(cxxopts INTERFACE)
add_library(cxxopts::cxxopts ALIAS cxxopts)
set(CMAKE_EXE_LINKER_FLAGS " -static")
target_link_libraries(cxxopts INTERFACE -static-libgcc -static-libstdc++)
target_include_directories(cxxopts INTERFACE
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
        )
add_executable(OpenMPProjectTwo src/main.cpp)