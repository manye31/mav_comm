cmake_minimum_required(VERSION 3.5)
project(mav_comm)

find_package(ament_cmake REQUIRED)
find_package(mav_msgs REQUIRED)
find_package(mav_planning_msgs REQUIRED)
find_package(mav_state_machine_msgs REQUIRED)
find_package(mav_system_msgs REQUIRED)

ament_export_dependencies(
  mav_msgs
  mav_planning_msgs
  mav_state_machine_msgs
  mav_system_msgs
)
ament_package()
