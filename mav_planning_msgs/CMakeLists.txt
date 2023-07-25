cmake_minimum_required(VERSION 3.5)
project(mav_planning_msgs)

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
find_package(geometry_msgs REQUIRED) 
find_package(sensor_msgs REQUIRED) 
find_package(std_msgs REQUIRED) 
find_package(mav_msgs REQUIRED) 
find_package(trajectory_msgs REQUIRED)
find_package(Eigen3 3.3 REQUIRED)

include_directories(
  include
)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Point2D.msg"
  "msg/PointCloudWithPose.msg"
  "msg/Polygon2D.msg"
  "msg/PolygonWithHoles.msg"
  "msg/PolygonWithHolesStamped.msg"
  "msg/PolynomialSegment.msg"
  "msg/PolynomialTrajectory.msg"
  "msg/PolynomialSegment4D.msg"
  "msg/PolynomialTrajectory4D.msg"
  "srv/PlannerService.srv"
  "srv/PolygonService.srv"
  "srv/ChangeNameService.srv"
  DEPENDENCIES builtin_interfaces std_msgs
  ADD_LINTER_TESTS
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

