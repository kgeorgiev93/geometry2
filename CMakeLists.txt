cmake_minimum_required(VERSION 2.8.3)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/lsolanka/hunter/archive/v0.22.4-rosdevel16.tar.gz"
    SHA1 "e75b43a1c98c1793ef6d39962db3dabe5bd5fb84"
)

project(geometry2)

hunter_add_package(ros_console_bridge)
hunter_add_package(ros_common_msgs)
hunter_add_package(ros_comm)
hunter_add_package(ros_actionlib)
hunter_add_package(Eigen)

find_package(Boost CONFIG REQUIRED COMPONENTS signals system thread)
find_package(catkin CONFIG REQUIRED)
find_package(Eigen3 CONFIG REQUIRED)

add_subdirectory(tf2_msgs)
add_subdirectory(tf2)
add_subdirectory(tf2_py)
add_subdirectory(tf2_ros)
add_subdirectory(tf2_eigen)
add_subdirectory(test_tf2)

# Omitted, have orocos-kdl as dependency
# add_subdirectory(tf2_geometry_msgs)
# add_subdirectory(tf2_kdl)
