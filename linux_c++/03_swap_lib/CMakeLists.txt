cmake_minimum_required(VERSION 3.0)

project(SWAP)

set(CMAKE_BUILD_TYPE "Debug")

include_directories(include)

# Create libaray
add_library(libswap SHARED src/swap.cpp)
# target_include_directories(libswap include)

# Create executable
add_executable(main main.cpp)

# Link library
target_link_libraries(main libswap)



