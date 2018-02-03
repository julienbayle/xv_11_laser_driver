cmake_minimum_required(VERSION 2.8.3)
project(xv_11_laser_driver)

find_package(catkin REQUIRED COMPONENTS roscpp sensor_msgs)
find_package(Boost REQUIRED COMPONENTS system)

catkin_package(
   INCLUDE_DIRS include
)

include_directories(include
  ${catkin_INCLUDE_DIRS}
)

add_executable(neato_laser_publisher 
	src/neato_laser_publisher.cpp
	src/xv11_laser.cpp
)


target_link_libraries(neato_laser_publisher
  ${catkin_LIBRARIES}
)

install(TARGETS neato_laser_publisher
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".git" EXCLUDE
)
