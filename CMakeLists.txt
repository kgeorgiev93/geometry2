cmake_minimum_required(VERSION 2.8.3)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/lsolanka/hunter/archive/v0.21.6-rosdevel1.tar.gz"
    SHA1 "90dd6443649cb1823522458b8c11d8950ecbf7e6"
)

project(geometry2)

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
