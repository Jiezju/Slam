# cmake simple case

# cmake 版本需求
cmake_minimum_required(VERSION 3.4.1)

# 设置 project 的 name
project(project_name)

# 设置 C++ 版本标准
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}e")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

#include headfiles 添加头文件路径 headfiles_path
include_directories(headfiles_path/include)


# 直接通过 find_package 
find_package(ZLIB REQUIRED)
include_directories(${ZLIB_INCLUDE_DIRS})

# 无法 直接 find_package 指定 DIR
set(Torch_DIR ~/libtorch-1.0.0)
find_package(Torch required)

# 手动设置第三方依赖
set(ZLIB_DIRS ${CMAKE_SOURCE_DIR}/../3rdparty/zlib/)
set(ZLIB_LIBRARIES ${ZLIB_DIRS}/libz.a)
include_directories(${ZLIB_DIRS})


# 将源码编译成 so 库
add_library(cnpy SHARED ${CMAKE_SOURCE_DIR}/../3rdparty/cnpy/cnpy.cpp)

# 设置依赖库目录路径
set(XXX_LIBS PAHT/XXX.so)

# 添加可执行文件 源码文件为 src/XXX.cpp 二进制文件名为 binary_name
add_executable(binary_name
        src/XXX.cpp
        src/depend.cpp  # src/depend.cpp 不选择将 该文件作为库导入，而是直接编入 可执行文件
        )

# 链接 lib 到 可执行文件
target_link_libraries(binary_name
	${XXX_LIBS}
    ${ZLIB_LIBRARIES}
)

# install target and libraries  ${CMAKE_SOURCE_DIR} 表示 CMakeLists.txt 的绝对路径
set(CMAKE_INSTALL_PREFIX ${CMAKE_SOURCE_DIR}/install/project_name)
# 拷贝 二进制文件 binary_name 到 指定目录
install(TARGETS binary_name DESTINATION ./)
# 拷贝 DIRS 到 指定目录
install(DIRECTORY DIRS DESTINATION ./)
# 拷贝 XXX_LIBS 到 指定目录
install(PROGRAMS ${XXX_LIBS} DESTINATION lib)
