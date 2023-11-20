cmake_minimum_required(VERSION 3.3)
project(mav_system_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  msg/CpuInfo.msg
  msg/ProcessInfo.msg
  DEPENDENCIES std_msgs
)

ament_export_dependencies(rosidl_default_runtime std_msgs)

ament_package()
