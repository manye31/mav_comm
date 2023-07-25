cmake_minimum_required(VERSION 3.5)
project(mav_msgs)

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

# Find Dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(Eigen3 3.3 REQUIRED)

include_directories(
  include/
)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Actuators.msg"
  "msg/AttitudeThrust.msg"
  "msg/RateThrust.msg"
  "msg/RollPitchYawrateThrust.msg"
  "msg/TorqueThrust.msg"
  "msg/Status.msg"
  "msg/FilteredSensorData.msg"
  "msg/GpsWaypoint.msg"
  DEPENDENCIES builtin_interfaces std_msgs
  ADD_LINTER_TESTS
)

install(
  DIRECTORY include/
  DESTINATION include
)

ament_export_include_directories(include)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
