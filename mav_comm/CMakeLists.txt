cmake_minimum_required(VERSION 3.5)
project(mav_comm)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

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
