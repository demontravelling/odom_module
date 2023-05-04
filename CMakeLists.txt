cmake_minimum_required(VERSION 3.0.2)
project(odom_module)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  nav_msgs
  sensor_msgs
  std_msgs
  roscpp
  rospy
  tf
)

 
catkin_package(
 
)

 
include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${Boost_INCLUDE_DIRS}
  ${console_bridge_INCLUDE_DIRS}
)

add_executable(wheel_odom
  src/main.cpp
)
add_dependencies(wheel_odom ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(wheel_odom
  ${catkin_LIBRARIES}
)


add_executable(error_record
  src/error.cpp
)
add_dependencies(error_record ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(error_record
  ${catkin_LIBRARIES}
)


add_executable(odom_treat
  src/odom_treat.cpp
)
add_dependencies(odom_treat ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(odom_treat
  ${catkin_LIBRARIES}
)

add_executable(can_sender
  src/can_sender.cpp
)
add_dependencies(can_sender ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(can_sender
  ${catkin_LIBRARIES}
)


add_executable(imu_node
  src/imu_node.cpp
)
add_dependencies(imu_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(imu_node
  ${catkin_LIBRARIES}
)
