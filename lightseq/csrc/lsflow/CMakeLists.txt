cmake_minimum_required(VERSION 3.10)

project(LightseqProtoType LANGUAGES CXX CUDA)

find_package(Threads REQUIRED)

set(CMAKE_CXX_STANDARD 14)

include_directories(includes)

add_library(lsflow STATIC context.cpp node.cpp manager.cpp layer.cpp tensor.cpp)

target_link_libraries(lsflow PUBLIC cuda_kernels -lcublas)

if(DEBUG)
  add_subdirectory(example)
endif()
