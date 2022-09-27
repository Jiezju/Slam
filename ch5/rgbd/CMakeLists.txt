find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})

find_package(Pangolin REQUIRED)

include_directories( ${Pangolin_INCLUDE_DIRS} )

find_package(FMT REQUIRED )

add_executable(joinMap joinMap.cpp)
target_link_libraries(joinMap ${OpenCV_LIBS} ${Pangolin_LIBRARIES})
target_link_libraries(joinMap  fmt::fmt)
