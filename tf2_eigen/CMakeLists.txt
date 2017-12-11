cmake_minimum_required(VERSION 2.8.3)
project(tf2_eigen)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  tf2
)

include_directories(include ${catkin_INCLUDE_DIRS})

set(PROJECT_INSTALLSPACE_LIBRARIES ros::${PROJECT_NAME})
catkin_package(
  INCLUDE_DIRS include
  DEPENDS Eigen3)

add_library(${PROJECT_NAME} INTERFACE)
target_link_libraries(${PROJECT_NAME} INTERFACE Eigen3::Eigen)
target_include_directories(${PROJECT_NAME} INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install(TARGETS ${PROJECT_NAME}
  EXPORT ${PROJECT_NAME}Targets
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
install(EXPORT ${PROJECT_NAME}Targets
  DESTINATION share/${PROJECT_NAME}/cmake
  NAMESPACE ros::
  FILE ${PROJECT_NAME}Targets.cmake
)

if(CATKIN_ENABLE_TESTING)

  catkin_add_gtest(tf2_eigen-test test/tf2_eigen-test.cpp)
  target_link_libraries(tf2_eigen-test Eigen3::Eigen ${catkin_LIBRARIES} ${GTEST_LIBRARIES})

endif()
