# 声明要求的 cmake 最低版本
cmake_minimum_required(VERSION 3.10)

# 声明一个 cmake 工程
project(HelloSLAM)

# 设置编译模式 表示 debug
set(CMAKE_BUILD_TYPE Debug)

# 设置 include 文件夹的路径
include_directories("include")

# 添加一个可执行程序 useHello 是编译二进制文件的名字 对应的包含 main 函数 cpp文件路径
# 语法：add_executable( 程序名 源代码文件 ）
add_executable(useHello main.cpp)

# 共享库 库名 （lib）hello  SHARED 表示 so
add_library(hello SHARED src/libHelloSLAM.cpp)

# 将库文件链接到可执行程序上
target_link_libraries(useHello hello)
