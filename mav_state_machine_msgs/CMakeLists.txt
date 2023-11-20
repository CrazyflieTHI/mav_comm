cmake_minimum_required(VERSION 3.3)
project(mav_state_machine_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  msg/StartStopTask.msg
  srv/RunTaskService.srv
  DEPENDENCIES std_msgs
)

ament_export_dependencies(rosidl_default_runtime std_msgs)

ament_package()
