cmake_minimum_required(VERSION 3.8)
project(rescue_robot_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# Find necessary ROS2 packages for building interfaces
find_package(rosidl_default_generators REQUIRED)

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

# Generate language-specific code from your custom message files
rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/RobotDrive.msg"
  "msg/RobotArm.msg"
  "msg/RescueControl.msg"
  "msg/RobotStatus.msg"
  # If any of your custom messages depend on standard ROS messages (e.g., geometry_msgs/Point),
  # you would list them here:
  # DEPENDENCIES geometry_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# Mark this package as ament_package, allowing it to be found by other ROS2 packages
ament_package()
