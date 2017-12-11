cmake_minimum_required(VERSION 2.8.3)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.211.tar.gz"
    SHA1 "c022f0c2480e835a6bafdd734035ec2071b51897"
)

project(geometry2)

hunter_add_package(ros_console_bridge)
hunter_add_package(ros_common_msgs)
hunter_add_package(ros_comm)
hunter_add_package(actionlib)
hunter_add_package(Eigen)
hunter_add_package(bullet)

find_package(Boost CONFIG REQUIRED COMPONENTS system thread)
find_package(catkin CONFIG REQUIRED)
find_package(Eigen3 CONFIG REQUIRED)

add_subdirectory(tf2_msgs)
add_subdirectory(tf2)
add_subdirectory(tf2_py)
add_subdirectory(tf2_ros)
add_subdirectory(tf2_eigen)
add_subdirectory(tf2_bullet)
add_subdirectory(tf2_sensor_msgs)
add_subdirectory(tf2_tools)
add_subdirectory(test_tf2)

# Omitted, have orocos-kdl as dependency
# add_subdirectory(tf2_geometry_msgs)
# add_subdirectory(tf2_kdl)
