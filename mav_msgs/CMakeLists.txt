cmake_minimum_required(VERSION 3.3)
project(mav_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

find_package (Eigen3 3.3 REQUIRED NO_MODULE)


# ament_export_targets(${PROJECT_NAME}_export HAS_LIBRARY_TARGET)

# ament_export_dependencies(rosidl_default_runtime std_msgs geometry_msgs trajectory_msgs nav_msgs)

ament_export_include_directories(${EIGEN3_INCLUDE_DIRS})

rosidl_generate_interfaces(${PROJECT_NAME}
  msg/Actuators.msg
  msg/AttitudeThrust.msg
  msg/RateThrust.msg
  msg/RollPitchYawrateThrust.msg
  msg/TorqueThrust.msg
  msg/Status.msg
  msg/FilteredSensorData.msg
  msg/GpsWaypoint.msg
  DEPENDENCIES std_msgs geometry_msgs nav_msgs
)

install(
  DIRECTORY include/
  DESTINATION include/${PROJECT_NAME}/
)

ament_export_dependencies(rosidl_default_runtime std_msgs geometry_msgs trajectory_msgs nav_msgs)

ament_package()


# find_package(catkin REQUIRED message_generation std_msgs geometry_msgs trajectory_msgs nav_msgs)
# include_directories(include ${catkin_INCLUDE_DIRS})

# find_package(Eigen3 QUIET)
# if(NOT EIGEN3_FOUND)
#   # ROS == Indigo.
#   find_package(cmake_modules REQUIRED)
#   find_package(Eigen REQUIRED)
#   set(EIGEN3_INCLUDE_DIRS ${EIGEN_INCLUDE_DIRS})
# else()
#   # ROS > Indigo.
#   set(EIGEN3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})
# endif()

# add_definitions(-std=c++11)

# add_message_files(
#   FILES
#   Actuators.msg
#   AttitudeThrust.msg
#   RateThrust.msg
#   RollPitchYawrateThrust.msg
#   TorqueThrust.msg
#   Status.msg
#   FilteredSensorData.msg
#   GpsWaypoint.msg
# )

# generate_messages(DEPENDENCIES std_msgs geometry_msgs nav_msgs)

# catkin_package(
#   INCLUDE_DIRS include ${EIGEN3_INCLUDE_DIRS}
#   CATKIN_DEPENDS message_runtime std_msgs geometry_msgs trajectory_msgs nav_msgs
#   CFG_EXTRAS export_flags.cmake
# )

# install(
#   DIRECTORY include/${PROJECT_NAME}/
#   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
#   FILES_MATCHING PATTERN "*.h"
# )
