# 声明要求的 cmake 最低版本
cmake_minimum_required(VERSION 3.10)

# 声明一个 cmake 工程
project(HelloSLAM)

# 设置编译模式 表示 debug
set(CMAKE_BUILD_TYPE Debug)

# 设置 include 文件夹的路径
include_directories(include)

# 设置 so 文件路径 （绝对路径）
LINK_DIRECTORIES(/home/bright/CLionProjects/slambook2-master/ch2/ex2_cmake_use/lib)

# 加入头文件编译可执行文件
add_executable(useHello2 main.cpp include/libHelloSLAM.h)

# 直接链接库
target_link_libraries(useHello2 libhello.so)