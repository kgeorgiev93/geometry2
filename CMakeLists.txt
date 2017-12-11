cmake_minimum_required(VERSION 2.8.3)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/lsolanka/hunter/archive/v0.19.210-11.tar.gz"
    SHA1 "ae63309e76bcad9748e236a28dc9fbd217811482"
)

project(actionlib)

hunter_add_package(ros-common_msgs)
hunter_add_package(ros-ros_comm)
hunter_add_package(ros-actionlib)
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
