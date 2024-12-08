cmake_minimum_required(VERSION 3.5)
project(mirs)

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(mirs_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(tf2 REQUIRED)

add_executable(odometry_publisher src/odometry_publisher.cpp)
ament_target_dependencies(odometry_publisher 
  rclcpp
  std_msgs
  nav_msgs
  geometry_msgs
  tf2_ros
  tf2
)

add_executable(parameter_publisher src/parameter_publisher.cpp)
ament_target_dependencies(parameter_publisher
  rclcpp
  mirs_msgs
)

add_executable(basic src/basic_command.cpp)
ament_target_dependencies(basic
  rclcpp
  mirs_msgs
)

add_executable(test_cli src/test.cpp)
ament_target_dependencies(test_cli
  rclcpp
  mirs_msgs
)

add_executable(update src/parameter_update.cpp)
ament_target_dependencies(update
  rclcpp
  mirs_msgs
)

add_executable(reboot src/reboot.cpp)
ament_target_dependencies(reboot
  rclcpp
  mirs_msgs
)

add_executable(reset src/encoder_reset.cpp)
ament_target_dependencies(reset
  rclcpp
  mirs_msgs
)

add_executable(jack_up src/jack_up.cpp)
ament_target_dependencies(jack_up
  rclcpp
  mirs_msgs
)

add_executable(jack_down src/jack_down.cpp)
ament_target_dependencies(jack_down
  rclcpp
  mirs_msgs
)

install(TARGETS
  odometry_publisher
  parameter_publisher
  update
  reboot
  reset
  basic
  DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY
  launch
  DESTINATION share/${PROJECT_NAME}/
)

ament_package()
