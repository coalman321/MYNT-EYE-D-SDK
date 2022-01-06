cmake_minimum_required(VERSION 3.8)
project(mynteye_wrapper_d)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

find_package(ament_cmake REQUIRED)
find_package(mynteyed REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(tf2 REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(rclcpp REQUIRED)
find_package(image_transport REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(cv_bridge REQUIRED)

find_package(OpenCV REQUIRED)
if(OpenCV_FOUND)
  message(STATUS "OpenCV is found.")
  set(WITH_OPENCV TRUE)
  add_definitions(-DWITH_OPENCV)
  message(STATUS "Defined WITH_OPENCV.")
endif()


# targets
add_compile_options(-std=c++11)

include_directories(
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

set(AMENT_LIBRARIES
  mynteyed
  sensor_msgs
  std_msgs
  tf2
  tf2_ros
  rclcpp
  image_transport
  cv_bridge
)

add_executable(mynteye_wrapper_d_node src/mynteye_wrapper_node.cc)
ament_target_dependencies(mynteye_wrapper_d_node ${LINK_LIBRARIES})

add_executable(mynteye_listener_d src/mynteye_listener.cc)
ament_target_dependencies(mynteye_listener_d ${LINK_LIBRARIES})

#generate messages
rosidl_generate_interfaces(${PROJECT_NAME}
  "srv/GetParams.srv"
  DEPENDENCIES std_msgs
)
ament_export_dependencies(rosidl_default_runtime)
rosidl_target_interfaces(dvl
  ${PROJECT_NAME} "rosidl_typesupport_cpp")

# install

install(TARGETS mynteye_wrapper_d mynteye_wrapper_d_node
  DESTINATION lib/${PROJECT_NAME})

# Install launch files.
install(DIRECTORY
  launch
  rviz
  DESTINATION share/${PROJECT_NAME}/
)

ament_package()