cmake_minimum_required(VERSION 3.16.3...3.20)
project(openslam_gmapping)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE RelWithDebInfo)

if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

find_package(ament_cmake REQUIRED)
add_compile_options(-fPIC)

include_directories(include)

add_subdirectory(gridfastslam)
add_subdirectory(scanmatcher)
add_subdirectory(sensor)
add_subdirectory(utils)

ament_export_libraries(gridfastslam)
ament_export_libraries(scanmatcher)
ament_export_libraries(sensor_base)
ament_export_libraries(sensor_odometry)
ament_export_libraries(sensor_range)
ament_export_libraries(utils)
ament_export_include_directories(include)

install(
  DIRECTORY include/
  DESTINATION include/
)

ament_package()
