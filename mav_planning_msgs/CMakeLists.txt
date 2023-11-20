cmake_minimum_required(VERSION 3.3)
project(mav_planning_msgs)

find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(mav_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(nav_msgs REQUIRED)

find_package (Eigen3 3.3 REQUIRED NO_MODULE)

ament_export_dependencies(rosidl_default_runtime geometry_msgs sensor_msgs std_msgs mav_msgs trajectory_msgs nav_msgs)

ament_export_include_directories(${EIGEN3_INCLUDE_DIRS})

rosidl_generate_interfaces(${PROJECT_NAME}
  msg/Point2D.msg
  msg/PointCloudWithPose.msg
  msg/Polygon2D.msg
  msg/PolygonWithHoles.msg
  msg/PolygonWithHolesStamped.msg
  msg/PolynomialSegment.msg
  msg/PolynomialTrajectory.msg
  msg/PolynomialSegment4D.msg
  msg/PolynomialTrajectory4D.msg
  srv/PlannerService.srv
  srv/PolygonService.srv
  srv/ChangeNameService.srv
  DEPENDENCIES geometry_msgs sensor_msgs std_msgs mav_msgs trajectory_msgs nav_msgs
)

ament_package()


# find_package(catkin REQUIRED COMPONENTS geometry_msgs sensor_msgs std_msgs message_generation mav_msgs trajectory_msgs)
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

# add_message_files(
#   FILES
#   Point2D.msg
#   PointCloudWithPose.msg
#   Polygon2D.msg
#   PolygonWithHoles.msg
#   PolygonWithHolesStamped.msg
#   PolynomialSegment.msg
#   PolynomialTrajectory.msg
#   PolynomialSegment4D.msg
#   PolynomialTrajectory4D.msg
# )

# add_service_files(
#   FILES
#   PlannerService.srv
#   PolygonService.srv
#   ChangeNameService.srv
# )

# generate_messages(
#   DEPENDENCIES geometry_msgs sensor_msgs std_msgs mav_msgs trajectory_msgs
# )

# catkin_package(
#   INCLUDE_DIRS include ${EIGEN3_INCLUDE_DIRS}
#   CATKIN_DEPENDS message_runtime geometry_msgs sensor_msgs std_msgs mav_msgs trajectory_msgs
# )
